# [extern"C"的作用是，实现类C和C++的混合编程。](https://github.com/Urchinzhou/Keep-ARTS/issues/18)



---

在C++源文件中的语句前面加上extern "C"，表明它按照类C的编译和连接规约来编译和连接，而不是C++的编译的连接规约。这样在类C的代码中就可以调用C++的函数or变量等。在这里所说的类C，代表的是跟C语言的编译和连接方式一致的所有语言。