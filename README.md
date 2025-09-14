🔥 Detecção de Fumaça e Fogo com YOLOv8 (Transfer Learning)  
📌 Descrição do Projeto

Este projeto tem como objetivo treinar um modelo YOLOv8 utilizando Transfer Learning para detectar fumaça e fogo em imagens.
Foram adicionadas pelo menos duas novas classes (smoke e fire) ao modelo pré-treinado, mantendo também as classes originais já aprendidas.

A detecção de fumaça e fogo pode ser aplicada em sistemas de monitoramento de incêndios florestais, indústrias e ambientes urbanos, auxiliando na prevenção de acidentes.

📂 Estrutura do Projeto  
├── README.md  
└── Treinamento_Rede_Yolo.ipynb.ipynb  

🗂️ Dataset

* Utilizado: [Smoke & Fire Detection YOLO Dataset (Kaggle)](https://www.kaggle.com/datasets/sayedgamal99/smoke-fire-detection-yolo)
* O dataset já está no formato YOLO, com as classes:
    * 0 → Fire 🔥
    * 1 → Smoke 💨

⚙️ Tecnologias Utilizadas

* Python 3
* PyTorch
* Ultralytics YOLOv8
* Kaggle API

🚀 Como Executar o Projeto
1. Clonar o repositório
<pre>
bash 

git clone https://github.com/DenisePotenza/Treinamento-com-Rede-Yolo-DIO.git
cd Treinamento-com-Rede-Yolo-DIO </pre>

2. Instalar dependências
<pre>
bash
  
pip install ultralytics torch torchvision torchaudio kaggle</pre>

3. Baixar dataset do Kaggle

* Baixe sua API Key em [Kaggle → Settings → Create API Token](https://www.kaggle.com/settings)


* Coloque o arquivo kaggle.json em:

  * Linux/Mac: ```~/.kaggle/kaggle.json ```

  * Windows: ```C:\Users\SEU_USUARIO\.kaggle\kaggle.json```

Depois rode:
<pre>
bash
  
kaggle datasets download -d sayedgamal99/smoke-fire-detection-yolo -p smoke_fire_dataset
unzip smoke_fire_dataset/smoke-fire-detection-yolo.zip -d smoke_fire_dataset
</pre>

4. Treinar modelo
<pre>
python
  
from ultralytics import YOLO

# Carregar modelo pré-treinado
model = YOLO("yolov8s.pt")

# Treinar com Transfer Learning
model.train(
    data="smoke_fire_dataset/data.yaml",
    epochs=30,
    imgsz=640,
    batch=16,
    device=0   # use "cpu" se não tiver GPU
)</pre>

5. Fazer predição em uma imagem
<pre>
python
  
results = model.predict("smoke_fire_dataset/valid/images/alguma_imagem.jpg", show=True)</pre>

📊 Resultados

* Métricas principais: mAP, precisão e recall.
* O modelo treinado fica salvo em:
<pre>
swift
  
runs/detect/train/weights/best.pt</pre>


📌 Próximos Passos

+ [ ] Aumentar o número de épocas para melhorar desempenho
+ [ ] Testar com YOLOv8m ou YOLOv8l para maior acurácia
+ [ ] Implementar deploy em Streamlit ou Flask para demo web

👩‍💻 Autora

Projeto desenvolvido por Denise Potenza.  
📫 [LinkedIn](https://www.linkedin.com/in/denise-ribeiro-potenza/)
 | 🌐 [GitHub](https://github.com/DenisePotenza)
