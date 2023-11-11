<template>
    <PageHead></PageHead>
    <div class="table-container">
        <table dir="auto">
            <TableHead name="姓名" today="今日新增" whole="本月累计"></TableHead>
            <TableRow v-bind:name="names[43]" v-bind:today="todays[43]" v-bind:whole="wholes[43]"></TableRow>
            <TableRow v-bind:name="names[0]" v-bind:today="todays[0]" v-bind:whole="wholes[0]"></TableRow>
            <TableRow v-bind:name="names[1]" v-bind:today="todays[1]" v-bind:whole="wholes[1]"></TableRow>
            <TableRow v-bind:name="names[2]" v-bind:today="todays[2]" v-bind:whole="wholes[2]"></TableRow>
            <TableRow v-bind:name="names[3]" v-bind:today="todays[3]" v-bind:whole="wholes[3]"></TableRow>
            <TableRow v-bind:name="names[4]" v-bind:today="todays[4]" v-bind:whole="wholes[4]"></TableRow>
            <TableRow v-bind:name="names[5]" v-bind:today="todays[5]" v-bind:whole="wholes[5]"></TableRow>
            <TableRow v-bind:name="names[6]" v-bind:today="todays[6]" v-bind:whole="wholes[6]"></TableRow>
            <TableRow v-bind:name="names[7]" v-bind:today="todays[7]" v-bind:whole="wholes[7]"></TableRow>
            <TableRow v-bind:name="names[8]" v-bind:today="todays[8]" v-bind:whole="wholes[8]"></TableRow>
            <TableRow v-bind:name="names[9]" v-bind:today="todays[9]" v-bind:whole="wholes[9]"></TableRow>
            <TableRow v-bind:name="names[10]" v-bind:today="todays[10]" v-bind:whole="wholes[10]"></TableRow>
            <TableRow v-bind:name="names[11]" v-bind:today="todays[11]" v-bind:whole="wholes[11]"></TableRow>
            <TableRow v-bind:name="names[12]" v-bind:today="todays[12]" v-bind:whole="wholes[12]"></TableRow>
            <TableRow v-bind:name="names[13]" v-bind:today="todays[13]" v-bind:whole="wholes[13]"></TableRow>
            <TableRow v-bind:name="names[14]" v-bind:today="todays[14]" v-bind:whole="wholes[14]"></TableRow>
            <TableRow v-bind:name="names[15]" v-bind:today="todays[15]" v-bind:whole="wholes[15]"></TableRow>
            <TableRow v-bind:name="names[16]" v-bind:today="todays[16]" v-bind:whole="wholes[16]"></TableRow>
            <TableRow v-bind:name="names[17]" v-bind:today="todays[17]" v-bind:whole="wholes[17]"></TableRow>
            <TableRow v-bind:name="names[18]" v-bind:today="todays[18]" v-bind:whole="wholes[18]"></TableRow>
            <TableRow v-bind:name="names[19]" v-bind:today="todays[19]" v-bind:whole="wholes[19]"></TableRow>
            <TableRow v-bind:name="names[20]" v-bind:today="todays[20]" v-bind:whole="wholes[20]"></TableRow>
            <TableRow v-bind:name="names[21]" v-bind:today="todays[21]" v-bind:whole="wholes[21]"></TableRow>
            <TableRow v-bind:name="names[22]" v-bind:today="todays[22]" v-bind:whole="wholes[22]"></TableRow>
            <TableRow v-bind:name="names[23]" v-bind:today="todays[23]" v-bind:whole="wholes[23]"></TableRow>
            <TableRow v-bind:name="names[24]" v-bind:today="todays[24]" v-bind:whole="wholes[24]"></TableRow>
            <TableRow v-bind:name="names[25]" v-bind:today="todays[25]" v-bind:whole="wholes[25]"></TableRow>
            <TableRow v-bind:name="names[26]" v-bind:today="todays[26]" v-bind:whole="wholes[26]"></TableRow>
            <TableRow v-bind:name="names[27]" v-bind:today="todays[27]" v-bind:whole="wholes[27]"></TableRow>
            <TableRow v-bind:name="names[28]" v-bind:today="todays[28]" v-bind:whole="wholes[28]"></TableRow>
            <TableRow v-bind:name="names[29]" v-bind:today="todays[29]" v-bind:whole="wholes[29]"></TableRow>
            <TableRow v-bind:name="names[30]" v-bind:today="todays[30]" v-bind:whole="wholes[30]"></TableRow>
            <TableRow v-bind:name="names[31]" v-bind:today="todays[31]" v-bind:whole="wholes[31]"></TableRow>
            <TableRow v-bind:name="names[32]" v-bind:today="todays[32]" v-bind:whole="wholes[32]"></TableRow>
            <TableRow v-bind:name="names[33]" v-bind:today="todays[33]" v-bind:whole="wholes[33]"></TableRow>
            <TableRow v-bind:name="names[34]" v-bind:today="todays[34]" v-bind:whole="wholes[34]"></TableRow>
            <TableRow v-bind:name="names[35]" v-bind:today="todays[35]" v-bind:whole="wholes[35]"></TableRow>
            <TableRow v-bind:name="names[36]" v-bind:today="todays[36]" v-bind:whole="wholes[36]"></TableRow>
            <TableRow v-bind:name="names[37]" v-bind:today="todays[37]" v-bind:whole="wholes[37]"></TableRow>
            <TableRow v-bind:name="names[38]" v-bind:today="todays[38]" v-bind:whole="wholes[38]"></TableRow>
            <TableRow v-bind:name="names[39]" v-bind:today="todays[39]" v-bind:whole="wholes[39]"></TableRow>
            <TableRow v-bind:name="names[40]" v-bind:today="todays[40]" v-bind:whole="wholes[40]"></TableRow>
            <TableRow v-bind:name="names[41]" v-bind:today="todays[41]" v-bind:whole="wholes[41]"></TableRow>
            <TableRow v-bind:name="names[42]" v-bind:today="todays[42]" v-bind:whole="wholes[42]"></TableRow>
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
                        let var1 = JSON.parse(response)["data"];
                        for (let var2 = 0; var2 < var1.length; var2++) {
                            let var3 = parseFloat(var1[var2]["tolastdistence"]);
                            if (var3 >= 1 && parseFloat(var1[var2]["totalspeed"]) < 9) {
                                dataList[dateList2[i]][1] += var3;
                            }
                        }
                        doneTask();
                    });
            }

            for (let i = 0; i < dateList.length; i++) {
                taskList2[taskList2.length] = getPage("https://jinhuaschool.smart-run.cn/report/student/record?student_no=" + dateList[i][1] + "&day=" + dateList[i][2])
                    .then(function(response) {
                        let var1 = JSON.parse(response)["data"];
                        for (let j = 0; j < var1.length; j++) {
                            let var3 = parseFloat(var1[j]["tolastdistence"]);
                            if (var3 >= 1 && parseFloat(var1[j]["totalspeed"]) < 9) {
                                dataList[dateList[i][0]][2] += var3;
                            }
                        }
                        doneTask();
                    });
            }

            await Promise.all(taskList2);

            this.tmpList = JSON.parse(JSON.stringify(dataList));

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
                        let var1 = JSON.parse(response)["data"];
                        for (let var2 = 0; var2 < var1.length; var2++) {
                            let var3 = parseFloat(var1[var2]["tolastdistence"]);
                            if (var3 >= 1) {
                                dataList[i][1] += var3;
                            }
                        }
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
