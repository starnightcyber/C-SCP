# C-SCP
C Secure Coding Practices

分节参考：[C安全编码标准](https://github.com/starnightcyber/C-SCP/wiki/C%E5%AE%89%E5%85%A8%E7%BC%96%E7%A0%81%E6%A0%87%E5%87%86)


欢迎来到《C安全编码标准》。

## 概述
 
本部分的内容源自《C安全编码标准》，方便个人参考使用。

书中的指导方针分为规则和建议两种。

### 规则

如果满足以下条件，就会被定义为规则：
* 违反编码实践有可能导致安全缺陷，产生可被利用的潜在风险。
* 违反这种编码实践仍然可以保证正确行为的情况是屈指可数的。
* 可以通过自动分析、形式方法或手工检查技巧检查是否遵循编码标准。

要保证C编程语言所开发的软件系统的安全性，实现本标准所定义的安全编码规则是必须的（但并不充分）。

### 建议

如果满足以下条件，就定义为建议：
* 应用这种编码实践可能会提到系统的安全性。
* 由于未满足一个或多个编码实践的要求，而不能定义为规则。

特定的开发实践所采纳的建议数量取决于最终的软件产品的安全需求。具有很高安全需求的项目可能会重视安全方面的资源，因此所采纳的建议可能更多。

## 预处理器（PRE）
### 建议
* PRE00. 用内联函数或静态函数代替与函数相似的宏。
* PRE01. 在宏参数名两边加上括号。
* PRE02. 宏替换列表应该加上括号。
* PRE03. 应该使用typedef定义编码类型。
* PRE04. 不要复用标准头文件名。
* PRE05. 连接标记或执行字符串化时宏替换。
* PRE06. 把文件放在包含防护条件中。
* PRE07. 避免使用连续的问号。
* PRE08. 保证头文件名唯一。
* PRE09. 不要用不安全的函数替换安全函数。
* PRE10. 在一个do-while循环中包装多条语句的宏。

### 规则
* PRE30. 不要通过连接创建统一字符名称。
* PRE31. 不要在不安全宏的参数中包含赋值、增值、减值、volatile访问或函数调用。

## 声明和初始化（DCL）
### 建议
* DCL00. 用const限定不可修改的对象。
* DCL01. 不要在子作用域中复用变量名。
* DCL02. 使用视觉区别明显的标识符。
* DCL03. 使用静态断言测试常量表达式的值。
* DCL04. 不要在一个声明中声明超过一个变量。
* DCL05. 使用typedef声明提高代码的可读性。
* DCL06. 使用有意义的符号常量表示程序逻辑中的字面值。
* DCL07. 在函数声明器中包含适当的类型信息。
* DCL08. 在常量定义中对关系进行正确的编码。
* DCL09. 把返回errno错误代码的函数的返回类型声明为errno_t。
* DCL10. 维护变参函数的编写者和调用者之间的契约。
* DCL11. 理解与变参函数相关联的类型问题。
* DCL12. 使用不透明类型实现抽象数据类型。
* DCL13. 把不会被函数修改的值指针参数声明为const。
* DCL14. 不要对跨翻译单元的全局变量的初始化顺序作出假设。
* DCL15. 把不需要外部链接的对象声明为static。
### 规则
* DCL30. 声明具有正确存储持久期的对象。
* DCL31. 在使用标识符之前声明他们。
* DCL32. 保证相互可见的标识符是唯一的。
* DCL33. 保证函数实参中具有限制性限定的源指针和目标指针不引用重叠的对象。
* DCL34. 对无法缓存的数据使用volatile。 
* DCL35. 不要使用与函数定义不匹配的类型转换函数。
* DCL36. 不要声明具有冲突链接属性的标识符。

## 表达式（EXP）
### 建议
* EXP00. 使用括号保证操作的优先级。
* EXP01. 不要用指针的长度确定它所指类型的长度。
* EXP02. 注意逻辑AND和OR操作符的短路行为。
* EXP03. 不要认为结构的长度等于它的各个成员的长度之和。
* EXP04. 不要在结构之间执行逐字节的比较。
* EXP05. 不要转换掉const限定。
* EXP06.  sizeof操作符的操作数不应该包含副作用。
* EXP07. 不要在表达式中对常量的值做出假设而削弱常量的优点。
* EXP08. 确保正确地使用指针运算。
* EXP09. 使用sizeof确定类型或变量的长度。
* EXP10. 不要依赖子表达式的求值顺序或副作用的发生顺序。
* EXP11. 不要把期待一种类型的操作符应用于一种不兼容的类型。
* EXP12. 不要忽略函数的返回值。
### 规则
* EXP30. 不要依赖序列点之间的求值顺序。
* EXP31. 避免断言的副作用。
* EXP32. 不要转换掉volatile限定。
* EXP33. 不要引用未初始化的内存。
* EXP34. 保证不对null指针进行解引用。
* EXP35. 不要在后续的序列点之后访问或修改一个函数的调用结果中的数组。
* EXP36. 不要把指针转换为对齐要求更严格的指针类型。
* EXP37. 调用函数时使用API所指定的参数。

## 整数（INT）
### 建议
* INT00. 理解编译器所使用的数据模型。
* INT01. 使用rsize_t或size_t类型表示所有对象长度的整数值。
* INT02. 理解整数转换规则。
* INT03. 使用安全的整数库。
* INT04. 对来自不信任来源的整数值实行限制。
* INT05. 如果输入函数无法处理所有可能出现的错误，就不要用它们转换字符数据。
* INT06. 使用strtol()或相关函数把字符串标记转换为整数。
* INT07. 只使用显式的有符号或无符号char类型表示数值。
* INT08. 验证所有的整数值位于范围内。
* INT09. 保证枚举常量映射到唯一的值。
* INT10. 使用%操作符时不要假设余数总是正的。
* INT11. 把指针转换为整数或者把整数转换为指针时需要小心。
* INT12. 当普通的整数位段用于表达式时，不要对它的类型做出假设。
* INT13. 只对无符号操作数使用位操作符。
* INT14. 避免在同一个数据上执行位操作和算术运算。
* INT15. 在程序员定义的整数类型的格式化IO中使用intmax_t或者uintmax_t。
### 规则
* INT30. 保证无符号整数运算不产生回绕。
* INT31. 保证整型转换不会丢失或错误解释数据。
* INT32. 保证有符号整数运算不会产生溢出。
* INT33. 保证除法和求模运算不会导致除零错误。
* INT34. 移位的数量不能是负数或大于操作数的位数。
* INT35. 把整型表达式比较或赋值为一种较大类型之前用这种较大类型对它进行求值。

## 浮点数（FCP）
### 建议
* FLP00. 理解浮点数的限制。
* FLP01. 在重新排列浮点表达式时需要注意。
* FLP02. 需要精确计算时避免使用浮点数。
* FLP03. 检测和处理浮点错误。
### 规则
* FLP30. 不要使用浮点数作为循环计数器。
* FLP31. 不要用复数调用期望接受实数的函数。
* FLP32. 防止或检测数学函数中的定义域错误和值域错误。
* FLP33. 执行浮点运算时把整数转换为浮点数。
* FLP34. 保证浮点数转换位于新类型的范围之内。

## 数组（ARR）
### 建议
* ARR00. 理解数组的工作方式。
* ARR01. 获取数组的长度时不要对指针应用sizeof操作符。
* ARR02. 显示地指定数组的边界，即使它已经由初始化值列表隐式地指定。
### 规则
* ARR30. 保证数组索引位于合法的范围之内。
* ARR31. 在所有源文件中使用一致的数组记法。
* ARR32. 保证变长数组的长度参数位于合法范围之内。
* ARR33. 保证复制的目标具有足够的存储空间。
* ARR34. 保证表达式中的数组类型是兼容的。
* ARR35. 不允许循环迭代到数组尾部之后。
* ARR36. 不要对两个并不指向同一个数组的指针进行相减或比较。
* ARR37. 不要把一个指向非数组对象的指针加上或减去一个整数。
* ARR38. 如果结果值并不引用合法的数组元素，不要把指针加上或减去一个整数。

## 字符和字符串（STR）
### 建议
* STR00. 使用适合的类型表示字符。
* STR01. 采纳和实现一致的字符串管理计划。
* STR02. 对传递给复杂子系统的字符串数据进行净化。
* STR03. 不要意外地阶段null结尾的字节字符串。
* STR04. 使用普通char类型表示基本字符集中的字符。
* STR05. 引用字符串常量时使用const指针。
* STR06. 不要以为strtok()会使解析的字符串不被修改。
* STR07. 使用托管字符串开发新的字符串操纵代码。
### 规则
* STR30. 不要试图修改字符串常量。
* STR31. 保证字符串的储存具有足够的空间容纳字符数据和null结尾符。
* STR32. 根据需要将字符串用null结尾。
* STR33. 正确地判断宽字符串的长度。
* STR34. 在转换为更大的整型长度时把字符转换为无符号类型。
* STR35. 不要把未检查边界来源的数据复制到固定长度的数组。
* STR36. 不要指定用字符串常量初始化的字符数组
* STR37. 字符处理函数的参数必须能够用unsigned char表示。

## 内存管理（MEM）
### 建议
* MEM00. 在同一个模块、同一个抽象层中分配和释放内存。
* MEM01. 在free()之后立即在指针中存储一个新值。
* MEM02. 把内存分配函数的调用结果立即转换为指向被分配类型的指针。
* MEM03. 及时清除存储在可复用资源中的敏感信息。
* MEM04. 不要执行零长度的分配。
* MEM05. 避免大型的堆栈分配。
* MEM06. 保证敏感数据不会写入到磁盘。
* MEM07. 保证calloc()的参数相乘后可以用size_t表示。
* MEM08. 只把realloc()用于改变动态分配数组的大小。
* MEM09. 不要假设内存分配函数会对内存进行初始化。
* MEM10. 定义和使用指针验证函数。
### 规则
* MEM30. 不要访问已释放的内存。
* MEM31. 动态分配的内存只应释放一次。
* MEM32. 检测和处理内存分配错误。
* MEM33. 使用正确的语法表示灵活数组成员。
* MEM34. 只释放动态分配的内存。
* MEM35. 为对象分配足够的内存。

## 输入/输出（FIO）
### 建议
* FIO00. 在创建格式字符串时应该小心。
* FIO01. 调用通过文件名标识文件的函数时必须小心。
* FIO02. 对来自不信任来源的路径名进行标准化。
* FIO03. 不要对fopen()和文件的创建做出假设。
* FIO04. 检测和处理输入和输出错误。
* FIO05. 使用多个文件属性标识文件。
* FIO05. 创建具有正确访问权限的文件。
* FIO07. 用fseek()代替rewind()。
* FIO08. 在打开的文件上调用remove()时应该小心。
* FIO09. 跨系统传输二进制数据时应该小心。
* FIO10. 使用rename()函数时应该小心。
* FIO11. 指定fopen()的mode参数时应该小心。
* FIO12. 使用setvbuf()代替setbuf()。
* FIO13. 不要压回多余1个的字符。
* FIO14. 理解文件流的文本模式和二进制模式的区别。
* FIO15. 保证文件操作在安全目录中执行。
* FIO16. 通过创建jail限制对文件的访问。
### 规则
* FIO30. 排除格式字符串中的用户输入。
* FIO31. 不要打开已经被打开的文件。
* FIO32. 不要在专用于文件的设备上执行操作。
* FIO33. 检测和处理导致未定义行为的输入输出错误。
* FIO34. 使用int捕捉字符I/O函数的返回值。
* FIO35. 当sizeof(int)==sizeof(char)时，使用feof()和ferror()检测文件尾和文件错误。
* FIO36. 不要假设fgets()会读取换行符。
* FIO37. 不要假设被读取的是字符数据。
* FIO38. 不要使用FILE对象的拷贝进行输入和输出。
* FIO39. 不要在没有干预刷新或定位调用的情况下，在一个流中交替地执行输入和输出。
* FIO40. 在fgets()失败时重置字符串。
* FIO41. 调用getc()或putc()时不要使用具有副作用的流参数。
* FIO42. 保证当文件不再需要时及时将它们关闭。
* FIO43. 不要在共享目录中创建临时文件。
* FIO44. 只在fsetpos()中使用fgetpos()所返回的值。

## 环境（ENV）
### 建议
* ENV00. 不要存储指向getenv()返回的字符串的指针。
* ENV01. 不要对环境变量的长度做出假设。
* ENV02. 注意具有相同的有效名称的多个环境变量。
* ENV03. 调用外部程序时对环境进行净化。
* ENV04. 如果不需要命令处理器就不要调用system()。
### 规则
* ENV30. 不要修改getenv()返回的字符串。
* ENV31. 在可能无效化环境指针的操作之后不能再依赖它。
* ENV32. 所有的atexit处理函数都不能以除了正常返回之外的其它任何方式终止。

## 信号（SIG）
### 建议
* SIG00. 屏蔽由不可中断的信号处理函数处理的信号。
* SIG01. 理解与信号处理函数的持久性有关的平台特定的细节。
* SIG02. 避免使用信号实现常规的功能。
### 规则
* SIG30. 只在信号处理函数中调用异步安全的函数。
* SIG31. 不要访问和修改信号处理函数中的共享对象。
* SIG32. 不要在信号处理函数中调用longjmp()。
* SIG33. 不要递归地低啊用raise()函数。
* SIG34. 不要在不可中断的信号处理函数内部调用signal()。

## 错误处理（ERR）
### 建议
* ERRO00. 采用和实现一致的、全面的错误处理策略。
* ERRO01. 使用ferror()而不是errno检查FILE流错误。
* ERRO02. 避免带内错误提示符。
* ERRO03. 调用TR24731-1所定义的函数时使用运行时约束处理函数。
* ERRO04. 选择一种适当的终止策略。
* ERRO05. 独立于应用程序的代码应该在不提示错误处理的情况下提供错误检测。
* ERRO06. 理解assert()和abort()的终止行为。
### 规则
* ERRO30. 调用设置errno的库函数之前把errno设置为0，并且在函数返回一个提示失败的值之后检查errno。
* ERRO31. 不要重定义errno。
* ERRO32. 不要依赖errno的不确定值。

## 其它（MSC）
### 建议
* MSC00. 在高警告级别进行干净的编译。
* MSC01. 实现逻辑完整性。
* MSC02. 避免因为省略所导致的错误。
* MSC03. 避免因为多余所导致的错误。
* MSC04. 用一种可读的风格，一致地使用注释。
* MSC05. 不要直接维护time_t类型的值。
* MSC06. 处理敏感数据时注意编译器的优化。
* MSC07. 检测和删除死代码。
* MSC08. 库函数应该对形参进行验证。
* MSC09. 字符编码：使用ASCII的子集以保证安全。
* MSC10. 字符编码：UTF-8相关的问题。
* MSC11. 使用断言进行诊断测试。
* MSC12. 检测和删除没有效果的代码。
* MSC13. 检测和删除未使用的值。
* MSC14. 不要引入不必要的平台依赖性。
* MSC15. 不要依赖未定义的行为。
### 规则
* MSC30. 不要使用rand()函数产生伪随机数。
* MSC31. 保证返回值与适当的类型进行比较。

## POSIX（POS）
### 建议
* POS00. 避免多线程的竞争条件。
* POS01. 检查链接是否存在。
* POS02. 遵循最小权限原则。
### 规则
* POS30. 正确地使用readlink()函数。
* POS31. 不要解锁或销毁另一个线程的mutext。
* POS32. 在多线程环境中使用位段时包含一个mutex。
* POS33. 不要使用vfork。
* POS34. 不要用一个指向自动变量的指针为参数调用putenv()。
* POS35. 避免检查符号链接是否存在时的竞争条件。
* POS36. 在撤销特权时注意正确的撤销顺序。
* POS37. 保证特权的撤销是成功的。


