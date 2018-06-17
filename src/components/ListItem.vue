<template>
   <li class="list-item" :class="{isStarred: item.star}">
      <div class="panel-top">
         <div class="main">
            <div>
               <el-checkbox class="checkbox" v-model="item.complete"></el-checkbox>
               <input type="text" class="title" v-model="item.title" :style="{'text-decoration': item.complete? 'line-through': ''}">
            </div>
            <div>
               <i class="fa-star" @click="item.star=!item.star" :class="{isStarred: item.star, far: !item.star, fas: item.star}"></i>

               <i class="fas fa-pencil-alt" @click="open=!open" :class="{open: open}"></i>
            </div>
         </div>
         <div class="second">
            <i class="fas fa-calendar-alt"></i>
            <span class="date">{{item.date}}</span>
            <i class="fas fa-file"></i>
            <i class="fas fa-comment-dots"></i>
         </div>
      </div>
      <div class="panel-bottom" v-if="open">
         <div class="controls">
            <h3>
               <i class="far fa-calendar-alt"></i>
               <span>Deadline</span>
            </h3>
            <el-date-picker v-model="item.date" value-format="yyyy/MM/dd">

            </el-date-picker>
            <h3>
               <i class="far fa-file"></i>
               <span>File</span>
            </h3>
            <h3>
               <i class="far fa-comment-dots"></i>
               <span>Comment</span>
            </h3>
            <el-input class="title">
               rows="5" type="textarea", placeholder="Type your memo here..."
            </el-input>
         </div>
         <div class="btns">
            <div class="btn cancel" @click="open=false">
               <i class="fa fa-times"></i>
               <span>Cancel</span>
            </div>
            <div class="btn task">
               <i class="fa fa-plus"></i>
               <span>Add Task</span>
            </div>
         </div>
      </div>
      <!-- {{item.title}} -->
   </li>
</template>

<style lang="scss">
   $c_blue: #4A90E2;
   $c_DarkBlue: #00408B;
   $c_red: #D0021B;
   $c_yellow: #f5a623;
   $c_lightYellow: #fff2dc;
   $c_greylight: #f2f2f2;
   $c_graymid: #c8c8c8;
   $c_grayDark: #757575;

   @mixin trans {
      transition: 0.5s
   }


   .list-item {
      width: 100%;
      margin-bottom: 8px;
      &.isStarred {
         .panel-top,
         .panel-bottom {
            background-color: #FFF2DC;

         }
      }
      .main {
         display: flex;
         align-items: center;
         justify-content: space-between;

         .title {
            font-size: 24px;
            background-color: transparent;
            border: none;
            outline: none;
         }
         i {
            @include trans;
            &.open {
               color: $c_blue;
            }
            &.isStarred {
               color: $c_yellow;
            }
            font-size: 24px;
            margin-right: 32px;
            &:last-child {
               margin-right: 0;
            }
         }
      }
      .second {
         margin-top: 15px;
         color: $c_grayDark;
         i {
            margin-right: 16px;
         }
         .date {
            margin-right: 16px;
         }
      }
      .panel-top,
      .panel-bottom {
         padding-left: 40px;
         background-color: #f2f2f2;
         padding: 24px 32px;
         .el-checkbox {
            margin-left: -16px;
            transform: scale(1.7) translateX(-5px)
         }

      }
      .panel-top{
         padding-left: 65px;
      }
      .panel-bottom{
         border-top: 1px solid $c_graymid;
         padding-left: 85px;
         h3{
            margin-top: 24px;
            margin-bottom: 8px;
            &:first-child{
               margin-top: 0;
            }
            i{
               margin-right: 8px;
               margin-left: -20px;
            }
         }
      }
      .btns{
         margin: 24px -32px -24px -85px;
         display: flex;
         .btn{
            padding: 16px;
            text-align: center;
            font-size: 24px;
            font-weight: 300;
            cursor: pointer;
            flex:1;
            @include trans;
            i{
               margin-right: 14px;
            }
            &.cancel{
               background-color: #fff;
               color: $c_red;
               &:hover{
                  background-color: $c_red;
                  color: white;
               }

            }
            &.task{
               background-color: $c_blue;
               color: white;
               &:hover{
                  background-color: darken($c_blue, 10);
               }
            }

         }
      }
   }
</style>


<script>
   export default {
      props: {
         item: Object
      },
      data() {
         return {
            open: false,
         }
      }
   }
</script>