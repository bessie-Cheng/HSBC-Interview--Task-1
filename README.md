1. 创建 Python 虚拟环境并安装依赖
bash
python3.12 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

2. （可选）确保模型文件存在
检查 models/housing_model.pkl 是否在目录中。如果没有，你需要先运行训练脚本生成模型：

bash
python app/train.py

3. 启动服务
bash
uvicorn app.main:app --host 0.0.0.0 --port 8002 --reload

5. 访问 Swagger UI
打开浏览器访问：
http://localhost:8002/docs

你将看到 FastAPI 自动生成的交互式 API 文档（OpenAPI），可以测试 /predict、/health、/model-info 等端点。

6. 测试端点（可选）
bash
curl -X POST http://localhost:8002/predict \
  -H "Content-Type: application/json" \
  -d '{"square_footage":1500,"bedrooms":3,"bathrooms":2,"year_built":2000,"lot_size":5000,"distance_to_city_center":10,"school_rating":7}'
   <img width="1427" height="780" alt="Swagger" src="https://github.com/user-attachments/assets/7f31073b-a56b-44d1-acc9-720410c3b314" />

