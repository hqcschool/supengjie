<template>
      <div id="box">
        <div class="main">
        <img :src="currentImage">
        <button @click="prev" class='prev'>1</button>
        <button @click="next" class='next'>></button>
      </div>
    </div>
</template>
<script>
export default{
  data(){
    return{
      images: [
                    "https://img0.baidu.com/it/u=1617940732,1879989235&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
                    "https://img0.baidu.com/it/u=4187423482,206374644&fm=253&fmt=auto&app=120&f=JPEG?w=1280&h=800",
                    "https://img2.baidu.com/it/u=1361506290,4036378790&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500",
                    "https://img2.baidu.com/it/u=2048195462,703560066&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=333",
                    'https://img1.baidu.com/it/u=1310564963,1641173348&fm=253&fmt=auto&app=120&f=JPEG?w=1280&h=800',
                    'https://img1.baidu.com/it/u=2508381239,2324251691&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500'
                ],
                index: 0
    }
  },        computed: {
            currentImage() {
                return this.images[this.index];
            }
        },
        mounted() {
            this.startCarousel();
        },
        methods: {
            startCarousel() {
                setInterval(this.next, 2000);
            },
            prev() {
                this.index = (this.index - 1 + this.images.length) % this.images.length;
            },
            next() {
                this.index = (this.index + 1) % this.images.length;
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
        #box{
            width: 800px;
            height: 500px;
            margin: 50px auto;
        }

        img {
            width: 800px;
            height: 500px;
        }

        .main {
            width: 800px;
            height: 500px;
            position: relative;
        }


        .main button {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            width: 50px;
            height: 100px;
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            font-size: 40px;
        }

        .prev {
            left: 10px;
        }

        .next {
            right: 10px;
        }
</style>
