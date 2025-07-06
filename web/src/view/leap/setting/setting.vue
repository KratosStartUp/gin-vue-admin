<template>
  <div class="app-container">
    <el-card>
      <p class="title">通用</p>
      <el-collapse class="custom-collapse" @change="handleChange">
        <el-collapse-item name="1">
          <template #title>
            <div class="title_content">
              <div>
                <p>产品</p>
                <span>用于在网络上识别你的 landing page 的详细信息。</span>
              </div>
              <el-button>{{ buttonNameList[0] }}</el-button>
            </div>
          </template>
          <div class="avatarArea">
            <el-avatar
              src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
            ></el-avatar>
            <el-button>Change</el-button>
          </div>
          <div class="input_area">
            <label>Name</label>
            <el-input></el-input>
          </div>
          <div class="input_area">
            <label>Tagline</label>
            <el-input></el-input>
          </div>
        </el-collapse-item>
        <el-collapse-item name="2">
          <template #title>
            <div class="title_content">
              <div>
                <p>Public site URL</p>
                <span>分享到网络的落地页将位于 jingle.bio/strenger</span>
              </div>
              <el-button>{{ buttonNameList[1] }}</el-button>
            </div>
          </template>
          <div class="input_area">
            <label>My Jingle Bio URL</label>
            <el-input></el-input>
          </div>
          <div class="input_area">
            <label>Custom URL</label>
            <el-input></el-input>
          </div>
        </el-collapse-item>
        <el-collapse-item name="3">
          <template #title>
            <div class="title_content">
              <div>
                <p>语言</p>
                <span>
                  选择访客将查看你的网站的语言。这适用于你未自定义的文本，例如默认按钮，错误等。
                </span>
              </div>
              <el-button>{{ buttonNameList[2] }}</el-button>
            </div>
          </template>
          <div class="input_area">
            <el-select v-model="language">
              <el-option label="English" value="en"></el-option>
              <el-option label="简体中文" value="zh"></el-option>
            </el-select>
          </div>
        </el-collapse-item>
        <div class="title_content">
          <div>
            <p>转化通知</p>
            <span>
              当一个新的转化动作在你的 landing page 页面上被触发时，你将会收到一封邮件通知。
            </span>
          </div>
          <el-switch
            v-model="switchOff"
            active-color="#13ce66"
            inactive-color="#ff4949"
            style="margin-right: 40px"
          ></el-switch>
        </div>
      </el-collapse>
    </el-card>
    <el-card style="margin-top: 20px">
      <p class="title">Site meta settings</p>
      <el-collapse class="custom-collapse" @change="handleChange2">
        <el-collapse-item name="4">
          <template #title>
            <div class="title_content">
              <div>
                <p>元数据</p>
                <span>设置你的落地页在网络上以及在社交媒体上分享时的显示方式</span>
              </div>
              <el-button>{{ buttonNameList[3] }}</el-button>
            </div>
          </template>
          <div class="metaSettings">
            <div>
              <div class="input_area">
                <label>元标题</label>
                <el-input></el-input>
                <span>建议输入：70 个字符。您已使用0 个字符</span>
              </div>
              <div class="input_area">
                <label>元描述</label>
                <el-input type="textarea"></el-input>
                <span>建议：156 个字符。您已使用0 个</span>
              </div>
            </div>
            <div class="metaSettings_right">
              <label>Search engine result preview</label>
              <div>
                <div>
                  <svg-icon icon-class="block" />
                  <div>
                    <svg-icon icon-class="serch" />
                  </div>
                </div>
                <span>strenger.newpage.im</span>
                <span>Strenger</span>
                <span>A good man!!</span>
              </div>
            </div>
          </div>
        </el-collapse-item>
        <el-collapse-item name="5">
          <template #title>
            <div class="title_content">
              <div>
                <p>开放图形图像</p>
                <span>
                  Customize structured data that appears when you post site to your social accounts
                </span>
              </div>
              <el-button>{{ buttonNameList[4] }}</el-button>
            </div>
          </template>
          <div class="openImage">
            <div class="input_area">
              <label>开放图形图像</label>
              <el-upload
                class="upload-demo"
                drag
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
              >
                <i class="el-icon-upload"></i>
                <div class="el-upload__text">
                  将文件拖到此处，或
                  <em>点击上传</em>
                </div>
                <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div>
              </el-upload>
            </div>
            <div class="openImage_right">
              <label>Search engine result preview</label>
              <div>
                <div>
                  <span style="padding-top: 50px">Strenger</span>
                  <span style="padding-top: 30px">A good man!!</span>
                  <div style="margin-top: 30px">Get started</div>
                </div>
                <span style="padding-top: 10px">Strenger</span>
                <span>A good man!!</span>
                <span>strenger.newpage.im</span>
              </div>
            </div>
          </div>
        </el-collapse-item>
      </el-collapse>
    </el-card>
    <el-card style="margin-top: 20px">
      <p class="title">Advanced</p>
      <div class="title_content">
        <div>
          <p>将网站设为私有</p>
          <span>使用单个，易记的密码保护你的落地页。所有 SEO 和社交媒体功能将被停用。</span>
        </div>
        <el-switch
          v-model="personalOff"
          active-color="#13ce66"
          inactive-color="#ff4949"
          style="margin-right: 40px"
        ></el-switch>
      </div>
      <div class="title_content">
        <div>
          <p>移除 Leap 品牌</p>
          <span>从你的页面上移除"由 Leap 制作"的标记。</span>
        </div>
        <el-switch
          v-model="brandOff"
          active-color="#13ce66"
          inactive-color="#ff4949"
          style="margin-right: 40px"
        ></el-switch>
      </div>
    </el-card>
    <el-card style="margin-top: 20px">
      <p class="title">Danger zone</p>
      <div class="title_content">
        <div>
          <p>删除落地页</p>
          <span>注意！删除落地页将导致所有转化，成员和数据的永久丧失 - 它们无法恢复！</span>
        </div>
        <el-button type="danger" style="margin: 20px 20px 0 0">删除</el-button>
      </div>
    </el-card>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const language = ref("en");
