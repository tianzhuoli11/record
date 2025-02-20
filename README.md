# intership record
# Started at Nov 26 2024

### 阶段任务
    学习mybuddy项目代码
    帮助张老师解决提取图像背景问题
    眼部提取
    生成空白视频帧
    去测试环境是否能跑程序
    解决text input问题
    解决大模型问题
    解决语音打断问题

# Nov 26 - Nov 28
    了解数字人项目大致流程技术栈

# Nov 29
    参加数字人组会
    向殷老师、邹老师、张老师学习拿到账号，按照流程开始安装程序

# Nov 30
    程序安装好后有一些bug做了debug操作
    和张老师做了远程系统交互测试
    学习核心模型ernerf
    看ernerf代码

# Dec 2
    Installation process:
    1. Install Cuda 12.3.
    2. Unzip PC-Assistant.zip.
    3. Click directly my-buddy to install.
    4. After finishing installation, open cmd as administrator.
    5. Navigate to dictionary of my-buddy.
    6. Execute app-launch.bat.

    Errors raised during the period of Installation:
    1. Happend in process 6, "No module named 'pywin32-bootstrap'" and "No module named '-cffi-backend'"
    Resolution: reinstall my-buddy.
    2. Happend in process 6, "Cannot conected to huggingface.co"
    Resolution: use global proxy.
    3. Happend in process 6, "Buffer exhausted"
    Resolution: try increasing the value of config.first_num_idle_frames in src\ernerf\config.py.
    4. Caught exception: Nonzero statue code returned while running Loop node
    Caught exception: Nonzero statue code returned while running ConstantOfShape node.
    Caught exception: tensorshape cannot contain negative value
    Resolution: 

    调试mybuddy：
    1. 更改#for window 参数
    无效
    2. 更改config.first_num_idle_frames in src\ernerf\config.py大小 10 50 100 1000
    画面会卡顿

    10无法对话，直接buffer exhausted
    50说一句话
    100可以说一句话
    1000向上并没有太多变化，无法完成加载
    10000

    调整光线设置
    ## 工作内容总结：对于mybuddy运行环境进行测试，调整一些参数进行测试，看是否能解决内存问题
    学习核心模型ernerf
    看ernerf代码


# Dec 3
    工作内容：
    入职学习数字人大概内容
    进组参加组会，明确学习任务
    安装程序
    和张老师一同参与调试
    学习核心模型ernerf
    看ernerf代码
    学习linux
    学习docker

    调试ernerf代码问题：
    wget要用powershell运行
    有目录没有，要手动创建
    最后发现问题在问过老师之后发现是没有设置虚拟环境
    必须要用wsl走linux
    下载conda cuda12.3 下载速度很慢
    UBUNTU系统模块：
    conda 24.9.2
    cuda 12.3 安装速度非常慢
    The following packages have unmet dependencies:
    nsight-systems-2023.3.3 : Depends: libtinfo5 but it is not installable

    ##工作内容总结：学习用wsl启动linux构建虚拟机相关操作，在虚拟机安装环境，运行ernerf

# Dec 4
    更换环境
    ubuntu18 安装cuda11.3没问题
    但是后面torch和torchvision安装出现问题
    张老师建议：用docker去镜像一个系统，按照最新的教程来配置镜像和容器，别的没有意义，注意映射
    学习dockerfile docker instruction.txt
    用ubuntu18.04构建时候，常规的构建出现在dockerfile第一步出现了问题。
    ubuntu20.04构建同样的问题下载不了
    用wsl走Dockerfile原始的这个ernerf的文件成功构建，正在构建中
    镜像源！！！！问题解决！！只用一个镜像源
    安装完成

    ##工作内容总结：在虚拟linux环境下更换配置等等太复杂，也很容易造成卡顿崩溃等问题，张老师带我引进docker学习，自学docker使用，如何构建镜像容器以及dockerfile相关




