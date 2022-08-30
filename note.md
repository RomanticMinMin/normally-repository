1.首页配置：
    注意点，所有页面的静态资源 都需要使用Thymeleaf接管
     所以使用 url: @{} 包含URL

2.页面国际化
    1):配置i18n文件：
      先建一个login.properties
      在建一个login_zh_CN.properties
      在建一个login_en_US.properties
     2):我们如果需要在项目中进行按钮自动切换，我们需要自定义一个组件LocaleResolver
     3):记得将自己写的组件配置到spring容器中 @Bean
     4):th:text="#{login.btn}"
 
3.登录功能实现
    1):

    2):犯了一个超级超级低级的错误，：password的参数不存在。
<label class="sr-only" name="password" th:text="#{login.password}">Password</label>
<input type="password" name="password" class="form-control" th:placeholder="#{login.password}" required="">
找了半天错误，最后都想呼自己~
    3): 拦截器实现

4.增删改查
    1): 员工管理实现：
    <nav class="col-md-2 d-none d-md-block bg-light sidebar" th:fragment="sidebar">
    <div th:insert="~{dashboard::sidebar}"></div>
    
    2):提取公共页面
        1.`th:fragment="sidebar"`
        2.`<div th:replace="~{commons/commons::sidebar(active='list.html')}"></div>`
        3.如果要传递参数，可以直接使用括号传参，接收判断即可
    3):列表循环展示，需要前端功底。

员工列表一直未出现部门的 原因： 竟然是 在Employee中将  这个 this.department = department;注释了
所有得到的是空值，甚至整个员工列表都不会显示！

5.添加员工
    1):按钮提交
    2):跳转到添加页面
    3):添加员工成功
    4):返回首页

6.CRUD 搞定
7.404

前端：
 - 模板：别人写好的，我们拿来改成自己需要的
 - 框架：组件，自己手动组合拼接  Bootstrap，Layui，semantic-ui，element-ui...
        栅格系统  分成多少列，对应上面的 12    12   16  24份
        导航栏
        侧边栏