# UnityHideCodeWithDLL
HideCodeWithDLL other can not see the code except decompiler suc
# **Untiy类库构建代替代码**

## Visual Studio构建类库给Unity用:

1. **创建类库项目，此处暂时没找到一次项目创建多个dll文件的方法，即类似Unity中AssemblyDefinitionFile的自定义程序集功能。**
 
      ![image](https://user-images.githubusercontent.com/64005736/174807004-2843944d-0efe-47db-9188-4aa02b4e0ed3.png)

   ​												图1-1

2. **注意命名方式，生成的动态链接库会以改名字生成，注意这里的命名不同于命名空间，这里是程序集命名。**
![image](https://user-images.githubusercontent.com/64005736/174807099-2c2b3b47-7208-4426-8273-d02efa505ef7.png)

   ​												图1-2

3. **创建之后的会进入第一个类文件Class1，这里已经将命名空间改为项目的名称。**
![image](https://user-images.githubusercontent.com/64005736/174807121-d539e692-c545-4836-93eb-ab7b314d2079.png)

   ​												图1-3

4. **添加依赖项(添加Unity相关类库的依赖)，在项目下拉框下，点击添加项目引用，会弹出一个浏览文件窗口，再定位到你电脑中Unity的类库的位置，如图1-5所示。**

    ![image](https://user-images.githubusercontent.com/64005736/174807143-ad634fd7-9550-4961-a584-9c92bc8a01b8.png)
    
    图1-4

    ![image](https://user-images.githubusercontent.com/64005736/174807149-8db137e4-7f8f-4d1a-a1c8-2a6afb4926f7.png)

    图1-5

5. **添加了依赖项之后就可以开始编写Mono脚本，添加UnityEngine的引用，撰写脚本，如图1-6。**

![image](https://user-images.githubusercontent.com/64005736/174807187-dd79b3e6-789b-4f02-be63-5be162644f47.png)

​												图1-6

6. **生成解决方案，步骤为下图1-7，结果为图1-8。**

![image](https://user-images.githubusercontent.com/64005736/174807219-ccfb9f6c-f514-4856-94fd-ff92b0d7ab67.png)

​												图1-7

![image](https://user-images.githubusercontent.com/64005736/174807235-e80177fa-e7cf-4260-9293-b78edc4f34fc.png)
​												图1-8

![image](https://user-images.githubusercontent.com/64005736/174807755-22177f96-e3a7-4ad9-8347-5583a00e9479.png)

​												图1-9

7. **使用类库中的相关类。**

![image](https://user-images.githubusercontent.com/64005736/174807792-57428abc-0377-4b0c-b812-2099614ff91a.png)

​					图1-10
![image](https://user-images.githubusercontent.com/64005736/174807805-26f67161-76b2-4444-88ba-d4206c350653.png)

​												                            图1-11

8. **Inspector面板和运行结果。**
![image](https://user-images.githubusercontent.com/64005736/174807836-5609fb21-484a-4e83-a094-570f07b0d12e.png)

​										图1-12
![image](https://user-images.githubusercontent.com/64005736/174807867-5fdf1321-79d7-4479-bdc7-726a67376ed5.png)

​												图1-13


## 在Unity项目中直接找到对应的类库使用：

1. **构建相关的AssemblyDefinationFile文件控制相关的代码，我的文件结构如下：**

 
![image](https://user-images.githubusercontent.com/64005736/174808321-2049d4ba-c830-4a63-a77e-acf53e3ee96a.png)

​												图2-1

 

2. **在Unity项目中找到对应的DLL文件，将其拖入Unity中。**


![image](https://user-images.githubusercontent.com/64005736/174808349-32565b62-c658-4b89-bc38-b5524d42833d.png)

​												图2-2

 

3. **拖入项目后，还不能将DLL文件中的Mono脚本挂在场景中的GameObject上，此时要将源码和ADF文件删除。**

 

![image](https://user-images.githubusercontent.com/64005736/174808381-c227037f-7959-4667-94c7-5bc5a5f1b71e.png)

​									图2-3

4. **将Mono脚本挂载在相关的脚本上。**

![image](https://user-images.githubusercontent.com/64005736/174808397-b880ffa9-2fdf-472f-8cbf-05f866878a87.png)

​																	图2-4

![image](https://user-images.githubusercontent.com/64005736/174808417-eb9ca9fc-00f9-4b72-9863-4c27268a3862.png)

​										图2-5

5. **运行游戏打印结果**

![image](https://user-images.githubusercontent.com/64005736/174808432-d668b0ee-08e4-469e-a39c-74bea1d80f3b.png)

​									图2-6

## 总结：

**1.经过推敲，如果是项目代码需要隐藏，可实施性不大，因为代码在不停的修改，不停的生成最新的DLL文件，即使是使用Unity自带的目前最新的Roslyn Compiler，直接将新生成的DLL文件放入工程以DLL的形式跑代码（上述方法二），也是一件很费时的事情。**

**2.此法最好隐藏代码是写一个插件，插件以DLL的形式引用、调用、甚至挂载在GameObject上。**

 

 

 

 

***\*相关资料查询：\****

DLL构建、隐藏代码

https://answers.unity.com/questions/1707814/how-to-hide-c-code-from-custom-package-for-distrib.html

https://www.jacksondunstan.com/articles/3052

https://answers.unity.com/questions/1078603/unity-editor-script-in-dll.html

https://www.youtube.com/watch?v=CPkO1Gek8XQ

ADF

https://blog.csdn.net/baidu_39447417/article/details/115151569
