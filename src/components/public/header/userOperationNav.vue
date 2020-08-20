<template>
    <div class="userOperationNav-box">
        <div class="userOperationNav">
            <!--这是左侧的盒子 -->
            <div class="userOperationNav-left">
                <p>您好,欢迎来到&nbsp;&nbsp;<span>惠播客</span></p>
                <ul class="loginUL">
                    <li v-for="(item,index) in leftNav" :key="index">
                        {{item}}
                        <span class="Cuttingline" v-show="index==0"></span>
                    </li>
                   
                </ul>
            </div>
            <!-- 这是右侧的盒子 -->
            <div class="userOperationNav-right">
                <ul class="Navul">
                    <li 
                        v-for="(item,index) in rightNav" 
                        :key="index"
                        class="NavulLi"
                        @mouseover="fathernav(index)"
                        @onmouseout="fathernavout"
                        ref="NavulLi"
                    >
                        {{item}}
                        <div class="triangle" v-show="index!==4"></div>
                        <div class="navLiPopup" v-show="navLiindex==index">
                            <!-- {{rightnavchild[index]}} -->
                            <ul class="Popupul">
                                <li 
                                    v-for="(items,indexs) in rightnavchild[index]" 
                                    :key="indexs"
                                    class="Popupli"
                                >
                                    <a class="Popupli_span">{{items}}</a>
                                </li>
                            </ul>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data(){
            return {
                leftNav:["请登录","免费注册"],
                rightNav:["商家中心","我的收藏","客户中心","快捷导航","微信端"],
                rightnavchild:[
                    ["商家入驻","商家登录"],
                    ["商品收藏","店铺收藏"],
                    ["帮助中心","售后服务","投诉中心"],
                    ["品牌","店铺街"]
                ],
                navLiindex:-1
            }
        },
        methods:{
            fathernav(indexs){
                // console.log(e.stopPropagation)
              this.navLiindex = indexs
            },
            //当鼠标移入的时候
            fathernavout(){
              this.navLiindex = -1  
            }
        }
    }
</script>
<style lang="less">
    @fontcolor:#7f7f7a;
    @fontSize:12px;
    .userOperationNav-box{
        background-color:#f5f4f4;
        .userOperationNav{
            display:flex;
            justify-content: space-between;
            max-width:1200px;
            // background-color:yellow;
            margin:0 auto;
            line-height:30px;
            .userOperationNav-left{
                display:flex;
                justify-content:space-around;
                width:30%;
                height:30px;
                // background-color:red;
                p{
                    font-size:@fontSize;
                    color:@fontcolor;
                    span{
                        color:#000;
                    }
                }
                .loginUL{
                    display:flex;
                    li{
                        font-size:@fontSize;
                        color: @fontcolor;
                        .Cuttingline{
                            border-right:1px solid @fontcolor;
                            height:8px;
                            font-weight: bold;
                            margin:0 7px;
                        }
                    }
                    
                }
            }
            .userOperationNav-right{
                width:40%;
                // background-color:green;
                .Navul{
                    display:flex;
                    .NavulLi{
                        position: relative;
                        display:flex;
                        align-items: center;
                        font-size:@fontSize;
                        color: @fontcolor;
                        // margin-right:20px;
                        padding:0 10px 0 15px;
                        .triangle{
                            width: 0;
                            height: 0;
                            border: 5px solid transparent;
                            border-top-color: #cecece;
                            border-bottom: none;
                            border-left-color: transparent;
                            border-right-color: transparent;
                            margin-left:5px;
                        }
                        .navLiPopup{
                            position: absolute;
                            top:30px;
                            left:0;
                            width: 100%;
                            height:100px;
                            // background-color:green;
                            background-color: #fff;
                            // border:1px solid #ccc;
                            // border-top:0;
                            .Popupul{
                                
                                .Popupli{
                                    text-align:center;
                                    border-bottom:0;
                                    .Popupli_span{
                                        padding-bottom:5px;
                                        transition: .3s;
                                    }
                                    &:hover .Popupli_span{
                                        border-bottom:1px solid red;
                                        color:red;
                                    }
                                }
                            }
                        }
                        &:last-child{
                            margin-right:0;
                        }
                        &:hover{
                            background-color: #fff;
                        }
                    }
                }
            }
        }
    }
</style>