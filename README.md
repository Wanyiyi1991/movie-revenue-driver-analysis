# 🎬 电影票房驱动因素分析

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3+-orange)](https://scikit-learn.org/)
[![SHAP](https://img.shields.io/badge/SHAP-0.42+-red)](https://github.com/shap/shap)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 整合4,800+部电影数据，通过特征工程+随机森林建模，用SHAP量化每个因素对票房的影响——发现"热度>口碑"是商业电影的核心逻辑。

## 📊 项目概览

对 TMDB 5000 Movie Dataset 进行从数据解析到模型解释的全流程分析。原始数据以JSON格式嵌套，经过**解析+特征工程+建模+SHAP解释**四步，最终输出一个R²=0.78的票房预测模型，并量化了每个驱动因素的影响大小。

## ❓ 回答的核心问题

| 序号 | 业务问题 | 分析方法 |
|------|----------|----------|
| 1 | 票房和评分的分布如何？它们相关吗？ | 分布分析 + 散点图 + 相关系数 |
| 2 | 哪些电影类型最赚钱？哪种评分最高？ | 类型拆解 + 分组聚合 |
| 3 | 预算和票房是什么关系？ROI如何？ | 散点图 + 盈亏平衡线 |
| 4 | 上映月份对票房有影响吗？ | 月度趋势 + 暑期档/圣诞档对比 |
| 5 | **什么因素真正驱动票房？影响多大？** | SHAP特征重要性分析 |

## 🔍 核心发现

1. **票房和评分几乎不相关**：相关系数仅0.21，"叫好≠叫座"
2. **热度>口碑**：SHAP分析显示，`vote_count`（评分人数=热度）是票房第一驱动力，远超`vote_average`（评分本身）
3. **Adventure最赚钱，Drama口碑最好**：存在清晰的"商业型vs口碑型"光谱
4. **预算推高票房，但ROI边际递减**：大制作风险更高，Horror是小成本高回报的典范
5. **导演的"品牌效应"确实存在**：导演历史平均票房对当前电影有显著正向影响
6. **暑期档票房优势明显**：6-8月上映的电影票房中位数高出全年均值约20%

## 🛠 技术栈

- **数据清洗**: Pandas, NumPy, ast (JSON解析)
- **特征工程**: 15+新特征（档期/ROI/导演历史成绩/标题长度等）
- **可视化**: Matplotlib, Seaborn
- **建模**: Scikit-learn (Linear/Ridge/Random Forest), 5折交叉验证
- **模型解释**: SHAP (Summary Plot + Dependence Plot)

## 📁 项目结构
movie-revenue-driver-analysis/  
├── README.md  
├── requirements.txt  
├── data/  
│ ├── tmdb_5000_movies.csv  
│ └── tmdb_5000_credits.csv  
├── notebooks/  
│ └── movie_analysis.ipynb # 完整分析过程  
├── images/  
│ ├── movie_distributions.png  
│ ├── revenue_vs_rating.png  
│ ├── genre_performance.png  
│ ├── budget_roi_analysis.png  
│ ├── release_month_analysis.png  
│ ├── correlation_heatmap.png  
│ ├── model_comparison.png  
│ ├── shap_summary.png  
│ └── shap_bar.png  
└── report/  
└── 电影票房驱动因素分析报告.md


## 🚀 快速复现

```bash
# 1. 克隆仓库
git clone https://github.com/Wanyiyi1991/movie-revenue-driver-analysis
cd movie-revenue-driver-analysis

# 2. 安装依赖
pip install -r requirements.txt

# 3. 下载数据
# 从 Kaggle 搜索 "TMDB 5000 Movie Dataset" 下载两个CSV文件
# 放入 data/ 文件夹

# 4. 启动 Jupyter
jupyter notebook notebooks/movie_analysis.ipynb

## 📈 关键可视化

### SHAP特征重要性——什么真正驱动票房？

https://github.com/Wanyiyi1991/movie-revenue-driver-analysis/blob/main/images/shap_summary.png

> 横轴是影响方向，颜色代表特征值高低。vote_count（热度）红色点集中在右侧，是票房最强正向驱动力。vote_average（评分）的影响幅度远小于热度。

### 电影类型的"商业-口碑"光谱

https://github.com/Wanyiyi1991/movie-revenue-driver-analysis/blob/main/images/genre_performance.png

> Adventure/Animation/Sci-Fi处在商业端（高票房），Drama/Documentary处在口碑端（高评分）。

## 💡 业务建议（如果我是制片厂）

- 🎬 **商业大片公式**：Adventure/Animation + 暑期档 + 知名导演 + 充足营销预算
    
- 🏆 **冲口碑路线**：Drama + 获奖潜力导演 + 秋季上映
    
- 💰 **小成本突围**：Horror类型ROI中位数极高，$5M预算可博$20M+票房
    
- ⚠️ **风险预警**：预算>$150M的电影，ROI为负的概率约30%
    

## 👤 关于我

[一个数据分析探索者、爱好者！
QQ：783899056
Email：wanyiyi1991@gmail.com]

---

⭐ 如果这个项目对你有帮助，欢迎给个Star！
