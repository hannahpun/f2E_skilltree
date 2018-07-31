<script>
export default {
  name: 'homepage',
  data(){
    return{
      clickList: ['basic'],
      checked: 0,
      basicData: [{
        category: 'basic',
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
        category: 'basic',
        id: "tools",
        icon: "build",
        title: "BASIC Tools",
        recommend: [
          {title: "Git - Version Contro", checked: false},
          {title: "Basic Terminal Usage", checked: false}, 
          {title: "Text Editor", checked: false},
          {title: "Heart of Reserching", checked: false},
        ],
        optional: []
      },{
        category: 'css',
        id: "framework",
        icon: "flip_to_front",
        title: "CSS FRAMEWORK",
        recommend: [
          {title: "Bootstrap", checked: false}
        ],
        optional: [
            {title: "UIKit", checked: false},
            {title: "Foundation", checked: false},
            {title: "Semantic UI", checked: false}
        ]
      },{
        category: 'css',
        id: "prepro",
        icon: "view_quilt",
        title: "CSS PREPROCESSORS",
        recommend: [
          {title: "Sass", checked: false},
          {title: "PostCSS", checked: false}
        ],
        optional: [
          {title: "Less", checked: false},
          {title: "Stylus", checked: false}
        ]
      },{
        category: '',
        id: "",
        icon: "",
        title: "",
        recommend: [
          {title: "", checked: false},
          {title: "", checked: false}
        ],
        optional: []
      },{
        category: '',
        id: "",
        icon: "",
        title: "",
        recommend: [
          {title: "", checked: false},
          {title: "", checked: false}
        ],
        optional: []
      },{
        category: '',
        id: "",
        icon: "",
        title: "",
        recommend: [
          {title: "", checked: false},
          {title: "", checked: false}
        ],
        optional: []
      }],
      myDetail: {},
      clickBtnIndex: false
    }
  },
  mounted(){
    // init 
    this.myDetail = this.basicData[0]
  },
  computed: {
    isBasic(){
      return this.clickList.findIndex(item => item == "basic") != -1
    },
    basicLists(){
        return this.basicData.filter(item => item.category == "basic")
    },
    cssLists(){
       return this.basicData.filter(item => item.category == "css")
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
        this.clickBtnIndex = !this.clickBtnIndex
      this.basicData.find(item => item.id == id).recommend[index].checked = true;      
    },
    checkedLength(list){
        return list.filter(item => item.checked == true).length
    }
    
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
