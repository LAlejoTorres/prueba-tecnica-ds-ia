# Prueba Tecnica — Cientifico de Datos para Soluciones con IA

Solucion a los 7 puntos planteados por el equipo de Canales Digitales

## Estructura del Repositorio

```
notebooks/
  01_top_products_analysis.ipynb        # Punto 1: Top 5 productos por volumen e ingresos
  02_customer_pain_points.ipynb         # Punto 2: Mayor dolor del cliente y categorias relacionadas
  03_customer_segmentation.ipynb        # Punto 3: Segmentacion de clientes (fieles vs esporadicos)
  04_recommendation_engine.ipynb        # Punto 4: Arquitectura de recomendacion en tiempo real
  05_flagship_store_location.ipynb      # Punto 5: Mejor ubicacion para tienda insignia
  06_knowledge_base_rag.ipynb           # Punto 6: Base de conocimiento simulada (JSON)
  07_ai_agent_system_prompts.ipynb      # Punto 7: 3 System Prompts hiper-personalizados

data/
  knowledge_base.json                   # Punto 6: Base de conocimiento en JSON (entregable)

outputs/                                # Imagenes, CSVs y artefactos generados

pyproject.toml                          # Dependencias del proyecto (uv)
```

## Resumen de Cada Punto

### Punto 1 — Top 5 Productos y Categorias
Identificacion de los 5 productos/categorias mas vendidos por volumen y por ingresos. Incluye analisis de Pareto (18 de 72 categorias generan el 80% de ingresos) y matriz estrategica volumen vs. ingresos.

### Punto 2 — Mayor Dolor del Cliente
Pipeline NLP en portugues (spaCy + TF-IDF) sobre 10,297 resenas negativas. El dolor #1 es entregas tardias (51.6% de quejas). Validacion con analisis Haversine de distancia vendedor-cliente como causa raiz.

### Punto 3 — Segmentacion de Clientes
Segmentacion comportamental con K-Means (K=4). Realidad critica: 97% de clientes con una sola compra. 4 segmentos: Loyal Champions (3.3%), Premium Buyers (17.8%), Mid-Value Buyers (47.8%), Low-Engagement Buyers (31.1%). Capa de riesgo de servicio independiente.

### Punto 4 — Motor de Recomendacion en Tiempo Real
Arquitectura de 3 niveles (cold/warm/hot) con routing por perfil e historial. Re-ranking por segmento con pesos dinamicos. Evaluacion offline: Hit Rate @5 = 87.5%. Diagrama de arquitectura completo con ciclo de retroalimentacion.

### Punto 5 — Ubicacion de Tienda Insignia
Embudo de seleccion en 5 pasos: pais, estado, ciudad, zona, validacion. Sao Paulo, Zona #1 (puntaje 0.936/1.000). DBSCAN adaptativo + puntaje compuesto. 374 vendedores dentro de 10 km para fulfillment local.

### Punto 6 — Base de Conocimiento
JSON estructurado con 3 capas (cliente, metadata, negocio) para 3 productos top. Precios reales extraidos del dataset. Disenada para ser consumida por un Agente de IA via RAG.

### Punto 7 — System Prompts del Agente IA
3 prompts hiper-personalizados (Nova, Clara, Alejandro) para 3 arquetipos de cliente. Variables dinamicas: [EDAD], [GENERO], [PERFIL_DE_CLIENTE], [HISTORIAL_COMPRAS], [BASE_CONOCIMIENTO]. Incluye guardas anti-alucinacion y demostracion con datos reales.

## Datos

El dataset no esta incluido en el repositorio por su tamano (123MB). Los 9 archivos CSV deben colocarse en la carpeta `Dataset_prueba/`:

- customers_dataset.csv
- geolocation_dataset.csv
- order_items_dataset.csv
- order_payments_dataset.csv
- order_reviews_dataset.csv
- orders_dataset.csv
- product_category_name_translation.csv
- products_dataset.csv
- sellers_dataset.csv

## Ejecucion

```bash
# Instalar dependencias
uv sync

# Ejecutar notebooks (orden recomendado: 01 a 07)
uv run jupyter lab
```

