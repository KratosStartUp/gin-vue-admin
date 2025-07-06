<template>
  <el-container>
    <el-header>
      <div class="headerContent">
        <div>
          <el-image
            style="width: 50px; height: 50px"
            src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
            fit="fill"
          ></el-image>
          <p>Leap</p>
        </div>
        <div>
          <p>Features</p>
          <p>Pricing</p>
          <p>Community</p>
          <el-button type="primary">Login</el-button>
        </div>
      </div>
    </el-header>
    <el-main>
      <div class="mainContent">
        <h1 class="slogon">DIscover Amazing Content</h1>
        <p class="slogonDescription">
          Explore a curated feed of inspiring posts,videos,and articles from
          creators around the world.
        </p>
        <el-row :gutter="20">
          <el-col
            :xs="24"
            :sm="12"
            :md="6"
            v-for="(card, index) in cardList"
            :key="index"
            style="padding-top: 10px"
          >
            <el-card
              class="card"
              :body-style="{ padding: '0px' }"
              shadow="hover"
            >
              <div class="top">
                <el-row>
                  <el-col :xs="5" :sm="5" :md="5">
                    <el-image :src="card.avatar" fit="fill"></el-image>
                  </el-col>
                  <el-col :xs="19" :sm="19" :md="19">
                    <p>{{ card.title }}</p>
                    <span>作者：{{ card.author }}</span>
                  </el-col>
                </el-row>
              </div>
              <div class="mid">
                <div>{{ card.description }}</div>
                <el-image :src="card.image" fit="fill"></el-image>
              </div>
              <div class="bot">
                <el-icon><View /></el-icon>{{ card.showNum }}
              </div>
            </el-card>
          </el-col>
        </el-row>
      </div>
    </el-main>
    <el-footer>
      <div class="footerContent">
        <el-image
          src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
          fit="fill"
        ></el-image>
        <span>Leap</span>
      </div>
      <div>© 2025 Leap Inc. All Rights Reserved.</div>
    </el-footer>
  </el-container>
</template>

<script setup lang="ts">
import { ref } from "vue";

const cardList = ref([
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品1",
    author: "作者1",
    description:
      "这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，这是产品1的详细描述内容，",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品2",
    author: "作者2",
    description:
      "This is by far the most awesome screenshottool l have ever seen. l have been using itsince its beta release and l'm in love with thisone. A very great job & congratulations",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品3",
    author: "作者3",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品4",
    author: "作者4",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品5",
    author: "作者5",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品6",
    author: "作者6",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品7",
    author: "作者7",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
  {
    avatar:
      "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png",
    title: "产品8",
    author: "作者8",
    description: "这是产品1的详细描述内容",
    image:
      "https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png",
    showNum: 100,
  },
]);
</script>

<style scoped>
.el-header {
  height: 60px;
  width: 100%;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  background-color: #fff;
  color: #333;
  text-align: center;
  .headerContent {
    width: 80vw;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    div {
      display: flex;
      align-items: center;
      margin: 2.5px 20px;
      p {
        padding: 0 10px;
      }
      .el-button {
        margin-left: 20px;
      }
    }
  }
}
.el-main {
  background-color: #e9eef3;
  color: #333;
  width: 100%;
  .slogon {
    font-size: clamp(2rem, 4vw, 2.5rem);
    font-weight: 700;
    margin: 0;
    padding: 30px 0;
    min-height: 50px;
    margin: 0 auto;
    text-align: center;
  }
  .slogonDescription {
    font-size: clamp(1rem, 2.5vw, 1.2rem);
    width: 80vw;
    line-height: 20px;
    padding: 20px 0;
    text-align: center;
  }
  .mainContent {
    display: block;
    width: 80vw;
    margin: 0 auto;
  }
  .card {
    width: 100%;
    display: block;
    border-radius: 10px;
    height: auto;
    .top {
      width: 100%;
      height: 60px;
      padding-top: 10px;
      .el-row {
        width: 100%;
        height: 100%;
        .el-col {
          height: 100%;
          .el-image {
            display: block;
            width: 50px;
            height: 50px;
            border-radius: 25px;
            margin: 2.5px auto;
          }
          p {
            font-size: clamp(1rem, 2vw, 1.2rem);
            text-align: left;
            line-height: 30px;
            font-weight: 700;
            height: 30px;
            padding-left: 10px;
          }
          span {
            text-align: left;
            font-size: clamp(0.8rem, 1vw, 0.9rem);
            line-height: 30px;
            display: block;
            height: 30px;
            padding-left: 10px;
          }
        }
      }
    }
    .mid {
      width: 100%;
      padding-top: 10px;
      div {
        width: 90%;
        margin: 0 auto;
        padding: 5px 10px;
        font-size: clamp(0.8rem, 1vw, 0.9rem);
        line-height: 25px;
        display: -webkit-box;
        -webkit-line-clamp: 5; /* 限制*行 */
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis; /* 超出部分显示... */
      }
      .el-image {
        display: block;
        width: 90%;
        aspect-ratio: 16/9;
        margin: 0 auto;
        border-radius: 10px;
        box-sizing: border-box;
        background: linear-gradient(135deg, rgb(102, 168, 250), #fff);
        padding: 20px;
      }
    }
    .bot {
      width: 90%;
      height: 20px;
      line-height: 20px;
      margin: 0 auto;
      padding: 10px 0;
      .el-icon {
        padding-right: 10px;
        height: 100%;
      }
    }
  }
}
.el-footer {
  display: block;
  height: auto;
  width: 100%;
  background-color: black;
  color: #ffffff;
  text-align: center;
  div{
    margin:10px 0;
  }
  .footerContent {
    display: flex;
    justify-content: center;
    align-items: center;
    .el-image {
      width: 50px;
      height: 50px;
      padding-right:10px;
    }
    span {
      display: inline-block;
      height: 50px;
      line-height: 50px;
    }
  }
}
</style>