# Dec 6
    安装NVIDIA container toolkit
    https://blog.csdn.net/DejaWu33/article/details/134339744?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522f64b990199b391f9d9bc66f7b687b84a%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=f64b990199b391f9d9bc66f7b687b84a&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-134339744-null-null.142^v100^pc_search_result_base5&utm_term=nvidia%20container%20toolkit%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187
    这个网站好用

    上周打的这个包没有numpy等问题
    已解决，需要激活环境

    张老师开会：
    1. 先重新配置一下环境，一步一步测试
    2. windows映射wsl，/mt/<windows 系统路径> 容器系统路径
    3. 继续做ernerf的训练
    数字人项目：
    目前需要做的是把训练和推理的dockerfile合二为一，还有linux的优化，和中断的考核
    项目工程实际，目标为先
    注意一些工具的使用，相比知道原理，对于解决实际问题知道怎么去用它更加重要
    vscode
    wsl使用
    github联动
    python多进程处理
    进程线程


    ##工作内容总结：熟悉docker镜像容器代码后，docker环境出现一些bug，解决后发现容器内和本地没能连接在一起，张老师教我一些工程相关经验




# Dec 9
    继续完成12.6的任务
    学习vscode做dockerfile镜像的步骤，测试环境
    学习vscode和github做联动的步骤
    镜像哇安城，激活环境后问题解决，按步骤安装nvidia container toolkit
    运行容器用这个：
    docker run --gpus all -d -it --name ernerf-env18 -v /mt/c/Users/tianz/Desktop/Internship/Avatar/2d-pc-assistant-code-main/ER-Nerf-main:/home/er-nerf ernerf-env18:latest #原始代码没办法连接到本地文件

    张老师：
    继续做git和ernerf混合训练使用，用这个源文件做一个上传下载训练

    ##工作内容总结：做的映射有问题，导致运行时候会各种报错



# Dec 10
    按照流程来没有parsing文件
    学会了git联动vscode

    docker run --gpus all -d -it --name ernerf-env184 -v /mnt/c/Users/tianz/Desktop/Internship/Avatar/2d-pc-assistant-code-main/ER-Nerf-main:/home/er-nerf ernerf-env18:latest 这个代码成功了，因为在 Ubuntu 或基于 Linux 的环境中（例如 WSL 或 Docker），路径前缀 /mnt 是用于挂载 Windows 文件系统的标准路径，而 /mt 是无效的，因为它不是系统挂载点的默认命名。除非您手动创建并设置了挂载规则

    COPY in powershell
    docker cp C:/Users/tianz/Desktop/Internship/Avatar/ER-NERF所需模型/checkpoints/. ernerf-env184:root/.cache/torch/hub/checkpoints

    in linux bash, from windows to docker container
    docker cp /mnt/c/Users/tianz/Desktop/Internship/Avatar/ER-NERF所需模型/checkpoints/. ernerf-env184:root/.cache/torch/hub/checkpoints
    开启镜像之后，copy文件进入目录，安装gcc模块，tensorflow模块
    python data_utils/process.py data/hm5/hm5.mp4

    12.10最后出现task5killed的问题，正在解决

    张老师，注意dockerfile里面那个文件要copy进入容器对应的目录里面，测试结果还是不行

    ##工作内容总结：经过学习，解决了映射问题，熟悉相关代码，安装了一些模型构建时候环境缺少的组件，但是出现了一些内存爆炸的问题


# Dec 11
    解决task 5 killed问题：1.内存？确实内存占满了，增加虚拟内存尝试
    sudo fallocate -l 4G /swapfile  # 创建4GB的Swap文件
    sudo chmod 600 /swapfile
    sudo mkswap /swapfile
    sudo swapon /swapfile

    再删除虚拟内存
    sudo swapoff /swapfile
    sudo rm /swapfile
    问题解决，task 5 总共需要6GBmem+5GBswp左右的内存
    task6运行时间很长
    task7运行时间也很长
    task8运行时间更长，280个包，3个小时30个，等待明天结果

    在这期间，张老师、邹老师：
    开始看以ernerf为核心的代码，但是可能因为内存占用严重，没办法解压压缩包
    创建git分支，做测试上传gitlab

    ##解决内存问题，基本完成训练，学习git管理相关操作，为后续参与开发做准备。开始看整个数字人项目主代码。

