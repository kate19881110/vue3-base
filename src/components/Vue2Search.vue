<template lang="">
    <div>
        <div>
            <input type="text" v-model="searchTerm" placeholder="搜索標題...">
            <select v-model="category">
                <option value="all">全部</option>
                <option value="vue">Vue</option>
                <option value="react">React</option>
                <option value="javascript">Javascript</option>
                <option value="css">CSS</option>
            </select>
        </div>
        <div>
            <div v-for="blog in resultBlogs" :key="blog.id">
                <h2>{{blog.title}}</h2>
                <p>分類: {{blog.category}}</p>
                <p>作者: {{blog.author}}</p>
                <p>發佈日期: {{blog.pubDate}}</p>
                <p>內容: {{blog.content}}</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Vue2Search',
    data(){
        return{
            searchTerm: "",
            category: "all",
            blogs:[
                {
                    id:1,
                    title: "Vue 完全指南教程",
                    category: "vue",
                    author: "張三",
                    pubDate: "2022-01-01",
                    content: "Vue博客內容"
                },
                {
                    id:2,
                    title: "TypeScript 對應手冊",
                    category: "typeScript",
                    author: "老四",
                    pubDate: "2022-02-02",
                    content: "TypeScript博客內容"
                },
                {
                    id:3,
                    title: "React 對症下藥",
                    category: "react",
                    author: "陳五",
                    pubDate: "2023-03-03",
                    content: "React博客內容"
                }
            ]
        }
    },
    computed:{
        resultBlogs(){
            let result = this.searchBlogs(this.blogs);
            result = this.filterBlogs(result);
            return result;
        }
    },
    methods: {
        searchBlogs(blogs){
            if(this.searchTerm === "") return blogs;
            return blogs.filter((blog)=>{
                return blog.title.includes(this.searchTerm)
            })
        },
        filterBlogs(blogs){
            if(this.category==="all") return blogs;
            return blogs.filter((blog)=>{
                return blog.category === this.category;
            })
        }
    },
    
}
</script>
<style lang="">
    
</style>