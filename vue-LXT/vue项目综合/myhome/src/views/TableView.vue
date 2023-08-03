<template>
    <div id="box">
        <div class='main'>
     <ul class="tab-nav">
      <li v-for="(tab, index) in tabs" :key="index" :class="tab.active?' tab-active':''" @click="changeTab(index)">
        {{ tab.title }}
      </li>
    </ul>
    <div class="tab-content">
      <div v-for="(tab, index) in tabs" :key="index" v-show="tab.active">
        {{ tab.content }}
      </div>
    </div>
</div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            tabs: [
                    { title: '1', active: true, content: '第一页' },
                    { title: '2', active: false, content: '第二页' },
                    { title: '3', active: false, content: '第三页' },
                ]
        }
    },
    methods: {
            changeTab(index) {
                this.tabs.forEach((tab, i) => {
                    tab.active = i === index;
                });
            }
        }
}
</script>

<style lang="scss" scoped>
        * {
            margin: 0;
            padding: 0;
            list-style: none;
            text-decoration: none;
        }

        .main {
            width: 500px;
            height: 550px;
            margin: auto;
        }

        .tab-nav {
            width: 500px;
            height: 50px;
            margin: auto;
            /* background-color: red; */
        }

        .tab-nav li {
            cursor: pointer;
            width: 166.66666px;
            height: 50px;
            float: left;
            line-height: 50px;
            text-align: center;
        }


        .tab-content {
            width: 500px;
            margin: auto;
            height: 500px;
            line-height: 500px;
            text-align: center;
            font-size: 50px;
            font-weight: 900;
            border: 1px solid black;
        }

        .tab-active {
            background-color: brown;
        }
</style>