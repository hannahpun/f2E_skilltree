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
        category: 'css',
        id: "architechture",
        icon: "developer_board",
        title: "CSS ARCHITECHTURE",
        recommend: [
          {title: "OOCSS", checked: false}
        ],
        optional: [
            {title: "SMACSS", checked: false},
            {title: "BEM", checked: false}
        ]
      },{
        category: 'css',
        id: "cssSkill",
        icon: "devices",
        title: "CSS SKILLS",
        recommend: [
          {title: "Responsive", checked: false},
          {title: "Flexbox", checked: false}
        ],
        optional: []
      },{
        category: 'css',
        id: "mastery",
        icon: "widgets",
        title: "CSS MASTERY",
        recommend: [],
        optional: [
          {title: "Grid Layout", checked: false},
          {title: "Animation", checked: false},
          {title: "Transform 2D, 3D", checked: false}
        ]
      },{
        category: 'js',
        id: "dom",
        icon: "hdr_strong",
        title: "BASIC DOM",
        recommend: [],
        optional: [{title: "jQuery", checked: false},]
      },{
        category: 'js',
        id: "draw",
        icon: "gradient",
        title: "WEB DRAWING",
        recommend: [],
        optional: [
          {title: "SVG", checked: false},
          {title: "Canvas", checked: false},
          {title: "D3.js", checked: false}
        ]
      },{
        category: 'js',
        id: "es6",
        icon: "format_quote",
        title: "JAVASCRIPT SKILLS",
        recommend: [
          {title: "ES6", checked: false}
        ],
        optional: []
      },{
        category: 'js',
        id: "jsframework",
        icon: "developer_mode",
        title: "JAVASCRIPT FRAMEWORK",
        recommend: [
          {title: "Vue.js", checked: false},
          {title: "Angular", checked: false},
          {title: "React.js", checked: false}
        ],
        optional: []
      },{
        category: 'js',
        id: "jsprepro",
        icon: "nfc",
        title: "JAVASCRIPT PREPROCESSORS",
        recommend: [],
        optional: [
          {title: "TypeScript", checked: false},
          {title: "Babel", checked: false},
          {title: "CoffeeScript", checked: false}
        ]
      },{
        category: 'maneger',
        id: "npm",
        icon: "device_hub",
        title: "PACKAGE MANAGERS",
        recommend: [
          {title: "NPM", checked: false},
          {title: "YARN", checked: false}
        ],
        optional: [{title: "Bower", checked: false}]
      },{
        category: 'maneger',
        id: "task",
        icon: "import_contacts",
        title: "TASK RUNNERS",
        recommend: [
          {title: "npm scripts", checked: false},
          {title: "gulp", checked: false}
        ],
        optional: [{title: "grunt", checked: false}]
      },{
        category: 'maneger',
        id: "buildtools",
        icon: "table_chart",
        title: "BUILD TOOLS",
        recommend: [
          {title: "Webpack", checked: false}
        ],
        optional: [{title: "Parcel", checked: false}]
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
    },
    jsLists(){
       return this.basicData.filter(item => item.category == "js")
    },
    managerLists(){
       return this.basicData.filter(item => item.category == "maneger")
    }
   
  },
  methods: {
    isCategory(category){
        return this.clickList.findIndex(item => item == category) != -1
    },
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
