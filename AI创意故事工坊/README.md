一、执行环境
项目：配置
平台：飞桨 AI Studio（百度）
Python 版本：3.8 或以上
网络要求：需联网（调用 API 服务）
依赖库
bash
openai>=1.0.0
erniebot>=0.6.0
edge-tts>=6.0.0
安装命令：
!pip install openai erniebot edge-tts
二、功能说明
本项目实现以下三个核心功能：
序号	功能名称	说明
1	AI 故事生成	根据用户输入的主题，调用大语言模型（ERNIE-4.0-8K）自动生成约 500 字的完整故事
2	AI 配图生成	从故事中智能提取 3 个关键场景，调用文心一格（ERNIE-ViLG）生成对应的配图（PNG 格式）
3	AI 语音解说	将完整故事文本合成为 MP3 格式的有声读物（中文女声）
工作流程
text
用户输入主题 → AI生成故事 → 提取关键场景 → 生成配图 → 语音合成 → 输出完整作品
输出文件
所有生成文件保存在 outputs/ 目录下：
story.txt — 故事文本
scene_1.png ~ scene_3.png — 场景配图（3张）
story_YYYYMMDD_HHMMSS.mp3 — 语音解说
运行示例
text
Please enter story theme: 一只会拉小提琴的章鱼在深海的失落城市里举办音乐会

[Info] Generating story... (about 10-20s)
[Success] Story saved to: outputs/story.txt
[Success] Extracted 3 scenes
[Success] 3 images generated
[Success] Audio saved to: outputs/story_20260624_103045.mp3
All done! Files are in 'outputs/' directory.
三、运行步骤
在 AI Studio 中打开项目，安装依赖：

python
!pip install openai erniebot edge-tts
获取 Access Token：AI Studio 左侧菜单 → “访问令牌” → 复制令牌。
在代码中替换 ACCESS_TOKEN 为你的实际令牌。
运行主程序，按提示输入故事主题。
在 outputs/ 目录中查看生成结果。
四、注意事项
Access Token 有效性：请确保 Token 未过期，若失效请在 AI Studio 重新生成。
模型可用性：程序已配置多个备用模型（ERNIE-4.0-8K → ERNIE-3.5-8K → deepseek-v3），若主模型不可用会自动切换。

运行时长：完整流程约需 60-120 秒（含图像生成和语音合成），请耐心等待。

网络依赖：所有 API 调用均需联网，请确保网络通畅。

免费额度：AI Studio 提供 100 万免费 Tokens，足以完成本项目测试。

五、其他说明
参考资源
飞桨 AI Studio 大模型 API 文档
文心一格图像生成服务
edge-tts 语音合成库


