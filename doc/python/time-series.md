import plotly.graph_objects as go
import pandas as pd

# 修正数据准备
data = {
    "年份": [2019, 2020, 2021, 2022, 2023, 2024],
    "采购额": [1959.8, 1951.9, 2832.2, 2909.7, 3284.2, 2941.8],
    "吨重": [8399.0, 8377.5, 11776.0, 11107.6, 12631.6, 11350.2],
    "含税单价": [2.33, 2.33, 2.41, 2.62, 2.60, 2.59]
}

# 创建数据框
df = pd.DataFrame(data)

# 创建图表
fig = go.Figure()

# 添加采购额柱状图
fig.add_trace(go.Bar(
    x=df["年份"],
    y=df["采购额"],
    name="采购额",
    marker_color="blue"
))

# 添加吨重柱状图
fig.add_trace(go.Bar(
    x=df["年份"],
    y=df["吨重"],
    name="吨重",
    marker_color="green"
))

# 添加含税单价折线图
fig.add_trace(go.Scatter(
    x=df["年份"],
    y=df["含税单价"],
    name="含税单价",
    mode="lines+markers",
    line=dict(color="red", width=2)
))

# 图表布局
fig.update_layout(
    title="公司前十大粉体供应情况统计",
    xaxis_title="年份",
    yaxis_title="数值",
    barmode="group",
    legend_title="指标",
    template="plotly_white"
)

# 显示图表
fig.show()