# Dec 12
    task89运行成功

    python main.py data/hm5_500 --workspace trial_hm5_500 -O --iters 100000 --asr_model hubert -stablize_mask True
    python main.py data/hm5 --workspace trial_hm5 -O --iters 10 --asr_model hubert --stablize_mask True
    python main.py data/hm5/ --workspace trial_hm5/ -O --iters 10
    运行上面指令的时候无法运行，报错一大堆，首先怀疑是raymarching安装包的问题
        安装时候报错：
    怀疑是cuda和pytorch版本兼容性，不是这个问题。
    怀疑gcc和nvidia toolkit，不是
    怀疑是更改后的setup.py问题，更改回来还是这样，不是
    怀疑是c++版本问题，更改setup.py，问题解决！！！
    张老师说先不直接install，从文件里面install一下， 

    安装raymarching，继续安装剩下三个。
    安装完成四个包，重新运行指令
    成功开始训练

    ##工作内容总结：在训练时解决了bug，通过另外一种方式安装了安装包，完成训练，写下了标准操作上传到项目组gitlab


# Dec 13
    拍摄数字人测试视频
    开始学习数字人源码，做笔记

# Dec 16
    对run文件学习，着重看了voiceassistant，ernerf的部分代码
    帮助汪双老师在新机器上build images
    学习extract_background相关代码
    问题： 在哪一步进行的extract_background，test_step在哪里
    Trainer和NeRFGUI哪一个

# Dec 17 
    明白extrac_background函数具体逻辑，使用knn去计算前景距离，抠出人像保留背景
    给汪老师搭配环境
    学习U-2-net去提取图像
    汪老师那边的hubert处理遇到问题，需要把facebook这个文件夹提到ernerf主文件夹目录下，就是data_utils外层
    给别人文件的时候，要给英伟达维护过的！！！源码不一样
    发现新的提取图像代码，SAM，学习

# Dec 18
    应用SAM,目前完成安装，但是应用还需要再做实践，结合代码和图片
    docker run --gpus all -d -it --name sam_test2 ernerf-env18:latest

    pip install git+https://github.com/facebookresearch/segment-anything.git

    git clone git@github.com:facebookresearch/segment-anything.git
    cd segment-anything; pip install -e .

    pip install opencv-python pycocotools matplotlib onnxruntime onnx

    download checkpoints file1 at windows
    docker cp /mnt/c/Users/tianz/Downloads/sam_vit_h_4b8939.pth sam_test2:app/segment-anything/segment_anything/util
    
    生成空白帧视频10s，目的是在数字人不说话期间完成视频的嵌入，参考英伟达文档


    帮张老师做300*300视频训练，把包发给他

    做背景替换，把视频的背景给变成一张图片，用rpbgimage.py文件，成功！！！

# Dec 19
    验收成果，发现脚部的图片没有替换
    继续看my_buddy源码
    继续看生成空白视频帧的代码
    从汪老师电脑解压了，超大压缩包，拷贝过来

# Dec 20
    提取背景的效果一般，还需要完善
    眨眼帧的提取，需要安装dlib的.dat文件，任务完成
    看SAM处理的效果
    
    
# Dec 23
    ##之前用简单手动的程序替换的脚本去运行时候，检测蓝色老是检测不到，主要的原因是opencv.imread导入的图片是BGR格式，需要给他变成RGB。
    张老师：下一阶段是测试环境的适配性，很多pip list里面的包没办法使用了，过程很漫长，具体的细节是：
    1. 把总安装包安装到汪老师电脑上
    2. 进行.bat文件运行（基于.tar.gz环境包）
    3. 查看日志报错
    4. 在容器里面，测试不同版本的包
    5. 打包环境，发给汪老师，重复2-5

# Dec 24
    拷贝张老师的环境和文件放到汪老师电脑上问题解决
    但是会报错ffmpeg
    本机运行时，会报错内存不足
    张老师说的主要任务意思是，现在有的这个运行程序包是已经生成好的，如果再添加新功能新的包，这个已经打好的包就不能用了需要重新打包。需要做的事情就是对照英伟达给的官方文档搭建这个环境，排除报错或者版本冲突的问题，打包成一个环境之后能够跑通目前的程序，或者是否能够把打包好的这个包返回到开发功能的状态，比如去安装

,
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn",
    "https://cr.console.aliyun.com",
    "https://mirror.ccs.tencentyun.com",
    "https://docker.mirrors.tuna.tsinghua.edu.cn"

