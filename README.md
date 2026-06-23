# 🇪🇨 Calculadora de Clasificación — Ecuador Copa Mundial 2026

Una página web autónoma que muestra la probabilidad de que Ecuador avance de la fase de grupos de la Copa Mundial de la FIFA 2026, con datos en vivo, cuotas de mercado y un modo de escenarios hipotéticos.

## Funciones

- **Idiomas**: Español por defecto, con interruptor a inglés.
- **Responsive**: funciona en móvil, tablet y escritorio; las tablas anchas se desplazan horizontalmente y la Fase 2 se adapta a pantallas pequeñas.
- **Formato del torneo**: 12 grupos de 4 equipos. Los 2 primeros de cada grupo clasifican directamente, más los 8 mejores terceros (32 equipos en total).
- **Datos en vivo**: Obtiene resultados de `worldcup26.ir` con respaldo en `openfootball/worldcup.json`.
- **Cuotas de partido de Polymarket**: Para cada partido restante, intenta obtener las probabilidades reales de victoria local, empate y victoria visitante desde Polymarket.
- **Respaldo por cuotas de ganador del torneo**: Si no hay cuotas de partido para un encuentro, usa las cuotas de "¿Ganará X el Mundial?" como indicador de fuerza relativa.
- **Dos probabilidades**: se muestran dos estimaciones en paralelo:
  - **Matemática pura**: todos los resultados pendientes tienen la misma probabilidad.
  - **Con cuotas de mercado**: ponderada por Polymarket (cuotas de partido cuando existen, o cuotas de ganador del torneo como respaldo).
- **Top 4 + Ecuador**: la tabla de cuotas de Polymarket muestra los 4 favoritos y, como quinta fila, Ecuador con su ranking real.
- **Fase 2 — Qué pasaría si...**: ingresa resultados hipotéticos de forma sencilla:
  - El partido de Ecuador aparece primero, resaltado.
  - Botón **Autofill con Polymarket**: rellena todos los partidos restantes con el resultado más probable según las cuotas del mercado.
  - Una barra de progreso muestra cuántos marcadores has llenado.
  - Los demás partidos se agrupan por grupo y se pueden expandir/colapsar.
  - Las cuotas de Polymarket se usan automáticamente; puedes editarlas manualmente mostrándolas con un clic.

## Archivos

- `index.html` — toda la calculadora (HTML, CSS y JavaScript en un solo archivo).

## Ejecutar localmente

Abre `index.html` directamente en cualquier navegador moderno, o sírvelo con un servidor local:

```bash
python3 -m http.server 8000
# luego abre http://localhost:8000
```

## Publicar en GitHub Pages (gratis)

1. Crea un nuevo repositorio público en GitHub y sube `index.html`.
2. Ve a **Settings → Pages**.
3. En **Build and deployment**, selecciona **Deploy from a branch**, luego `main` y `/ (root)`.
4. Guarda. Tu calculadora estará disponible en `https://TU_USUARIO.github.io/TU_REPO/`.

## Incrustar en Google Sites

1. Publica la calculadora en GitHub Pages (ver arriba).
2. En Google Sites, haz clic en **Insertar → Insertar**.
3. Elige **Código de inserción** y pega:

```html
<iframe
  src="https://TU_USUARIO.github.io/TU_REPO/"
  width="100%"
  height="1000"
  frameborder="0"
  allowfullscreen>
</iframe>
```

4. Ajusta el valor de `height` para que toda la calculadora sea visible sin demasiado desplazamiento.

## Fuentes de datos

- Partidos: `https://worldcup26.ir/get/games`, `/get/groups`, `/get/teams`
- Respaldo: `https://raw.githubusercontent.com/openfootball/worldcup.json/master/2026/worldcup.json`
- Cuotas de partido: `https://gamma-api.polymarket.com/events/slug/fifwc-{local}-{visitante}-{aaaa-mm-dd}`
- Cuotas de ganador del torneo: `https://gamma-api.polymarket.com/markets?limit=100`

## Notas

- La probabilidad de la **Fase 1** siempre intenta usar cuotas de resultado de partido de Polymarket; si no existen para un partido, cae en cuotas de ganador del torneo y, como último recurso, en probabilidades iguales.
- Puedes pegar cuotas exactas de cualquier casa de apuestas (incluyendo valores de Oddschecker copiados manualmente) en la **Fase 2** para anular las cuotas automáticas.
