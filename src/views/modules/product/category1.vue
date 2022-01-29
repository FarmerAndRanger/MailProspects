<template>
     <div>
         <el-tree :data="menus" :props="defaultProps" @node-click="handleNodeClick"></el-tree> 
     </div>
   
</template>

<script>
export default {
    name: 'category',
    components: {},
    directives: {},
     data() {
      return {
        data: [],
        defaultProps: {
          children: "children",
        label: "name"
        }
      };
    },
    mounted() {
        
    },
    methods: {
        handleNodeClick(data) {
        console.log(data);
      },
    //   getMenus(){
    //     this.$http({
    //       url: this.$http.adornUrl('/product/category/list/tree'),
    //       method: 'get'
    //     }).then(data=>{
    //         console.log(data)
    //     })
    //   }
    getMenus() {
      this.$http({ // http://localhost:10000/renren-fast/product/category/list/tree
        url: this.$http.adornUrl("/product/category/list/tree"),
        method: "get"
      })
        .then(({ data }) => { // success
          this.menus = data.data; // 数组内容，把数据给menus，就是给了vue实例，最后绑定到视图上
        }) //fail
        .catch(() => {});
    }




    },
    created(){
        this.getMenus();
    }
};
</script>

<style scoped>

</style>