# Dec 25
    tar zcvf mybuddy_app_v1.0.tar.gz --exclude mybuddy_app_v1.0.tar.gz --exclude models --exclude tllm_debug --exclude dist --exclude .git *
    tar zcvf models.tar.gz models
    conda pack -n my_buddy_env_py310 -o my_buddy_env_py310.tar.gz
    昨天张老师的这个问题被刘老师解决了，可以直接在这个环境里面的pip.exe去安装，直接就能解决这个问题，不需要再重新搭环境
    pip好之后按照流程可以生成新的打包程序
    inno setup

# Dec 26
    看代码，voiceassistant，nerfgui（包括teststep和render）

# Dec 27
    看代码，voiceassistant目录下面其他的.
    了解推理流程，推流流程
    大力哥教了读代码，端口，断点调试（目前没法调试）
    看完了ernerf的代码后，张老师讲解了目前遇到的问题：
    1. 如何解决把透明背景的视频推到网页上
    2. 如何增加文本输入

# Dec 30
    看完了voiceassitant所有的函数，大致明白了流程
    和张老师讨论了一下，张老师建议说先用websocket去推一个音视频上去看一下，做一下环境测试，还有就是文本那个问题同步进行。
    主要准备做text部分

# Dec 31
    做完了textinput部分，主要采用的是把文字转成语音，再通过语音输入的模式，完成了任务。但是效果不是特别好，还需要性能上的优化
    再看图像任务
    conda出问题

# 2025
# Jan 2
    增加了pyttsx3的新算法，控制tts音频速度，测试效果
    需要将输入文本原文直接在前端输出
    音频audio_chunk前面加入静音帧

# Jan 3
    音频里面静音帧添加完成
    文本没有想的那么简单，得从算法函数入手传递给前端
    解决好文本问题了，然后测试中又遇到了标点符号，对标点符号进行算法上的微调，现在的效果是别的都好但是没有办法输入符号

# Jan 6

# Jan 7
    开第三次组会：
    1. 测试丢字
    2. 想办法解决公式符号
    3. 背景块部分，抠图，小区细节
    4. 推流问题
    5. 如何直接接入文本
    6. 大语言模型问题

# Jan 8 
    测试数字人的fps：开始73，第一次对话73-61.8，第二次对话61左右，第三次对话发送之后卡顿，无论再发什么都无法继续对话。尝试刷新无用
    再测试：第一次对话71-69，第二次对话稳定在69，第三次69，第四次69
    改代码，把文本直接接入大模型，成功
    解决字数识别不清晰的问题

# Jan 9
    主要任务：研究大模型
    测试任务：测试运行时内存
        初始化9G占用，可用54.7GB
        启动程序 39.1G (1)41G (2) 41.7G 说话时上升到41.5G左右，静止时到40.9G左右
    测试任务：测试运行时显存
        初始化1.5G占用，可用47.90GB
        启动程序 13.2G (1)14.7G (2) 15G 15.1 15.3 15.4 15.6 之后稳定到15.6G没有变动了
    测试任务：测试运行时cpu
        启动程序占用67%，每次发送文字后cpu会打满一瞬间

    以后写代码的时候注意把init这种放在循环外面，这样的话每次循环不用再init，节省时间和资源

# Jan 10
    主要任务：1.研究大模型 2.研究语音输入冲突的问题 3.研究内存问题

    在李老师电脑运行stable1.0版本，一句话就崩了
    汪老师显卡性能不足
    李老师电脑cuda版本更新，之后可以做到和其他人电脑一样的情况
    研究语音交互逻辑
    内存问题刘博代码找出来是加载了很多的英文单词

# Jan 13
    主要任务：1. 研究语音输入冲突的问题 

    想用lock，但是张老师不建议，主要是frame有一个时间问题，还有state1有一个loop循环，未测试
    张老师说在tts last这一块加resetevent

# Jan 14
    主要任务：1. 在防止打断这一块进行优化，做一个prompt，在画面大概说完之后进行提示。
    在绿字附近加入提示之后会出现asr卡顿情况，主要问题是没有检测到vad
    麦克风输入部分问题
    
# Jan 15
    主要任务：1.麦克风输入部分问题 2. 解决了麦克风输入时一直拒绝接收的问题 

# Jan 16
    主要任务：1.
    
    猜想1.是不是语音文件传入和音频传入的格式形式不一样

# Jan 17
    解决冲突问题思路，在frame audio队列为空时候，加入event控制

# Jan 20
    控制逻辑任务完成
    但是手动打断逻辑有时会让屏蔽输入功能失效，它一直禁止输入功能
    报错assert，把assert给注释掉后并没有实际解决问题

