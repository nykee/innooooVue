<template>
  <div id="app" >
    <!--导航条-->
    <Navbar></Navbar>
    <!--路由显示-->
    <router-view></router-view>
    <!--页脚-->
    <FootBar></FootBar>
    <!--<BackToTopBtn class="toTopBtn" v-show="isToTop" ></BackToTopBtn>-->
  </div>
</template>

<script>
  import FootBar from "./components/FootBar.vue";
  import Navbar from "./components/NavBar.vue";
  // import BackToTopBtn from './components/BackToTopBtn.vue';
export default {
  data(){
    return {
      isToTop:false,
      scroll:'',
      isIndex:true
    }
  },
  methods:{

    chkScroll(){
      this.isIndex = this.$route.path ==="/";
      this.scroll = document.body.scrollTop ||document.documentElement.scrollTop;
      if(this.isIndex&&(this.scroll>100)){
        this.isShow = true;
      }
      else{
        this.isShow =false;
      }
    },
    chkIndex(){
      if(this.isIndex ===false){
        this.isShow =false;
      }
    },

  },
  mounted:function () {
    window.addEventListener('scroll', this.chkScroll)
  },
  watch:{
    '$route':'chkIndex'
  },
  components:{
    FootBar,Navbar
  }

}
</script>

<style>

body, button, select, textarea, input, label, option, fieldset, legend{font-family: 微软雅黑E\8F6F\96C5\9ED1,Tahoma,Verdana;font-size: 12px;line-height: 18px;color: #444;}
body, div, dl, dt, dd, ul, ol, li, h1, h2, h3, h4, h5, h6, pre, form, fieldset, legend, input, textarea, button, p, blockquote, th, td{margin: 0;padding: 0;}
textarea{resize: none}

a,img{border:0;}
img{vertical-align: middle}
a{color: #000 ;text-decoration: none !important;}
a:hover{
  text-decoration: none !important;
}
li{list-style-type:none;}
.navbar-default .navbar-nav>li>a:hover{
  color:#fff !important;

}
#app{
  position: relative;
}
.toTopBtn{
  position: fixed;
  right: 10px;
  bottom:100px;
}
.loginMenu{
  margin-right:20px;
  line-height: 60px;
  height: 55px;
  font-size: 14px;
  color:#BFCBD9;
  width: 50px;
  text-align: center;

}

.loginMenu a{
  color:#BFCBD9;
}
.loginMenu:hover{
  border-bottom:5px solid #20a0ff;
}
.fl{
  float: left;}
.fr{
  float: right;}
.clearfix{*zoom:1}
.clearfix:after{display:block;visibility:hidden;clear:both;height:0;content:'.';font-size:0}

.flex-container{
  display: flex;
  align-items: center;
  justify-content: center;
}


</style>
