<template>
    <div class="ch_serve">
     <div class="ch_container">
    <!-- 股权池现金池选择 -->
    <el-tabs v-model="activeName" @tab-click="handleClick">
    <el-tab-pane label="股权池" name="first">
        <div class="el-tab_margin">
           <span>股权余量</span>
           <b>{{stockMargin}}</b>
        </div>
        <div class="el-tab_change">
           <div class="el_tab_buy">
            <img src="./images/tab_buy.png"/>
            <span>购入新的股权</span>
           </div>
           <div class="el_tab_var">
             <img src="./images/tab_change.png"/>
             <span>股票库存变动</span>
           </div>
        </div>
        <!-- 合伙人非合伙人选择 -->
         <el-tabs :tab-position="tabPosition">
         <el-tab-pane>
             <div slot="label">
              <div>合伙人</div>
              <ul>
                  <li>已授予股权数<b>{{awarded}}</b></li>
                  <li>已归属股权数<b>{{attribut}}</b></li>
              </ul>
             </div>
             <div>
                 <!-- 股权柱状图 -->
                 <div id="myChart" :style="{width: `800px`, height: `400px`}" class="myChart"></div>
                 <div class="stock_detail">
                  <h4>{{detail.year}}年股权明细</h4>
                  <div class="content_bottom">
                      <span>{{detail.rank}}</span>
                      <span>{{detail.number}}人</span>
                      <div class="stock_process">
                       <el-progress :text-inside="true" :stroke-width="10" :percentage="70" :show-text=false></el-progress>
                      </div>
                      <span class="stock_hint">
                       <t>已授予股权数:{{awarded}}</t>
                       <t>已归属股权数:{{attribut}}</t>
                      </span>
                  </div>
                 </div>
                 </div></el-tab-pane>
         <el-tab-pane>
              <div slot="label">
                  用户管理
              <ul>
                  <li>已授予股权数<b>{{awarded}}</b></li>
                  <li>已归属股权数<b>{{awarded}}</b></li>
              </ul>
             </div>
             <div>配置管理</div>
        </el-tab-pane>
        </el-tabs>
    </el-tab-pane>
    <el-tab-pane label="现金池" name="second">现金池</el-tab-pane>
  </el-tabs>
  </div>
    </div>
</template>
<script>
     export default {
      name: 'eCharts',
      data() {
      return {
        tabPosition: 'left',
        activeName: 'first',
        stockMargin:'12,303,700',
        awarded:'7,000,000',
        attribut:'7,000,000',
        detail:{
            year:"2017",
            number:"12",
            rank:"长期合伙人:",
            awarded:"10",
            attribut:"1"

        }
       };
       },
    mounted(){
      this.drawLine();
    },
    methods: {
        /*设置股权，现金池切换*/
       handleClick(tab, event) {
        console.log(tab, event);
      },
       drawLine(){

            // 基于准备好的dom，初始化echarts实例

            var myChart = this.$echarts.init(document.getElementById('myChart'))

            // 绘制图表

            myChart.setOption({
                color:['#32a0f0','#cccccc'],
                title: { text: '' },
                tooltip: {},
                xAxis: {
                    data: ['2017','2018','2019'],

                },
                yAxis: {
                },
                legend:{
                    itemWidth:15
                },
                series: [{

                    name: '已授予股权数',
                    //显示折叠柱状图
                    stack:true,
                    type: 'bar',
                    data: [20, 30, 70],
                    barMaxWidth:40

                },{

                    name: '已归属股权数',
                    stack:true,
                    type: 'bar',
                    data: [10, 20, 40],
                    barMaxWidth:40

                }]

            });

        }
    }
  };

</script>
<style lang="less" scoped>
*{
    margin:0;
    padding:0;
}
ul,li{
    list-style:none;
}
@fontColor:#el-tab_margin;
.ch_serve{
   padding-top:10px;
   padding-left:10px;
   padding-right:10px;
     .ch_container{
        width:85%;
        background:#e8edf3;
        border-radius:5px;
        /deep/.el-tabs__header{
            padding-left:20px;
        /deep/.el-tabs__item{
            font-size:16px;
            }
         }
         /deep/.el-tabs__content{
            padding-left:20px; 
            padding-right:10px;
            .el-tab_margin{
               span{
                   color:@fontColor;
                   margin-right:100px;
               }
               b{
                  color:#999999;
               }
               margin-bottom:20px;
            }
            .el-tab_change{
                .el_tab_buy{
                    img{
                        margin-right:10px;
                    }
                    span{
                       line-height:23px;
                    }
                }
                .el_tab_var{
                    img{
                        margin-right:10px;
                    }
                }
                margin-bottom:20px;
            }
            // 合伙人非合伙人选择
            .el-tabs--left{
                background:#ffffff;
                .el-tabs__item{
                   line-height:normal;
                   height:auto;
                   border-bottom:1px solid #e1e1e1;
                   padding-left:10px;
                   div:nth-child(1){
                       div:nth-child(1){
                           font-size:17px;
                           line-height:30px;

                       }
                       ul{
                           li{
                               font-size:15px;
                               line-height:20px;
                               padding-left:10px;
                               b{
                                   margin-left:20px;
                                   margin-bottom:10px;
                                   position:relative;
                                   top:-5px;
                               }
                           }
                           li:nth-child(1){
                               b{
                                   margin-left:25px;
                                   color:#32a0f0;
                               }
                           }
                       }
                   }
                }
                .el-tabs__header{
                    padding-left:0;
                }
                .el-tabs__content{
                    border-left:2px solid #cbcdcf;
                }
                .el-tabs__item:hover{
                    color:#000;
                }
                .is-left{
                    text-align:left;
                    margin-right:0;
                }
                .is-active{
                       color:black;
                       background:#f7f7f7;
                   }
            }
            .myChart{
                border-bottom:1px solid #797979; 
            }
            .stock_detail{
               padding-top:10px;
               line-height:40px;
               //股权详情
               .content_bottom{
                   position:relative;
                   span:nth-child(1){
                     display:inline-block;
                     width:15%;
                   }
                   span:nth-child(2){
                      margin-right:20px;
                   }
                  .stock_process{
                    display:inline-block;
                    width:50%;
                }
                  .stock_hint{
                    // position:absolute;
                    // left:30%;
                    border:1px solid #797979;
                    t{
                      font-size:14px;  
                    }
                    
                }
               }
            }
         }
        }
      }

</style>