# Jan 21
    控制逻辑debug完成，解决一直禁止输入功能
    但是在merge之后出现一些意外的问题

# Jan 22
    撰写实习报告，后续继续调试功能
    
# Jan 23
    数字人开会，主要问题：
    1. 卡顿
    2. 延时太多了
    3. 打断部分能否打断画面

# Jan 24
    数字人性能问题

# Feb 5 6
    继续数字人
    配置新的电脑，步骤在procedures

# Feb 7
    参加讲座，具身智能
    解决卡顿问题

# Feb 8
    解决卡顿问题:已经解决，通过把音频段合并
    考虑打断问题

# Feb 10
    研究打断逻辑

# Feb 11
    完成打断逻辑，但是前端代码

# Feb 12
    更改前端代码，完成打断控制逻辑，和张老师一起解决了延迟问题，但是合并方案的延迟太高了，目前采用打断逻辑但是不合并的方案部署到了楼下显示器
    后台连接我的主机

# Feb 13
    
# Feb 14
    给夏院做演示的部署最后还是部署的我的版本，夏院觉得美工宣传和品牌还需要做，张老师觉得工程技术上问题不大
    现在着重实现给张平老师的模型训练，更改代码为播报型数字人

# Feb 17
    主要更改代码去实现播报音频本地存储，图片部署这块没能实现，赶上开会，推理和训练给张老师那边去完成

# Feb 18
    统一git管理，看cs231，实现图片本地存储，打包发给张老师完成播报音频合成
    
# Feb 19
    解决音频输入留存到了下一次的问题

# Feb 20
    解决了音频输入留存到了下一次的问题，whisper需要一些微调，测试到楼下的效果，听了一个关于配置的讲座，主要讲了英伟达GPU等等硬件软件


