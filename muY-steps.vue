<template>
  <div class="bg">
    <div class="steps">
      <div class="steps_item" v-for="(item, index) in infoList" :key="item.id">
        <div class="s_l">
          <div class="index"></div>
          <div
            class="line"
            :style="{
              backgroundColor: index != infoList.length - 1 ? backgroundColor : 'rgba(0,0,0,0)'
            }"
          ></div>
        </div>
        <div class="s_r">
          <div class="s_wrap" @tap="topage(index)">
            <div class="s_content">
              <div style="min-width: 115px">{{ item.submitTime }}</div>
              <div class="content-wrap wid100">
                <div class="content_r">
                  <div>{{ item.submiterName }}&nbsp;&nbsp;&nbsp;&nbsp;{{ item.behavior }}</div>
                </div>
                <div class="content-reason">
                  <div>{{ item.remark }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'YiSteps',
  props: {
    infoList: {
      type: Array,
      default: [],
    },
    backgroundColor: {
      type: String,
      default: '#4170ff'
    }
  },
  data() {
    return {
    }
  },
  methods: {
    topage(e) {
      this.$emit('click', e)
    }
  }
}
</script>

<style lang="less" scoped>
div,
span {
  color: #a1a1a1;
}

.wid100 {
  width: 100%;
}
.bg {
  background-color: #fff;
  display: flex;
}

.steps {
  width: 100%;
  display: flex;
  flex-direction: column;

  .steps_item {
    display: flex;
    min-height: 68px;
    .s_l {
      padding-right: 10px;
      display: flex;
      flex-direction: column;
      align-items: center;

      .line {

        width: 2px;
        height: 100%;
        background-color: #fff;
      }

      .index {
        width: 12px;
        height: 12px;
        font-size: 14px;
        background: #0066ff;
        text-align: center;
        line-height: 12px;
        border-radius: 50%;
      }
    }

    .s_r {
      flex: 1;
      align-items: center;
      margin-top: -5px;
      .s_wrap {
        flex: 1;
        color: #525252;
        background-color: #fff;
        border-radius: 10px;
        display: flex;
        .s_content {
          .content-wrap {
            display: flex;
            flex-direction: column;
            .content-reason {
              display: flex;
              margin-left: 28px;
              flex-wrap: wrap;
              padding: 2px 0 10px;
              div {
                margin-right: 10px;
              }
            }
          }
        }
        .info_name {
          font-size: 16px;
          font-weight: 600;
        }
      }

      .s_wrap:active {
        background-color: #f4f4f4;
      }
    }
  }
}
</style>
