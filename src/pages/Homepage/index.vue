<script>
export default {
  name: 'homepage',
  data(){
    return{
      clickList: ['basic'],
      checked: 0,
      basicData: [{
        id: "skills",
        icon: "category",
        title: "BASIC SKILLS",
        recommend: [
          {title: "Learn HTML", checked: false},
          {title: "Basics of CSS", checked: false}, 
          {title: "Basics of JavaScript", checked: false}
        ],
        optional: []
      },{
        id: "tools",
        icon: "build",
        title: "BASIC Tools",
        recommend: [
          {title: "Git - Version Contro", checked: false},
          {title: "BBasic Terminal Usage", checked: false}, 
          {title: "Text Editor", checked: false},
          {title: "Heart of Reserching", checked: false},
        ],
        optional: []
      }],
      myDetail: {}
    }
  },
  mounted(){
    // init 
    this.myDetail = this.basicData[0]
  },
  computed: {
    isBasic(){
      return this.clickList.findIndex(item => item == "basic") != -1
    }
  },
  methods: {
    addItem(e){
      this.clickList.push(e);
    },
    showDetail(data){
      this.myDetail = data;
    },
    addCheck(id, index){
      // this.showDetail(this.basicData.find(item => item.id == id))
      this.basicData.find(item => item.id == id).recommend[index].checked = true;
      this.myDetail = this.basicData.find(item => item.id == id);
      console.log('hi', this.myDetail)
      
    }
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