PS C:\Users\tianz\Desktop\Internship\Avatar\ER-NeRF-main\ER-NeRF-main> docker build -f Dockerfile0 -t ernerf-env200 .
[+] Building 7012.2s (13/13) FINISHED                                                              docker:desktop-linux
 => [internal] load build definition from Dockerfile0                                                              0.0s
 => => transferring dockerfile: 2.08kB                                                                             0.0s
 => [internal] load metadata for docker.io/nvidia/cuda:11.3.1-cudnn8-devel-ubuntu20.04                             2.3s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/9] FROM docker.io/nvidia/cuda:11.3.1-cudnn8-devel-ubuntu20.04@sha256:bf709b30743d7db557f22a6e10414660f4  1823.0s
 => => resolve docker.io/nvidia/cuda:11.3.1-cudnn8-devel-ubuntu20.04@sha256:bf709b30743d7db557f22a6e10414660f4a4e  0.0s
 => => sha256:bab5e42b090969b5fad1fe641309ebe5f9013acdb9d55509b3396dd4e6c6156a 1.90GB / 1.90GB                  1798.2s
 => => sha256:48e812d52855f45d0acc800042f392bc18aa20c061697c7da24c5f5171aab5e4 1.57GB / 1.57GB                  1637.6s
 => => sha256:109a48468c4c433e8cbce16773812d111907861b26061c06ac6bf6151032f40d 1.02GB / 1.02GB                  1489.9s
 => => sha256:784f5ac03608788bc385e7e2e6ad3ed6148b6881b5b866b01a7fe602aeacbc23 7.94MB / 7.94MB                    30.5s
 => => sha256:96d54c3075c9eeaed5561fd620828fd6bb5d80ecae7cb25f9ba5f7d88ea6e15c 27.51MB / 27.51MB                  71.4s
 => => extracting sha256:96d54c3075c9eeaed5561fd620828fd6bb5d80ecae7cb25f9ba5f7d88ea6e15c                          0.4s
 => => extracting sha256:784f5ac03608788bc385e7e2e6ad3ed6148b6881b5b866b01a7fe602aeacbc23                          0.1s
 => => extracting sha256:9ecba0f44e3728547597cfb34ee25608bbf2daa19503c1c3bcaecdbcf471db50                          0.1s
 => => extracting sha256:5a50897adb412bbfe42a4a359f29ddc5326f731e7d7e0ddb1c459d3a9b7dea72                          0.0s
 => => extracting sha256:5f412bd2f1fc57b0c16288ed4ddc9bc5db33040fdc0fdf7f0e25a9539bd2dce7                          0.0s
 => => extracting sha256:109a48468c4c433e8cbce16773812d111907861b26061c06ac6bf6151032f40d                         17.1s
 => => extracting sha256:7c7262c9634ff22e828da49aea602ecffda37b28765f2bfaeeb6f45eb3e87cb1                          0.0s
 => => extracting sha256:115273afe479591bafa9360f84858211dde28170756c8874118f23d8b82a0506                          0.0s
 => => extracting sha256:179b90fac1fd9fccbc470349be5dc478d1b7c22a223be78660fac5b2827008c5                          0.0s
 => => extracting sha256:48e812d52855f45d0acc800042f392bc18aa20c061697c7da24c5f5171aab5e4                         14.9s
 => => extracting sha256:a6fb42cd5e499d552129315add8feb333dc72cbd30c3b2710b62569a5efc4306                          0.0s
 => => extracting sha256:bab5e42b090969b5fad1fe641309ebe5f9013acdb9d55509b3396dd4e6c6156a                         24.8s
 => [2/9] WORKDIR /app                                                                                             0.2s
 => [3/9] RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo Asia/Shanghai > /etc/timezone        0.6s
 => [4/9] RUN apt-get update &&     apt-get install -y --no-install-recommends         build-essential           204.8s
 => [5/9] RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh &&     bash Miniconda3  198.9s
 => [6/9] RUN /opt/miniconda/bin/conda init bash                                                                   0.6s
 => [7/9] RUN /opt/miniconda/bin/conda create --yes --name ernerf python=3.10                                     66.3s
 => [8/9] RUN /bin/bash -c "source /opt/miniconda/etc/profile.d/conda.sh && conda activate ernerf && conda ins  4252.8s
 => [9/9] RUN /bin/bash -c "source /opt/miniconda/etc/profile.d/conda.sh && conda activate ernerf && pip instal  130.7s
 => exporting to image                                                                                           331.6s
 => => exporting layers                                                                                          269.6s
 => => exporting manifest sha256:60bd533cc7dc8c655f48f314db9b73369d44301aca6920b64772896848bcb2ef                  0.0s
 => => exporting config sha256:118f0b9e496047b0090629874cce16153b5bf81c8388c842b85e58d4d92360ea                    0.0s
 => => exporting attestation manifest sha256:3b909967d410a14780f69fbe8cd8825d6ee2578c54e54a477dbbea6fbfdb5878      0.0s
 => => exporting manifest list sha256:6420fbc5541b2f43998b837139f95df6506b75e8fd94a804f9e652cd6118de3d             0.0s
 => => naming to docker.io/library/ernerf-env200:latest                                                            0.0s
 => => unpacking to docker.io/library/ernerf-env200:latest                                                        62.0s

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/xo65ud74ixbb084aytpvjzqqy
PS C:\Users\tianz\Desktop\Internship\Avatar\ER-NeRF-main\ER-NeRF-main>


第二次build ubuntu18.04
 *  正在执行任务: docker build --pull --rm -f "dockerfile18version" -t ernerf-env18 "." 