const switchOff = ref(false);
const personalOff = ref(false);
const brandOff = ref(false);
const buttonNameList = ref(["Expand", "Expand", "Expand", "Expand", "Expand"]);

const handleChange = (val: any) => {
  changeButtonName(val);
};
const handleChange2 = (val: any) => {
  changeButtonName(val);
};
function changeButtonName(val: any) {
  buttonNameList.value.map((item: any, index: number) => {
    if (val.indexOf((index + 1).toString()) !== -1) {
      buttonNameList.value[index] = "Close";
    } else {
      buttonNameList.value[index] = "Expand";
    }
  });
}
</script>

<style lang="scss" scoped>
.app-container {
  width: 60%;
  min-width: 800px;
  margin: 0 auto;
  .el-button {
    width: 80px;
  }
}
.title {
  height: 30px;
  font-size: 20px;
  margin-top: 0;
  margin-bottom: 10px;
}
.app-container :deep() .el-collapse-item__header {
  height: 80px;
  line-height: 60px;
}
.app-container {
  label {
    display: block;
  }
  .el-input,
  .el-select {
    width: 300px;
  }
}
.title_content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 70px;
  width: 100%;
  padding: 10px 0;
  p {
    height: 30px;
    font-size: 20px;
    font-weight: 600;
    margin: 0;
  }
  span {
    height: 30px;
    font-size: 14px;
    margin: 0;
  }
}
.custom-collapse :deep(.el-collapse-item__arrow) {
  display: none !important;
}
.avatarArea {
  display: flex;
  justify-content: left;
  align-items: center;
  height: 70px;
  width: 100%;
  padding: 10px 0;
  .el-avatar {
    width: 50px;
    height: 50px;
    margin-right: 20px;
    border-radius: 50%;
  }
  .el-button {
    width: 70px;
    height: 30px;
  }
}

.input_area {
  margin: 10px 0;
}

.metaSettings {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px 0;
  > div {
    width: 50%;
    .input_area {
      width: 80%;
    }
  }
  .metaSettings_right {
    margin-top: -30px;
    > div {
      height: 150px;
      width: 100%;
      padding-top: 60px;
      border-radius: 5px;
      border: 1px solid #ccc;

      span {
        display: block;
      }
    }
  }
}
.openImage {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px 0;
  > div {
    width: 50%;
    height: 240px;
    padding: 0 10px;
  }
  .input_area {
    .upload-demo {
      width: 100%;
      height: 240px;
      .el-upload {
        height: 230px;
        .el-upload-dragger {
          height: 230px;
        }
      }
    }
  }
  .openImage_right {
    > div {
      height: 240px;
      width: 100%;
      border-radius: 5px;
      border: 1px solid #ccc;
      > div {
        height: 150px;
        background-image: url("https://cube.elemecdn.com/6/94/4d3ea53c084bad6931a56d5158a48jpeg.jpeg");
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        span {
          display: block;
          height: 20px;
          width: 100%;
          text-align: center;
        }
        div {
          height: 20px;
          width: 100px;
          background-color: #ccc;
          margin: 0 auto;
          border-radius: 15px;
          text-align: center;
        }
      }
      span {
        display: block;
        padding-left: 15px;
      }
    }
  }
}
</style>
