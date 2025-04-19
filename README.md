# OCR-Template-Matching
这是一个基于OpenCV和模板匹配的信用卡数字识别系统，能够自动识别信用卡上的卡号并判断信用卡类型（Visa、MasterCard等）
功能特性
自动识别信用卡上的16位数字

支持4种主要信用卡类型识别：

American Express（以3开头）

Visa（以4开头）

MasterCard（以5开头）

Discover Card（以6开头）

可视化处理过程，便于调试

依赖环境
Python 3.x

OpenCV 4.x

NumPy

imutils

安装依赖：

bash
pip install opencv-python numpy imutils
文件结构
.
├── ocr_template_match.py    # 主程序
├── myutils.py              # 工具函数
└── README.md               # 说明文档
使用方法
1. 准备模板图像
准备一个包含OCR-A字体数字的模板图像（如ocr_a_template.png）

确保图像中数字从左到右依次排列（0-9）

2. 运行程序
bash
python ocr_template_match.py -i [信用卡图像路径] -t [模板图像路径]
示例：

bash
python ocr_template_match.py -i credit_card.png -t ocr_a_template.png
3. 查看结果
程序会显示：

信用卡类型（如Visa、MasterCard等）

识别出的信用卡号码

处理过程中的各个步骤图像（按任意键继续）

处理流程
模板预处理：

灰度转换

二值化

轮廓提取

数字模板创建

信用卡图像处理：

尺寸调整

灰度转换

礼帽操作（突出明亮区域）

Sobel边缘检测

闭操作（连接数字区域）

阈值处理

数字识别：

轮廓检测

数字区域定位

模板匹配

结果输出

自定义调整
如需提高识别率，可以调整以下参数：

rectKernel 和 sqKernel 的大小（当前为(9,3)和(5,5)）

数字区域筛选条件（当前宽高比2.5-4.0，宽度40-55，高度10-20）

模板匹配方法（当前使用cv2.TM_CCOEFF）

注意事项
确保模板图像中的数字清晰可辨

信用卡图像建议分辨率不低于300dpi

光线均匀的信用卡照片识别效果最佳

程序会显示多个中间处理图像，按任意键继续

示例图像
建议使用包含标准OCR-A字体数字的信用卡图像进行测试。
