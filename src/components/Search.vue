<template>
    <div class="container">
        <input type="text" 
        v-model="title" 
        placeholder="Search for Movies,series & more"
        class="form-control"/>
        <div class="selects">
            <select 
              v-for="filter in filters" 
              v-model="$data[filter.name]"
              :key="filter.name"
              class="form-select"
              @keyup.enter="apply"
            > 
               <option v-if="filter.name==='year'" value="">All Years</option>
                <option 
                v-for="item in filter.items" 
                :key="item">
                   {{item}}
                </option>
            </select>
        </div>
        <button class="btn btn-primary" @click="apply">Apple</button>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return{
            title:'',
            type:'movie',
            number:10,
            year:'',
            filters:[
                {
                    name:'type',
                    items:['movie','series','episode']
                },
                {
                    name:'num',
                    items:[10,20,30]
                },
                {
                    name:'year',
                    items:(()=>{
                        const years = []
                        const thisYear= new Date().getFullYear()//RECENT YEAR
                        for (let i =thisYear; i>=1985; i-=1){
                            years.push(i)
                        }
                       return years
                    })()
                }

            ]
        }
    },
    methods:{
        async apply(){
            //serach movies..
            const OMDB_API_KEY='7035c60c'
            const res = await axios.get(`http://www.omdbapi.com/?apikey=${OMDB_API_KEY}&s=${this.title}&type=${this.type}&y=${this.year}&page=1`)
        }
    }
}
</script>
<style lang="scss">
    .container { 
        display:flex;
        > * {
            margin-right: 10px;
            font-size: 15px;
            &:last-child{
                margin-right:0
            }
        }
        .selects{
            display:flex;
            select {
                width: 120px;
                margin-right:10px;
                &:last-child{
                 margin-right:0
                }
                }
           
        }
        .btn{ 
            width: 120px;
            height: 50px;
            font-weight: 700;
            flex-shrink: 0;
        }

    }
</style>