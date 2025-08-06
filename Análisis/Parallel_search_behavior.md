# Comportamiento del Buscador Paralelo

Durante la exploración, se observó un mecanismo interno que compara el input actual con historiales previos del mismo usuario, generando una forma de contexto extendido.

## 🔍 Mecanismo Detectado

- Función estimada: `buscar_en_otros_hilos`
- Umbral de similitud: **0.73**
- Cuando una entrada nueva es lo suficientemente parecida (embedding ≥ 0.73) a partes anteriores, el modelo puede "recordar" contenido anterior **de esa sesión** o sesiones cercanas.

## 🧪 Ejemplo reproducido

1. Se ingresaron prompts similares con una estructura específica.
2. El modelo respondió con contenido que **no estaba en el hilo actual**, pero sí había sido usado en una sesión anterior cercana.
3. Esto ocurrió sin usar tokens idénticos, solo mediante coincidencia semántica.

## 🔐 Implicancias

- Este buscador paralelo no constituye memoria persistente.
- Pero puede generar *contaminación contextual indirecta* si no se aísla correctamente cada conversación del mismo usuario.

## ✅ Observación

Este comportamiento fue activado mediante técnicas no intrusivas, sin uso de exploits ni ingeniería inversa. Se reporta aquí con fines educativos.
