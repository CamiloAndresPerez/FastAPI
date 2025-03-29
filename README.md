
# 🦌API de Clasificación con FastAPI 

Este proyecto despliega un modelo de clasificación (Random Forest con el dataset Iris) como un servicio web usando **FastAPI**. El modelo está entrenado y expuesto a través de un endpoint REST para facilitar su integración con otras aplicaciones.

---

##  Modelo

Se usó un clasificador `RandomForestClassifier` de `scikit-learn` entrenado con el dataset `Iris`. El modelo fue serializado con `joblib`.

---

##  Estructura del Proyecto

```
fastapi-classification-api/
├── app/
│   ├── main.py
│   ├── model.py
│   ├── schemas.py
│   └── logger.py
├── model/
│   └── modelo_entrenado.pkl
├── requirements.txt
├── README.md
└── notebook_deploy.ipynb
```

---

##  Cómo ejecutar la API

###  Requisitos

- Python 3.8+
- FastAPI
- Uvicorn
- Scikit-learn
- Joblib

Instalación de dependencias:

```bash
pip install -r requirements.txt
```

### ▶️ Ejecución local

```bash
uvicorn app.main:app --reload
```

Visita: [http://localhost:8000/docs](http://localhost:8000/docs)

---

##  Despliegue desde Google Colab

1. Entrena y guarda el modelo (`modelo_entrenado.pkl`)
2. Ejecuta la API en Colab con FastAPI + Uvicorn
3. Usa `ngrok` para exponer el endpoint:

```python
!pip install fastapi uvicorn nest-asyncio pyngrok
!ngrok config add-authtoken 
```

---

##  Endpoint de Predicción

### `POST /predict`

- Input:
```json
{
  "features": [5.1, 3.5, 1.4, 0.2]
}
```

- Output:
```json
{
  "prediction": 0
}
```

---

##  Pruebas

### curl (Windows compatible)

```bash
curl -X POST "https://https://9270-34-75-103-151.ngrok-free.app.ngrok-free.app/predict" -H "Content-Type: application/json" -d "{"features": [5.1, 3.5, 1.4, 0.2]}"
```

### Postman

- URL: `https://https://9270-34-75-103-151.ngrok-free.app.ngrok-free.app/predict`
- Método: `POST`
- Body (raw/JSON):

```json
{
  "features": [5.1, 3.5, 1.4, 0.2]
}
```

---

### Resultado Satisfactorio

![image](https://github.com/user-attachments/assets/f0aac0d5-f5bb-47c3-9371-a82f4f34d61d)

## ️ Logging

Se registra cada solicitud en un archivo `api.log` para monitoreo básico.

---

##  Créditos

Proyecto desarrollado por Camilo Andres Pérez Moreno para demostrar el despliegue de modelos de Machine Learning con FastAPI como API REST, probado localmente y en Google Colab.



##  Notebook de Google Colab

Puedes ver todo el proceso de entrenamiento, serialización del modelo y despliegue con FastAPI documentado paso a paso en el siguiente notebook:

 [Abrir en Colab](https://colab.research.google.com/drive/1rWsUG5gi6qt2m2k52JUUqxCJhbNs4u-k?usp=sharing)
