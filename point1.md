##1实例化
### 1 代码中我们经常遇到 是不是要在构造方法中实例化 类的操作，以往我们都是一股脑,这种做法

 class test{
     public function __construct(){
         $this->abc=new ABC();
     }
 }
 如果好一点，我们可以使用
###2 class test{
     public function __construct(){
         
     }
     public function getAbc(){
         if(isset($this->abc)){
             $this->abc = new ABC();
         }
         return $this->abc
     }
 }
 这种方式，可以减少实例化过程中不必要的连接，这就是再代码运行过程中进行的延迟实例化 不过调用的时候，需要使用$this->getAbc();这种方式

### php 其他的方法进行这种操作(闭包函数)

<?php
class ABC{
    public function __construct(){
        echo 1231;
    }
    public function test(){
        echo 456;
    }
}
$obj = function(){
    return new ABC();
};
var_dum($obj);//此时var_dump() 不执行不会走构造函数
$obj()->test();
