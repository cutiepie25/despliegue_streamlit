# despliegue_streamlit

App de **Streamlit** que despliega un modelo de regresión (Minería de Datos) para predecir **cuánto invertirá un cliente en una tienda de videojuegos**.

## Cómo funciona

1. Carga desde `modelo-reg.pkl` el modelo entrenado, el `MinMaxScaler` y la lista de variables.
2. El usuario ingresa los datos en la interfaz:
   - **Edad** (14 a 52)
   - **Videojuego**: Mass Effect, Battlefield, Fifa, KOA: Reckoning, Crysis, Sim City, Dead Space, F1
   - **Plataforma**: Play Station, Xbox, PC, Otros
   - **Sexo**: Hombre, Mujer
   - **Consumidor habitual**: True, False
3. Las variables categóricas se convierten con *one-hot encoding* (`pd.get_dummies`) y se alinean con las columnas del entrenamiento (`reindex`).
4. El modelo (árbol de decisión, con un error aproximado del 12 %) hace la predicción.

## Archivos

| Archivo | Descripción |
|---------|-------------|
| `app.py` | Interfaz de Streamlit y lógica de predicción |
| `modelo-reg.pkl` | Modelo serializado: `(modelo, min_max_scaler, variables)` |
| `requirements.txt` | Dependencias |

## Ejecución

```bash
python -m venv .venv
source .venv/bin/activate        # En Windows: .venv\Scripts\activate
pip install -r requirements.txt streamlit
streamlit run app.py
```

> `streamlit` no está en `requirements.txt`, por eso se instala aparte. Para desplegar en Streamlit Community Cloud, agrégalo al archivo.
