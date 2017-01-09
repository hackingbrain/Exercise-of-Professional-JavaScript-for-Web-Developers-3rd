# 第二章 在HTML中使用JavaScript

## 1. &lt;script>元素
  1. 简介&lt;script>定义的6个属性？    
    答：async, charset, defer, language, src, type
    * async: 可选，表示以异步的方式立即下载该脚本
    * charse: 可选，表示该脚本的字符集。大多浏览器会忽略该值，因此该属性很少被使用
    * defer: 可选，表示该脚本可延迟至文档被完全解析和显示后再执行
    * language: 已废弃，无使用必要
    * src: 可选，表示包含要执行代码的外部文件
    * type: 可选，表示代码使用的脚本语言的内容类型，及MIME类型，默认为text/javascript    
    
  2. 使用&lt;srcipt>引入外部脚本的写法是？    
    答：可以写成&lt;script src=”...”>&lt;/script>或&lt;script src=”...” />, 但需要注意的是不能在HTML文档中使用第二种写法(XHTML中可以)。因为该种语法不符合HTML规范，且某些浏览器无法正确解析(比如IE)。
    
    ### 1.1. 标签的位置      
    &lt;script>元素一般放在页面元素中的哪个位置?  
    答: 传统的做法为将所有&lt;script>元素房子页面的&lt;head>元素中，这种方式主要目的为__将所有外部文件引用均置与同一位置，便于管理__。而浏览器在解析至&lt;body>标签后才开始呈现内容，当浏览器解析head时，若&lt;script>等外部文件均置于head中，浏览器会将__head中所有外部文件下载完成后__才开始解析body，会导致延迟。  
    因此，现代的web一般均把JS引用放在&lt;script>元素中页面内容的后面，这样在解析JS前便可将页面内容展现在浏览器，提升用户体验。  
    
    ### 1.2. 延迟脚本
    defer属性的用途是？  
    答: 表明脚本在执行时不会影响页面构造，即脚本会被延迟至整个页面都解析完毕后在运行。HTML5规范要求脚本按照它们出现的先后顺序执行，因此第一个延迟脚本会先于第二个延迟脚本执行，且两个脚本先于DOMContentLoaded事件触发。__但是__，在现实当中，延迟脚本__不一定会按照顺序执行__，也__无法保证__会在DOMContentLoaded事件之前执行。因此最好只包含一个延迟脚本。  
    
    ### 1.3. 异步脚本
    async属性的用途是？  
    答: 类似与defer，标记为async的脚本不保证按指定它们的先后顺序执行，一定会在页面的load事件前执行，但不能确定执行时机是在DOMContentLoaded之前还是之后。
    
## 2. 文档模式  
  文档模式的种类及区别?  
  答：IE5.5引入了文档模式的概念，通过使用__文档类型(doctype)__切换实现。最初的两种模式为__混杂模式__和__标准模式__。混杂模式让IE的行为与IE5相同，标准模式让IE的行为更接近标准行为。  
  IE引入文档模式的概念后，其他浏览器也纷纷效仿。当浏览器在文档开始出__没有__发现文档类型声明时，所有浏览器都会__默认开启混杂模式__。  

## 3. &lt;noscript>元素
  &lt;noscript>元素的用途是？  
  答：当浏览器不支持脚本或浏览器支持脚本但脚本被禁用时，浏览器显示&lt;noscript>元素中的内容
  
  
  