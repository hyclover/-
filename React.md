1. react中的state和props

   state：组件内部的状态，可变属性，控制组件内部的状态；

   props：用于组件之间的通信，数据传递方式，不可变，从父组件流向子组件

2. 

   ```react
   class Square extends React.Component {
     render() {
       return (
         <button className="square">
           {this.props.value}
         </button>
       );
     }
   }
   
   class Board extends React.Component {
     renderSquare(i) {
       return <Square value={i} />;
     }
   ```

3. 用户定义的组件必须以大写字母开头，小写字母开头的元素代表一个HTML 内置组件。

4. 所有React组件必须像纯函数一样保护它们的props不被更改。

5. JSX列表渲染

   ```react
   bgData.map((item: any) => {
                           return (
                               <div>
                                   <img src={item.url} />
                               </div>
                           )
                       })
   ```

6. JSX条件渲染

   + 三元表达式
   + 逻辑&&运算

7. JSX样式控制

   + 行内样式：在元素身上绑定一个style属性即可
   + 类名样式：在元素身上绑定一个className属性即可

8. 组件

   函数组件

   + 组件名称须首字母大写
   + 函数组件须有返回值
   + 组件就像HTML标签一样可以被渲染到页面中，组件表示一段结构内容，对于函数组件来说，渲染的内容是函数的返回值就是对应的内容
   + 使用函数名称作为组件标签名称，可成对出现也可自闭合

   类组件

   + 类名称必须以大写字母开头
   + 类组件继承React.Component父类，从而使用父类提供的方法或属性
   + 类组件须提供render方法，render方法必须有返回值，表示该组件的UI结构

   ```react
   class HelloComponent extends React.Component {
       render(){
           return <div>this is class component</div>
       }
   }
   
   渲染
   <HelloComponent/>
   ```

9. 事件绑定

   * 语法  on+事件名称={事件处理程序}

      onClick={ () => {xxx} }

函数事件回调：

```react
function Form() {
  //e能阻止默认事件
  function handleSubmit(e) {
    e.preventDefault();    
    console.log('You clicked submit.');
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

类中事件函数回调：

```react
class LoggingButton extends React.Component {
  // This syntax ensures `this` is bound within handleClick. 标准写法，能确保this的指向 
    handleClick = () => {    console.log('this is:', this);  }; 
    render() {
    return (
      <button onClick={this.handleClick}>
        Click me
      </button>
    );
  }
}
```

在回调函数中传递

+ 自定义参数：{clickHandler} ->{() => clickHandler('自定义参数')}
+ 既需要e也需要额外的参数： {（e）=> clickHandler(e, '自定义参数')}

10. 组件状态

     ```react
     class TestComponent extends React.Component {
      //1.定义组件状态
         state = { name:'xx' } //这里可以定义各种属性，当前组件的状态
         //3.修改state中的状态name，必须通过方法setState
         changeName = () => {this.setState({name:'旭哥'})} //事件回调函数
         render () {
             return (
                 //2.使用状态
                 <div>
                     当前name为：{this.state.name}
                     <button onClick={this.changeName}>修改name</button>
                 </div>)
         }
     }
     ```

数组状态修改：state = {list：[1,2,3]}

​                         this.setState( {list: [...this.state.list, 4, 5] } )

对象修改：state = { obj：{name：‘xx’， age：xx } }

​                  this.setState({ obj: { ...this.state.person, name: 'xxx'}})

**在编写函数组件并需要向其添加state，可以使用hook。**

```react
import React, {useState} from 'react'
function TestComponent() {
    //声明state变量
    const [name, setName] = useState('xx'); //useState参数为初始state，返回值为当前state和更新state的函数
    return (
        //读取state
    	<div>
            当前name为:{name} 
            <button onClick={()=>setName('xxx')}>修改name</button>
        </div>
    )
}
```



11. react中import {}

    + 不使用{}：导入模块的js文件中采用默认导出export default语法，且import时命名随意
    + 使用{}：导入模块的js文件中采用命名方式导出，如export xx名字，import时模块命名有意义

    一个模块只能有一个默认导出，可以有人以命名导出。

12. 定义className时有多个花括号：className={\`title ${index === this.state.active ? 'active' : ''}\`}

13. 生成一个独一无二的id，uuid

    yarn add uuid

14. 组件通信：组件之间数据传递

    + 父子关系
    + 兄弟关系--自定义事件模式产生技术方法eventBus
    + 其他关系--mobx/redux/基于hook方案

15.  父传子实现

    父组件提供要传递的数据：定义state

    给子组件标签添加属性值为state中的数据

    子组件中通过props接收父组件中传过来的数据

    - 类组件使用this.props获取props对象
    - 函数式组件直接通过参数获取props对象

16. 

    

    

    

    

    