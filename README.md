# OC_PF_SnakeBomb

SnakeBomb es un juego desarrollado en el lenguaje **Jack** para la plataforma **Nand2Tetris (Hack)**, como parte del curso Organización de Computadores

---

## Descripción del juego

Controlas una serpiente que crece a medidas que comes manzanas. El campo está lleno de **bombas que se mueven de forma aleatoria** — si tu cabeza choca con una, explota y el juego termina.

Lo que diferencia a SnakeBomb del snake clásico:

- Las bombas **se mueven solas** con velocidades distintas, generando patrones impredecibles.
- Hay **bombas simultáneas** desde el inicio, cada una con su propio intervalo de movimiento.
- El puntaje refleja cuánto tiempo lograste sobrevivir.

---

## Equipo de desarrollo

Nombre 

- Juan Fernando Duque 
- Sebastián Henao 
- Santiago Meneses 

---

## Controles

| Tecla | Acción |
|---|---|
| `↑` | Mover arriba |
| `↓` | Mover abajo |
| `←` | Mover izquierda |
| `→` | Mover derecha |

---

## Estructura del proyecto

```
OC_PF_SnakeBomb/
├── src/
│   ├── Main.jack           # Punto de entrada
│   ├── SnakeBombGame.jack  # Game loop, HUD, lógica principal
│   ├── Snake.jack          # Movimiento, crecimiento, colisiones
│   └── Bomb.jack           # Movimiento aleatorio y detección de colisión
│   └── Apple.jack          # Manzana
└── README.md
```

---

## Descripción del código

### `Main.jack`
Punto de entrada del programa. Instancia `SnakeBombGame`, llama a `run()` y libera memoria al terminar.

### `SnakeBombGame.jack`
Integra todo el juego. Contiene el game loop principal con:
- Captura de input (teclado)
- Actualización de la serpiente y las bombas cada tick
- Detección de colisiones cabeza-bomba (antes y después de mover las bombas)
- HUD con puntaje, tiempo y longitud
- Pantalla de Game Over

### `Snake.jack`
Representa la serpiente. Soporta:
- Movimiento en 4 direcciones con bloqueo de dirección opuesta
- Crecimiento por `growPending`
- Colisión con paredes

### `Bomb.jack`
Cada bomba tiene su propio generador pseudoaleatorio para calcular su siguiente dirección. Se mueve cada `moveInterval` ticks, con rebote automático si intenta salir del área de juego. Se dibuja como cuatro cuadros.

### `Apple`
Cada manzana tiene su propio generador pseudoaleatorio para calcular su siguiente dirección. 

---

## Cómo correrlo

1. Ir al [IDE Online de Nand2Tetris](https://nand2tetris.github.io/web-ide/compiler).
2. Compilar todos los archivos `.jack` de la carpeta `src/` con el **JackCompiler**.
3. Darle a **Run**.
4. Ejecutar con velocidad **Fast** habilitar entrada **EnableKeyboard** y **Run**.