[+] Building 19.8s (4/13)                                                                                                                           docker:default
[+] Building 6348.6s (14/14) FINISHED                                                                                                               docker:default
 => [internal] load build definition from dockerfile18version                                                                                                 0.0s
 => => transferring dockerfile: 2.13kB                                                                                                                        0.0s
 => [internal] load metadata for docker.io/nvidia/cuda:11.8.0-cudnn8-devel-ubuntu18.04                                                                        2.1s
 => [auth] nvidia/cuda:pull token for registry-1.docker.io                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                                             0.0s
 => => transferring context: 2B                                                                                                                               0.0s
 => [1/9] FROM docker.io/nvidia/cuda:11.8.0-cudnn8-devel-ubuntu18.04@sha256:c2bc6ed8b72602cf32f1ef9f514589ab4f321fc7726a493a936e33528ae6db4d                946.4s
 => => resolve docker.io/nvidia/cuda:11.8.0-cudnn8-devel-ubuntu18.04@sha256:c2bc6ed8b72602cf32f1ef9f514589ab4f321fc7726a493a936e33528ae6db4d                  0.0s
 => => sha256:960d96c91fd12ab8f023f5d8e7c192feab0833b99a7ca052fadb755fccef6eca 1.47GB / 1.47GB                                                              525.9s
 => => sha256:ecf188d26601bffdb94ea7453d8b2e8b71e30ffb420470e1b299803e36484d65 1.78GB / 1.78GB                                                              903.1s
 => => sha256:1aece8b4bd634093f588f31d0d544b3b52ea701322103c0d975f28ce4bc38f01 1.38GB / 1.38GB                                                              849.2s
 => => extracting sha256:1aece8b4bd634093f588f31d0d544b3b52ea701322103c0d975f28ce4bc38f01                                                                    14.3s
 => => extracting sha256:8030ee497010e420e37b8b173851f58a09e5cace33e798247624f9b3cbb828cc                                                                     0.0s
 => => extracting sha256:a41332b1bef317dac3e7540dbbe236e17aa5db1c241c34140ff24ebb9c2d4a84                                                                     0.0s
 => => extracting sha256:aed8824e0575ddd7f0f795e370b0da8875e145398794b62e3353d5141ddfda9f                                                                     0.0s
 => => extracting sha256:ecf188d26601bffdb94ea7453d8b2e8b71e30ffb420470e1b299803e36484d65                                                                    30.1s
 => => extracting sha256:8c74646e5134e5cb564e2f08ce3b1b877cd6ed7058fd06c2975e246eabbf1690                                                                     0.0s
 => => extracting sha256:960d96c91fd12ab8f023f5d8e7c192feab0833b99a7ca052fadb755fccef6eca                                                                    11.9s
 => [2/9] WORKDIR /app                                                                                                                                        0.1s
 => [3/9] RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo Asia/Shanghai > /etc/timezone                                                   0.5s
 => [4/9] RUN apt-get update &&     apt-get install -y --no-install-recommends         build-essential         cmake         git         curl         ca-c  164.2s
 => [5/9] RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh &&     bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/minicond  213.1s
 => [6/9] RUN /opt/miniconda/bin/conda init bash                                                                                                              0.6s
 => [7/9] RUN /opt/miniconda/bin/conda create --yes --name ernerf python=3.10                                                                                59.3s
 => [8/9] RUN /bin/bash -c "source /opt/miniconda/etc/profile.d/conda.sh && conda activate ernerf && conda install -y pytorch==2.1.1 torchvision==0.16.1   4394.3s
 => [9/9] RUN /bin/bash -c "source /opt/miniconda/etc/profile.d/conda.sh && conda activate ernerf && pip install numpy==1.26.4 && pip install protobuf==3.  236.4s
 => exporting to image                                                                                                                                      320.5s
 => => exporting layers                                                                                                                                     263.5s
 => => exporting manifest sha256:5b949a5ad31828dd0430a5376bca254b486b581d12f4d5850c20307d5beccd62                                                             0.0s
 => => exporting config sha256:8ccf9e82f78f61023e5ed6a34e74dc8e6abe190156708c0d382a3a5d813fe7eb                                                               0.0s
 => => exporting attestation manifest sha256:7d2a397267b2a8451d33a18f9064d6addee27784ce2ac9ae888800ed3200b036                                                 0.0s
 => => exporting manifest list sha256:c8f5ea723a3fa94b6e8fd73a74198b3e04c7d1632936d19d01ec866347c81899                                                        0.0s
 => => naming to docker.io/library/ernerf-env18:latest                                                                                                        0.0s
 => => unpacking to docker.io/library/ernerf-env18:latest  
pytz, python_speech_features, pyaudio, tzdata, trimesh, tqdm, tifffile, threadpoolctl, soxr, six, scipy, safetensors, rege
 => => # x, pyparsing, pygments, pycparser, platformdirs, packaging, opencv-python, ninja, msgpack, mdurl, llvmlite, kiwisolver, joblib, imageio-ffmpeg, imageio, 
 => => # fsspec, fonttools, einops, decorator, dearpygui, cycler, contourpy, configargparse, audioread, tensorboardX, scikit-learn, python-dateutil, PyMCubes, poo
 => => # ch, numba, markdown-it-py, lazy-loader, huggingface-hub, cffi, torch-ema, tokenizers, soundfile, scikit-image, rich, resampy, pandas, matplotlib, transfo
 => => # rmers, lpips, librosa, face_alignment  


