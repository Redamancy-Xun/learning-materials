> # C++ STL库
> 
> 声明：并未完成，且99%会有理解错误，请见谅，欢迎指正。目前更新至容器（vector、deque、list） 
> 
> ### 前言（整体理解）
> 
> 其实从STL库的名称上就可以看出来，STL全称为：Standard Template Library，翻译过来就是：标准模版库。提取一下关键的两个字：模版，什么叫模版呢，应用范围广、可以直接套用的就是模版。我认为STL库的存在是C++和C最大的区别之一，也是最大的优点之一。举个简单的例子，STL库里主要包含了容器（Containers）、算法（Algorithms）、迭代器（iterators）等等，以算法为例，当我们引用<algorithm>头文件中的sort函数时，可以对数据进行排序，而在c语言中实现这样一个排序（例如冒泡排序），我们需要多次循环遍历数组，还要自定义一个swap函数用来进行交换，使用stl就省去了这样一个教程。用stl就相当于站在巨人的肩膀上，我们不用探究这些函数、还有容器等等是如何实现的，只需要掌握用法就行了，学会stl是可以大大节省编程时间的，也可以降低编程的复杂度。
> 
> ## 1、容器
> 
> ### 1.1 vector
> 
> ##### 概念理解：
> 
> 说白了就是一个动态数组（但是不只可以存储数字）
> 
> 对于动态的理解：在程序运行的时候可以动态地插入和删除元素，正常的数组需要在使用前声明长度，进行内存的分配，但是vector对于内存的分配是自动的，可以根据需求动态增长和缩小
> 
> ##### 优点
> 
> 自动分配内存，不需要在开始编写程序的时候就考虑要将数组长度定义为多少（懒人学vector之前都往大了定义，学完之后直接用vector了）
> 
> 头文件里包含了各种各样vector有关的函数，可以灵活进行元素的插入、删除、清空以及获取大小等操作
> 
> ##### 缺点
> 
> 会造成内存的浪费（这个很好理解，vector会像我这个懒人一样，通常会分配大于实际需求的内存）
> 
> 有的时候时间复杂度较大，就比如说要在vector的头部插入一个元素，这个时候时间复杂度就远不如deque
> 
> 在数据大小超出原先分配的内存块时，会有一个寻找新的内存块，并将原内存块中所有数据拷贝到新内存块中的操作。
> 
> ##### 使用（前面都是废话，便于加深理解而已，会用就行）
> 
> 需要引用<vector>头文件
> 
> ###### 创建vector与初始化：
> 
> 在using namespace std；之后，直接：
> 
>             vector<int> vec1;                          // 创建空的vector，名称为vec1
>             vector<int> vec2(5);                      // 创建长度为5的vector，元素全部初始化为0
>             vector<int> vec3(5, 10);                // 创建长度为5的vector，元素全部为10
>             vector<int> vec4 = {1, 2, 3, 4};      // 创建vector，元素为1、2、3、4
> 
> ###### 赋值操作
> 
>             vec1.assign(arr, arr + 5);            //将一个数组arr中的第1-5个元素赋值给一个名为vec1的vector
> 
>                                                                 （为什么是arr+5而不是arr+4——因为assign后面的（arr，arr+5）是一个左闭右开的区间）
> 
>             vec2=vec1                                    //将vec1中的所有数据赋值给vec2
> 
>             vec3.assign（5，10）                //功能与初始化中提到的 vector<int> vec3(5, 10);类似，但现在这个是将5个10赋值给本身，
> 
>                                                                   并没有规定vec3的长度
> 
>             vec4.swap（vec5）                    //将vec4和vec5中的元素进行互换
> 
> ###### 关于大小的函数
> 
>             vec1.size（）                    //返回值是vec1中的元素个数
> 
>             vec2.empty（）               //判断vec2是否为空，空则返回1，不为空则返回0
> 
>             m=vec3.max_size();        //此时m等于vec3所能容纳元素数量的最大值，一般是非常大的，我试了一下，返回值是2305843009213693951
> 
> ###### 元素的插入、删除、访问、清空
> 
>             vec1.push_back(10);                                       //在vec1的末尾添加元素10
> 
>             vec1.insert(vec2.begin() + 3, 5) ；                //将5这个元素插入到vec1中索引为3的位置（第四个元素）
> 
>                                                                                        （vec2.begin是vec2中的第一个元素）
> 
>             vec1.insert(vec2.begin() + 3, 5)；               //在vec1中索引为3的位置插入10个5
> 
>             n=vec2[0]；                                                  //将vec2中的第一个元素赋值给n（与数组类似，可以在[]中输入下标来访问元素）
> 
>             m=vec2.at(1);                                               //将vec2中的第一个元素赋值给m
> 
>             vec3.erase(vec1.begin() + 3);                     //删除vec3中的第四个元素
> 
>             vec3.pop_back();                                         //移除vec3中的最后一个元素
> 
>             vec4.clear();                                                  //清空vec4


