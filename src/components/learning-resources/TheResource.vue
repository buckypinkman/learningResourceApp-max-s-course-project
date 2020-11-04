<template>
    <div>
        <base-card>
            <base-button :mode="storedTab" @click="setSelectedTab('stored-resource')" style="margin-right: 6px">Stored Resource</base-button>
            <base-button :mode="addResourceTab" @click="setSelectedTab('add-resource')">Add Resource</base-button>
        </base-card>
        <component :is="selectedTab"></component>
        
    </div>
</template>

<script>
    import StoredResource from './StoredResource'
    import AddResource from './AddResource'

    export default {
        data() {
            return {
                selectedTab: 'stored-resource',
                storedResources: [
                    {
                        id: '1',
                        title: 'Tutorial Something',
                        description: 'Some dummy text to fill the description.',
                        link: 'https://google.com'
                    },
                    {
                        id: '2',
                        title: 'Tutorial Vue',
                        description: 'Some other dummy text to fill the description.',
                        link: 'https://vue.org'
                    },
                    {
                        id: '3',
                        title: 'React Tutorial',
                        description: 'lorem ipsum dolor sit amet consectetur adipisicing elit.',
                        link: 'https://react.org'
                    }
                ]
            }
        },
        provide() {
            return {
                resources: this.storedResources,
                addResource: this.addResource,
                deleteResource: this.deleteResource
            }
        },
        methods: {
            setSelectedTab(tab) {
                this.selectedTab = tab
            },
            addResource(title,description,link) {
                const newResource = {
                    id: new Date().toISOString(),
                    title: title,
                    description: description,
                    link: link
                }
                this.storedResources.unshift(newResource)
                this.selectedTab = 'stored-resource'
            },
            deleteResource(resId) {
                const resIndex = this.storedResources.findIndex(res => res.id == resId)
                this.storedResources.splice(resIndex, 1)
            }
        },
        computed: {
            storedTab() {
                return this.selectedTab == 'stored-resource' ? null : 'flat'
            },
            addResourceTab() {
                return this.selectedTab == 'add-resource' ? null : 'flat'
            }
        },
        components: {
            StoredResource,
            AddResource
        }
    }
</script>

<style scoped>
    
</style>