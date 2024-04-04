<template>
    <PageHead></PageHead>
    <div class="table-container">
        <table dir="auto">
            <TableHead name="姓名" today="今日新增" whole="本月累计"></TableHead>
            <TableRow v-bind:name="names[43]" v-bind:today="todays[43]" v-bind:whole="wholes[43]"></TableRow>
            <TableRow v-for="i in 42" v-bind:key="i" v-bind:name="names[i-1]" v-bind:today="todays[i-1]"
                      v-bind:whole="wholes[i-1]"></TableRow>
        </table>
    </div>
</template>


<script>
import TableRow from "./components/TableRow";
import TableHead from "./components/TableHead";
import PageHead from "./components/PageHead";
import axios from "axios";

export default {
    name: "App",
    components: {
        TableRow,
        TableHead,
        PageHead
    },
    data() {
        let names = [], todays = [], wholes = [];
        const idList = [20210602,20210907,20211102,20210203,20210204,20210206,20210208,20210209,20210210,20210212,20210214,20210221,20210223,20210224,20210225,20210231,20210233,20210238,20210306,20210313,20210315,20210322,20210333,20210334,20210336,20210340,20210343,20210403,20210406,20210409,20210410,20210412,20210414,20210415,20210417,20210418,20210419,20210420,20210421,20210423,20210426,20210429,20210440];
        let tmpList = [];
        const day = function() {
            const date = new Date();
            let month = date.getMonth() + 1;
            if (month < 10
            ) {
                month = "0" + month;
            }
            let day = date.getDate();
            if (day < 10) {
                day = "0" + day;
            }
            return date.getFullYear() + "-" + month + "-" + day;
        }();
        let tasks = [0, 0];
        return {
            names,
            todays,
            wholes,
            idList,
            tmpList,
            day,
            tasks,
            polling: null
        };
    },
    async created() {
        function getCount(data) {
            let count = 0;
            for (let var2 = 0; var2 < data.length; var2++) {
                let var3 = parseFloat(data[var2]["tolastdistence"]) / 1000;
                if (data[var2]["youxiao"] === 1) {
                    count += var3;
                }
            }
            return count;
        }

        for (let i = 0; i < 44; i++) {
            this.names[i] = "Loading";
        }
        this.names[0] = `Get ${this.tasks[0]}/${this.tasks[1]}`;
        {
            const getPage = async (url) => {
                const { data } = await axios.get(url);
                return data;
            };
            let tasks = this.tasks, names = this.names;
            const addTask = () => {
                tasks[1]++;
                names[0] = `Get ${tasks[0]}/${tasks[1]}`;
            }, doneTask = () => {
                tasks[0]++;
                names[0] = `Get ${tasks[0]}/${tasks[1]}`;
            };
            const day = this.day, idList = this.idList;
            let dataList = [];
            let dateList = [], dateList2 = [];
            let taskList = [], taskList2 = [];

            for (let i = 0; i < idList.length; i++) {
                dataList[i] = [null, 0.0, 0.0];
                addTask();
                taskList[taskList.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/month?student_no=" + idList[i])
                    .then(function(response) {
                        let var1 = JSON.parse(response)["data"];
                        for (let var2 = 0; var2 < var1.length; var2++) {
                            let date = var1[var2]["date"];
                            if (date !== day) {
                                dateList[dateList.length] = [i, idList[i], date];
                                addTask();
                            } else {
                                dateList2[dateList2.length] = [i];
                                addTask();
                            }
                        }
                        doneTask();
                    });
            }
            for (let i = 0; i < idList.length; i++) {
                addTask();
                taskList2[taskList2.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/index?student_no=" + this.idList[i])
                    .then(function(response) {
                        let res = JSON.parse(response);
                        dataList[i][0] = res["data"]["student"]["name"];
                        doneTask();
                    });
            }

            await Promise.all(taskList);

            for (let i = 0; i < dateList2.length; i++) {
                taskList2[taskList2.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/record?student_no=" + idList[dateList2[i]] + "&day=" + day)
                    .then(function(response) {
                        dataList[dateList2[i]][1] += getCount(JSON.parse(response)["data"]);
                        doneTask();
                    });
            }

            for (let i = 0; i < dateList.length; i++) {
                taskList2[taskList2.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/record?student_no=" + dateList[i][1] + "&day=" + dateList[i][2])
                    .then(function(response) {
                        dataList[dateList[i][0]][2] += getCount(JSON.parse(response)["data"]);
                        doneTask();
                    });
            }

            await Promise.all(taskList2);

            this.tmpList = JSON.parse(JSON.stringify(dataList));

            dataList.sort((a, b) => {
                if (a[1] < b[1] || (a[1] === b[1] && a[2] < b[2])) {
                    return 1;
                } else if (a[1] > b[1] || (a[1] === b[1] && a[2] > b[2])) {
                    return -1;
                } else {
                    return 0;
                }
            });

            this.todays[43] =0
            this.wholes[43] =0


            for (let i = 0; i < dataList.length && i < 43; i++) {
                this.names[i] = dataList[i][0];
                this.todays[i] = dataList[i][1];
                this.wholes[i] = dataList[i][2] + dataList[i][1];
                this.todays[43] += dataList[i][1];
                this.wholes[43] += dataList[i][2] + dataList[i][1];
            }

            this.names[43]="班级合计"

            let list = [];

            for (let i = 0; i < dataList.length; i++) {
                list[i] = [dataList[i][0], dataList[i][1], dataList[i][2] + dataList[i][1]];
            }

            console.log(list);

        }

        if (this.timer) {
            clearInterval(this.timer);
        } else {
            this.timer = setInterval(() => {
                setTimeout(this.pollData, 0);
            }, 60 * 1000);
        }
    },
    methods: {
        async pollData() {
            function getCount(data) {
                let count = 0;
                for (let var2 = 0; var2 < data.length; var2++) {
                    let var3 = parseFloat(data[var2]["tolastdistence"]) / 1000;
                    if (data[var2]["youxiao"] === 1) {
                        count += var3;
                    }
                }
                return count;
            }

            const getPage = async (url) => {
                const { data } = await axios.get(url);
                return data;
            };

            const idList = this.idList, day = this.day;
            let dataList = JSON.parse(JSON.stringify(this.tmpList));
            let taskList = [];
            for (let i = 0; i < this.idList.length; i++) {
                dataList[i][1] = 0.0;
                taskList[taskList.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/record?student_no=" + idList[i] + "&day=" + day)
                    .then(function(response) {
                        dataList[i][1] += getCount(JSON.parse(response)["data"]);
                    });
            }

            await Promise.all(taskList);

            dataList.sort((a, b) => {
                if (a[1]+a[2] < b[1]+b[2] || (a[1]+a[2] === b[1]+b[2] && a[1] < b[1])) {
                    return 1;
                } else if (a[1]+a[2] > b[1]+b[2] || (a[1]+a[2] === b[1]+b[2] && a[1] > b[1])) {
                    return -1;
                } else {
                    return 0;
                }
            });

            this.todays[43] =0
            this.wholes[43] =0


            for (let i = 0; i < dataList.length; i++) {
                this.names[i] = dataList[i][0];
                this.todays[i] = dataList[i][1];
                this.wholes[i] = dataList[i][2] + dataList[i][1];
                this.todays[43] += dataList[i][1];
                this.wholes[43] += dataList[i][2] + dataList[i][1];
            }
        }
    }
};

</script>


<style>

div.table-container {
    margin: 0 10px 10px;
}

body {
    margin-top: 0;
    background-color: rgba(17, 17, 17, 0.8);
    font-size: x-large;
    -webkit-app-region: drag;
}

table {
    border-collapse: collapse;
    border-top: solid 2px #afafaf;
    border-left: solid 2px #afafaf;
    border-bottom: solid 2px #afafaf;
    border-right: 0;
    margin: 0;
    width: 450px;
    display: block;
    overflow-x: auto;
}

tr {
    text-align: center;
    border-collapse: collapse;
    color: #eee;
    margin: 0;
    overflow-x: auto;
}

td {
    width: 150px;
    padding: 10px 5px;
}
</style>
