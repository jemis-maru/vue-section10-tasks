<template>
    <base-card>
        <base-button 
            @click="changeCurTab('stored-resources')"
            :mode="storedBaseBtnStyle">
            Stored Resources
        </base-button>
        <base-button
            @click="changeCurTab('add-resources')"
            :mode="addBaseBtnStyle">
            Add Resources
        </base-button>
    </base-card>
    <keep-alive>
        <component :is="currentTab"></component>
    </keep-alive>
</template>

<script>
import StoredResources from './StoredResource.vue';
import AddResources from './AddResource.vue';

    export default {
        components: {
            'stored-resources': StoredResources,
            'add-resources': AddResources,
        },
        data(){
            return{
                resourceArr: [
                    {
                        id: 'official-guide',
                        title: 'Official Guide',
                        description: 'Official VueJs documentation.',
                        resourceLink: 'https://vuejs.org/',
                    },
                    {
                        id: 'google-guide',
                        title: 'Google',
                        description: 'Learn with google..',
                        resourceLink: 'https://google.com/',
                    },
                ],
                currentTab: 'stored-resources',
            };
        },
        methods:{
            changeCurTab(tab){
                this.currentTab = tab;
            },
            addResFun(title, des, url){
                this.resourceArr.unshift({
                    id: new Date().toISOString(),
                    title: title,
                    description: des,
                    resourceLink: url,
                });
                this.currentTab = 'stored-resources';
            },
            removeResFun(resId){
                const ind = this.resourceArr.findIndex(res => {
                    return res.id === resId;
                });
                this.resourceArr.splice(ind, 1);
            },
        },
        computed:{
            storedBaseBtnStyle(){
                return this.currentTab === 'stored-resources' ? null : 'flat';
            },
            addBaseBtnStyle(){
                return this.currentTab === 'add-resources' ? null : 'flat';
            },
        },
        provide(){
            return{
                resources: this.resourceArr,
                addRes: this.addResFun,
                removeRes: this.removeResFun,
            };
        },
    }
</script>

<style scoped>

</style>