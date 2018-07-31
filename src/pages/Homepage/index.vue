<script>
export default {
  name: 'homepage',
  data(){
    return{
      clickList: ['basic'],
      checked: 0,
      myImg: [
        require('@/assets/img-ship-beginner.png'),
        require('@/assets/img-ship-developer.png'),
        require('@/assets/img-ship-master.png'),
        require('@/assets/img-ship-noob.png')
      ],
      basicData: [{
        category: 'basic',
        id: "skills",
        icon: "category",
        title: "BASIC SKILLS",
        done: false,
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
          done: false,
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
          done: false,
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
          done: false,
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
          done: false,
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
          done: false,
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
          done: true,
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
          done: true,
          recommend: [],
          optional: [{title: "jQuery", checked: false},]
        },{
          category: 'js',
          id: "draw",
          icon: "gradient",
          title: "WEB DRAWING",
          done: true,
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
          done: false,
          recommend: [
            {title: "ES6", checked: false}
          ],
          optional: []
        },{
          category: 'js',
          id: "jsframework",
          icon: "developer_mode",
          title: "JAVASCRIPT FRAMEWORK",
          done: false,
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
          done: true,
          recommend: [],
          optional: [
            {title: "TypeScript", checked: false},
            {title: "Babel", checked: false},
            {title: "CoffeeScript", checked: false}
          ]
        },{
          category: 'manager',
          id: "npm",
          icon: "device_hub",
          title: "PACKAGE MANAGERS",
          done: false,
          recommend: [
            {title: "NPM", checked: false},
            {title: "YARN", checked: false}
          ],
          optional: [{title: "Bower", checked: false}]
        },{
          category: 'manager',
          id: "task",
          icon: "import_contacts",
          title: "TASK RUNNERS",
          done: false,
          recommend: [
            {title: "npm scripts", checked: false},
            {title: "gulp", checked: false}
          ],
          optional: [{title: "grunt", checked: false}]
        },{
          category: 'manager',
          id: "buildtools",
          icon: "table_chart",
          title: "BUILD TOOLS",
          done: false,
          recommend: [
            {title: "Webpack", checked: false}
          ],
          optional: [{title: "Parcel", checked: false}]
        }],
      myDetail: {},
      nowTxt: 0,
      clickBtnIndex: false
    }
  },
  mounted(){
    // init 
    this.myDetail = this.basicData[0]
  },
  computed: {
    nowImg(){
      if(this.isCategory('manager')){
        this.nowTxt = 3
        return this.myImg[3]
      }else if(this.isCategory('js')){
        this.nowTxt = 2
        return this.myImg[2]
      }else if(this.isCategory('css')){
        this.nowTxt = 1
        return this.myImg[1]
      }else{
        this.nowTxt = 0
        return this.myImg[0]
      }
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
       return this.basicData.filter(item => item.category == "manager")
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
    addCheck(id, index, subCategory){
      // let btn is active
      this.clickBtnIndex = !this.clickBtnIndex;

      // change basicData property done and recommend checked
      let goal = this.basicData.find(item => item.id == id);
      if(subCategory=='recommend'){
        goal.recommend[index].checked = true;      
        goal.done = goal.recommend.every(i => i.checked===true)
      }else if(subCategory=='optional'){
        goal.optional[index].checked = true;     
      }
      

      // can click next level
      if(this.basicLists.every(i => i.done==true)){
        this.clickList.push('css')
      }
      if(this.cssLists.every(i => i.done==true)){
        this.clickList.push('js')
      }
      if(this.jsLists.every(i => i.done==true)){
        this.clickList.push('manager')
      }
    },
    checkedLength(list){
        return list.filter(item => item.checked == true).length
    }
    
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
