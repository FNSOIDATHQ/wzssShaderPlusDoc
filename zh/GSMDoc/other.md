## 目录
*  [附录1 GSM代码编译流程](#附录1_GSM代码编译流程)
*  [返回](./menu.md)

# 附录1 GSM代码编译流程
关于这部分内容我知之甚少，因为我没有引擎源代码，也没有shader文件夹里其余的着色器代码。  
但是根据查询可执行文件的硬编码文本和对GSM文件的观察，编译流程应当如下：  
* 1. 根据GSM文件的md5值比对，确定当前要使用的着色器是否已经被编译，如果没有则继续进行第二步，如果有则跳转到第六步
* 2. 根据代码内容，必要的输入输出和#define被自动识别并打包为shader_combinations.set
* 3. GSM文件被转换为HLSL代码，猜测文件名为scheme.h(在报错时出现的名字)
* 4. 转换后的HLSL与shader文件夹中的代码被合并并编译为着色器缓存
* 5. 着色器缓存被存储到%LOCALAPPDATA%\Men of War II\shader_cache\文件夹
* 6. 游戏读取缓存并执行着色器