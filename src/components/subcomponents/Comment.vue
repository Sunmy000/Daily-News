<template>
  <div class="cmt-container">
      <h3>发表评论</h3>
      <hr>
      <textarea placeholder="请输入要评论的内容（最多吐槽120字）" maxlength="120"></textarea>

      <mt-button type="primary" size="large">发表评论</mt-button>
      <div class="cmt-list">
          <div class="cmt-item" v-for="(item,i) in comments" :key="item.add_time">
              <div class="cmt-title">
                  第{{ i+1 }}楼&nbsp;&nbsp;用户：{{ item.user_name }}&nbsp;&nbsp;发表时间：{{item.add_time | dataFormat}}
              </div>
              <div class="cmt-body">
                {{ item.content === 'undefined' ? '此用户很懒，并没有说什么': item.content}}
              </div>
          </div>
      </div>   
      <mt-button type="danger" size="large" plain @click="getMore">加载更多</mt-button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            pageIndex: 1, // 默认展示第一页数据
            comments: [] // 所有的评论数据 
        }
    },
    created(){
        this.getComment();
    },
    methods: {
        getComment() {
            this.$http.get('api/getcomments/'+this.id+'?pageindex='+this.pageIndex).then(result => {
                if(result.body.status === 0){
                    // 每当获取新评论的时候，不清除就数据，而是进行拼接
                    this.comments = this.comments.concat(result.body.message);
                }else {
                    Toast('获取评论失败')
                }
            })
        },
        getMore() { //加载更多
            this.pageIndex++;
            this.getComment();
        }
    },
    props: ["id"]
}
</script>

<style lang="scss" scoped>
.cmt-container {
    h3 {
        font-size: 18px;
    }
    textarea {
        font-size: 14px;
        height: 85px;
        margin: 0;
    }
    .cmt-list {
        margin: 5px 0;
        .cmt-item{
            font-size: 13px;
            .cmt-title{
                line-height: 30px;
                background-color: #ccc;
            }
            .cmt-body {
                line-height: 35px;
                text-indent: 2em;
            }
        }
    }
}
</style>

