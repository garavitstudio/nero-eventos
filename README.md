# Nero · Eventos — Checklist compartida

Checklist compartida en tiempo real del equipo de **Nero Salamanca** para preparar eventos.

Alguien apunta lo que hay que llevar (botellas, servilletas, bandejas...) y el resto del
equipo va marcando desde su móvil lo que ya está hecho. Todo el mundo ve la misma lista y
los cambios aparecen al instante en todos los teléfonos, sin recargar.

---

## Cómo se usa

**Link público:** https://nero-eventos.vercel.app
*(la URL que asigne Vercel al importar el repo — ver [Despliegue](#despliegue). Si Vercel
le pone un sufijo porque el nombre está cogido, actualizar esta línea.)*

Se abre en el navegador del móvil y ya está. **No hay que instalar nada, no hay que
registrarse y no hay login.** Se pasa el link por el grupo de WhatsApp y quien lo abra
entra directo.

Lo único obligatorio es **poner tu nombre**. Sirve para que quede constancia de quién
apunta, quién marca, quién cambia las cantidades y quién borra. Si intentas hacer algo sin
haberlo puesto, **sale una ventana en medio de la pantalla** que no deja seguir hasta
escribirlo — antes era un textito debajo del campo y se colaba: si no estabas atento
parecía que la app se había quedado colgada. En cuanto lo escribes, **se hace lo que
ibas a hacer**, no hay que repetirlo. El nombre se queda guardado en ese móvil, así que
solo se escribe la primera vez.

Mirar la lista no pide nada: el nombre solo se pide al tocar algo.

Tres pestañas independientes, cada una con su propia lista:

| Pestaña | Para qué |
|---|---|
| **General** | Material y suministros generales del evento |
| **Coctelería** (José Alexis) | Lo que necesite la barra |
| **Cocina** (Jordan) | Lo que necesite la cocina |

Encima de las pestañas hay un **buscador que mira las tres a la vez** y un aviso de
**artículos repetidos** entre listas — ver [Buscador](#buscador).

Qué se puede hacer con cada punto de la lista:

- **Marcarlo / desmarcarlo** con el círculo de la izquierda. El texto se tacha, no
  desaparece.
- **Editarlo** tocando directamente el texto. Es para cuando cambia la cantidad sobre la
  marcha ("tres cajas" → "cinco cajas").
- **Borrarlo** con la ✕ de la derecha.

Debajo de cada punto queda escrito quién lo apuntó y el historial completo de cambios:
quién lo marcó, quién lo desmarcó y quién cambió qué por qué. **Ese historial no se borra
nunca**, es a propósito.

### Al apuntar algo, se elige la categoría en el momento

Al darle a **Añadir** sale una ventana con lo que has escrito y **la categoría que le ha
puesto la app ya marcada**. Si ha acertado, un toque en el botón (*"Añadir en Bebidas ·
Licores"*) y listo. Si se ha equivocado, se toca la categoría buena y se añade. Así no hay
que apuntar el punto, buscarlo luego en la lista y cambiárselo ahí.

La sugerencia sigue siendo la de siempre: la app lee el texto ("3 botellas de Beefeater" →
Bebidas · Licores). Lo que cambia es que ahora **pasa por delante de quien apunta** antes
de guardarse. Cancelar no añade nada y deja lo escrito en la caja.

### Lo que se ha borrado

Al final de cada lista hay un enlace discreto — **Ver lo borrado (3)** — que solo aparece
si se ha borrado algo en esa pestaña. Dentro está cada punto que se quitó, **quién lo
quitó, cuándo y quién lo había apuntado**. Es para cuando falta algo el día del evento y
nadie sabe qué pasó: la evidencia está ahí y se acabó la discusión.

Cada entrada lleva un **Volver a añadirlo**, por si fue sin querer. Se guardan los últimos
50 borrados de cada lista.

### Buscador

Arriba del todo, encima de las pestañas, hay un buscador que **mira las tres listas a la
vez**. Está fuera de las pestañas a propósito: la gracia es no tener que acordarse de en
cuál apuntó cada uno lo suyo. Mientras se escribe, la pestaña abierta se aparta y salen los
resultados de las tres, cada uno con la etiqueta de la lista a la que pertenece. **Se toca
un resultado y te lleva a su lista**, con el punto parpadeando un momento para no perderlo
de vista.

Lo importante: **no busca solo lo que está escrito igual**. Cada uno llama a las cosas de
una manera y las escribe como le sale, así que buscando `queso` salen también los
`quezo brie` y `quezos 4 de cada` de Jordan, y buscando `bayetas` sale `balletas`. Los que
no coinciden letra por letra vienen marcados como **Parecido**.

### Artículos que se repiten

Debajo del buscador aparece un botón con un número — **Artículos que se repiten 2** —
cuando la app encuentra puntos de las tres listas que parecen el mismo artículo escrito de
otra forma. Se toca y salen agrupados, diciendo si están repartidos **entre dos listas**
(el caso caro: se carga dos veces lo mismo en la furgoneta) o repetidos **dentro de una**.
Si no hay nada raro, el botón no aparece.

No borra ni junta nada por su cuenta, solo avisa: a veces dos cosas parecidas son dos cosas
distintas de verdad, y eso solo lo sabe quien está montando el evento.

Lo mismo pasa al apuntar algo nuevo: mientras se escribe en la caja de añadir, si eso ya
está en alguna lista sale debajo un aviso *"Puede que ya esté apuntado: «quezos 4 de cada»
en Cocina"*, y se puede tocar para ir a verlo. **Nunca impide apuntarlo.**

### Filtros

Sobre la lista hay dos filtros que se combinan, y funcionan igual en las tres pestañas:

1. **Por estado** (la barra de arriba): *Todos* · *Pendientes* · *Tachados*. Para ver de un
   vistazo lo que falta por cargar. Es igual en las tres pestañas.
2. **Por tipo**, y aquí **cada pestaña tiene los suyos**, porque a Jordan no le sirve
   filtrar por vinos y licores:

| Pestaña | Categorías |
|---|---|
| **General** y **Coctelería** | *Bebidas* (con *Refrescos* · *Vinos* · *Licores* · *Otras*) · *Utensilios* · *Otros* |
| **Cocina** | *Género* (con *Salsas* · *Charcutería* · *Congelados* · *Otros*) · *Máquinas* · *Utensilios* · *Menaje* · *Limpieza* · *Otros* |

Cada ficha lleva al lado el número de puntos que hay dentro, contando ya el filtro de
estado que tengas puesto. Si una categoría está vacía, su ficha se ve apagada.

Con un filtro puesto, el contador de abajo lo dice (`8 pendientes de 28 · mostrando 4`) para
que nadie piense que se han borrado cosas. El botón **Quitar filtros** lo deja todo a cero.
**Los filtros no se recuerdan entre visitas** a propósito: si alguien abriera el link y le
saliera media lista por un filtro del día anterior, pensaría que faltan cosas.

### Categoría de cada punto

Cada punto lleva su categoría en una etiqueta pequeña debajo del texto. **Es un desplegable:
se toca y se cambia**, con el selector nativo del móvil. Cambiarla queda registrada en el
historial igual que cualquier otra edición.

Cuando apuntas algo nuevo, la app le pone categoría sola leyendo el texto ("3 botellas de
Beefeater" → Bebidas · Licores; "palillos" → Utensilios). Si se equivoca, se corrige con
un toque. Lo que no reconoce cae en **Otros**, que es justo para eso.

Dos decisiones que conviene saber, porque son discutibles y se cambian en un toque:
**el agua va en Refrescos** (agrupa lo que son cajas de bebida sin alcohol, que es como se
carga la furgoneta) y **la cerveza va en Otras bebidas** (no es refresco, ni vino, ni licor).

---

## Cómo funciona por debajo

La app es **un único archivo HTML estático** (`index.html`) servido por Vercel. No hay
proceso de build, ni framework, ni dependencias que instalar: es HTML, CSS y JavaScript
vanilla. Se abre con datos móviles en un almacén, así que pesa lo mínimo.

Los datos viven en **Firebase Firestore**, una base de datos en la nube de Google. El
navegador habla directamente con Firestore usando el SDK web que se carga desde CDN, y se
queda escuchando los tres documentos con `onSnapshot`: cuando alguien guarda un cambio
desde otro móvil, Google lo empuja a todos los que están mirando y la pantalla se
actualiza sola.

**Se escuchan las tres listas a la vez, no solo la pestaña abierta.** El buscador y el
detector de repetidos las necesitan todas, y son tres documentos pequeños: cuesta
prácticamente lo mismo que escuchar uno. De regalo, cambiar de pestaña ya no espera a
Firestore, es instantáneo.

**Por qué no hay backend propio.** Un servidor intermedio aquí solo añadiría trabajo: otra
pieza que desplegar, que mantener, que se puede caer y que hay que pagar o vigilar. Como
la app no tiene lógica de negocio que proteger (es una lista de la compra) ni usuarios que
autenticar, el navegador puede hablar con la base de datos directamente. Firestore ya
resuelve el tiempo real, la persistencia y la concurrencia. Menos piezas, menos cosas que
se rompan.

### Modelo de datos

Una colección `checklists` con **un documento por sección**:

```
checklists/general
checklists/cocteleria
checklists/cocina
```

Y dentro de cada documento, todos los puntos en un solo array:

```js
{
  items: [
    {
      text: "3 botellas de Verdejo",
      done: true,
      cat: "bebidas",                      // bebidas | utensilios | otros
      sub: "vinos",                        // solo en bebidas; null en el resto
      author: "Selu",                      // quién lo apuntó
      createdAt: 1737800000000,
      history: [                           // se acumula, nunca se recorta
        { text: "Marcado por Jordan", at: 1737800100000 }
      ]
    }
  ],
  borrados: [                              // registro de lo que se ha quitado
    {
      text: "3 cajas de tónica",
      cat: "bebidas", sub: "refrescos",
      done: false,
      author: "Selu",                      // quién lo había apuntado
      history: [ /* el que tuviera el punto */ ],
      by: "Jordan",                        // quién lo borró
      at: 1737900000000
    }
  ]
}
```

`borrados` **sí se recorta**: se queda con los últimos 50 de cada lista. Es un registro
para mirar cuando falta algo, no un archivo histórico, y todo va en el mismo documento.
Los documentos de antes de que existiera no tienen el campo; se lee como lista vacía y no
pasa nada.

Los puntos apuntados antes de que existieran los filtros no tienen `cat` ni `sub`
guardados. No pasa nada: la app se los calcula al vuelo al pintarlos, **sin escribir en
Firestore**. Si se escribieran al abrir, cada móvil que entrase dispararía una escritura
de la lista entera sin que nadie haya tocado nada. La categoría solo se guarda cuando
alguien la cambia a mano o cuando se apunta un punto nuevo.

Está así a propósito: son listas de decenas de puntos, no de miles, y con todo en un mismo
documento cada guardado es **una sola escritura** y cada actualización en tiempo real
**una sola lectura**. Con subcolecciones se gastarían muchas más operaciones para nada.

Si un documento no existe la primera vez que se abre su pestaña, la app lo crea sola
(`general` con su lista inicial, las otras dos vacías).

---

## Cómo actualizar la app

1. Editar `index.html`.
2. `git commit`
3. `git push`

Vercel detecta el push a `main` y **redespliega solo** en unos segundos. No hay que entrar
al panel de Vercel para nada.

### Añadir o renombrar una sección

Todo está en el array `SECTIONS`, dentro de `index.html`:

```js
const SECTIONS = [
  { key: 'general', title: 'General', label: 'General', note: '(material y suministros generales del evento)' },
  ...
];
```

- `key` → el nombre del documento en Firestore. **Si lo cambias, la lista antigua deja de
  verse** (sigue guardada en Firestore bajo la clave vieja, pero la app mirará otra).
- `title` → el título grande de la pestaña.
- `label` → la etiqueta pequeña de debajo.
- `note` → el texto en cursiva bajo las pestañas.

Añadir una sección nueva es meter un objeto más al array. El documento se crea vacío la
primera vez que alguien abre esa pestaña; no hay que tocar nada en Firebase.

### Añadir o cambiar categorías

Hay **dos juegos de categorías** en `index.html`, `CATS_SALA` (para General y Coctelería) y
`CATS_COCINA`. Cada sección elige el suyo con la clave `cats` de `SECTIONS`
(`cats: 'sala'` o `cats: 'cocina'`):

```js
const CATS_COCINA = {
  genero:   { label: 'Género',   subs: { salsas: 'Salsas', charcuteria: 'Charcutería', congelados: 'Congelados', otros: 'Otros' } },
  maquinas: { label: 'Máquinas', subs: null },
  ...
};
```

Con meter una entrada más ya aparece sola en los filtros y en el desplegable de cada punto:
no hay que tocar nada más. `subs: null` significa que esa categoría no tiene subfiltros.
**Todos los juegos deben tener una categoría `otros`**, que es donde cae lo que no encaja.

Debajo están `REGLAS_SALA` y `REGLAS_COCINA`, las listas de palabras con las que se adivina
la categoría de lo que se apunta nuevo. **Se miran en orden y gana la primera que encaje**,
así que lo específico va arriba: en cocina, `menaje` va antes que `genero` para que
"Platos jamón" sea un plato y no charcutería, y `maquinas` va de las primeras para que
"jamonero" sea la máquina y no el jamón.

Las palabras se comparan **enteras**, no por trozos — por eso "colador" no cae en refrescos
por contener "cola", ni "salsa" en otros por contener "sal". Si añades una categoría nueva,
añádele también su regla o todo lo suyo caerá en *Otros*.

Si un punto tiene guardada una categoría que no existe en la pestaña donde se ve (por
ejemplo algo movido de General a Cocina, con `cat: "bebidas"`), la app la ignora y lo
reclasifica con las reglas de esa pestaña. No se rompe nada.

### Cómo decide la app que dos cosas son el mismo artículo

Está todo en el bloque *Motor de parecidos* de `index.html`, y no usa ninguna librería.
De cada texto se saca una lista de palabras y se compara palabra con palabra:

1. **Se tira lo que no es el artículo.** Números (`200 ud`, `3 cajas`), palabras de relleno
   (`de`, `para`, `cada`, en `RELLENO`) y los envases y medidas de `ENVASE`, que dicen
   cuánto y no qué: por eso *"4 cajas de agua"* y *"agua"* son lo mismo. Ojo con tocar
   `ENVASE`: **`bandeja` y `bolsa` no están ahí** aunque lo parezcan, porque en estas
   listas son artículos de pleno derecho.
2. **Se comparan por cómo suenan, no por cómo se escriben** (`fonetica()`). Se quitan los
   plurales y se juntan las confusiones de escribir deprisa en el móvil: z/s/c, b/v, ll/y,
   la h muda, qu/k, g/j. Así *"quezo"* = *"queso"* y *"balletas"* = *"bayetas"*. Lo que no
   se arregla así se compara por distancia de edición, perdonando poco más de una letra —
   y en palabras de menos de cinco letras no se perdona nada, porque *"sal"* y *"sol"* no
   son lo mismo.
3. **Cada palabra pesa lo que distingue** (`recalcularPesos()`). El peso no está escrito a
   mano: sale de contar en cuántos puntos de las tres listas aparece cada palabra. `salsa`
   y `biberón`, que salen en ocho puntos de la cocina, no dicen nada; `brie`, que sale una
   vez, es justo lo que separa un queso de otro. **Sin esto, los ocho "Biberón salsa X" de
   Jordan saldrían como repetidos entre sí**, que era el problema al montar esto.
4. Si **todo** lo que dice un punto está dentro del otro, se dan por parecidos aunque uno
   añada cosas: *"limones"* está entero dentro de *"Fruta: naranja y limón"*.

El resultado va de 0 a 1 y el corte está en `UMBRAL_PARECIDO` (0,6). Es el número a tocar
si algún día avisa de más o de menos: **subirlo** deja pasar cosas que sí eran lo mismo,
**bajarlo** empieza a emparejar *"Platos de café"* con *"Platos negros"*. Buscar es más
blando (`UMBRAL_BUSQUEDA`) porque lo que se teclea es un trozo, no un punto entero.

Los repetidos se agrupan en cadena: si A se parece a B y B a C, los tres van al mismo
montón aunque A y C no se parezcan tanto. Para un aviso es lo que interesa. Se recalculan
solo cuando cambian los datos, no en cada repintado.

---

## Firebase: configuración y reglas

- **Proyecto:** `nero-eventos`
- **Ubicación de Firestore:** `europe-west3` (Frankfurt) — es fija, no se puede cambiar.

Las credenciales (`firebaseConfig`) están escritas directamente en `index.html`. **No es un
descuido:** son claves públicas de cliente, Firebase las expone por diseño en el navegador
de cualquiera que abra la app y esconderlas no aporta nada. La seguridad real de un
proyecto Firebase vive en las reglas de Firestore, no en ocultar esas claves. Se dejan en
el código para que el repo se pueda clonar y desplegar sin configurar variables de entorno.

### ⚠️ Reglas de Firestore — hay que pegarlas antes de que caduque el modo de prueba

El proyecto se creó **en modo de prueba, y ese modo caduca a los 30 días** del alta. Cuando
caduque, Firestore empieza a rechazar toda lectura y escritura: **la app dejará de
funcionar de golpe** y saldrá "Error de conexión con Firebase".

Para evitarlo, ir a
[Firebase Console](https://console.firebase.google.com/project/nero-eventos/firestore/rules)
→ **Firestore Database** → pestaña **Reglas**, sustituir lo que haya por esto y pulsar
**Publicar**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /checklists/{document} {
      allow read, write: if true;
    }
  }
}
```

Esto abre lectura y escritura **solo** a la colección `checklists`, sin fecha de caducidad,
y deja cerrado el resto del proyecto.

### 🔓 Aviso importante: cualquiera con el link puede escribir

No hay login ni contraseña. **Cualquiera que tenga el link puede ver, añadir, editar y
borrar puntos de las tres listas.** El campo "Tu nombre" es solo para dejar constancia de
quién hizo cada cosa; no comprueba nada ni impide que alguien escriba otro nombre.

Es aceptable para lo que es: una lista de la compra de un evento entre compañeros, sin
datos personales ni sensibles, con un link que no se publica en ningún sitio indexable.
Pero conviene tenerlo claro: **no metáis ahí nada que no queráis que vea cualquiera a
quien le reenvíen el link** (datos de clientes, teléfonos, precios de proveedores,
cualquier cosa privada).

Si algún día hiciera falta cerrarlo, la vía es activar autenticación anónima o por enlace
en Firebase y endurecer las reglas — pero eso añade fricción, y la fricción es justo lo
que haría que el equipo dejara de usarlo.

---

## Despliegue

Repo: **https://github.com/garavitstudio/nero-eventos** (público).

Alojado en **Vercel**, plan Hobby (gratis), conectado a este repo de GitHub. Al ser un
sitio estático no lleva configuración de build (framework preset *Other*): Vercel sirve
`index.html` tal cual desde la raíz. Cada `git push` a `main` redespliega solo.

**El repo tiene que seguir siendo público.** El plan Hobby de Vercel no despliega desde
repos privados; con el repo en privado los builds no llegan a ejecutarse y la web se queda
servida con la versión anterior sin dar ningún error visible. Que sea público no expone
nada: lo único parecido a una credencial que hay en el código son las claves de cliente de
Firebase, que son públicas por diseño (ver arriba).

Cosas del plan gratis que conviene tener escritas:

- El plan Hobby es de **uso personal, no comercial**. Una checklist interna del equipo
  entra sin problema. Si esto llegara a ser algo que se vende o se factura, tocaría pasar a
  Pro.
- Solo hay **1 puesto de desarrollador**. Los compañeros **no necesitan cuenta de Vercel**,
  solo el link público.
- Los límites de uso (100 GB de transferencia al mes, etc.) son inalcanzables para una app
  de este tamaño.

---

## Estructura del repo

```
nero-eventos/
├── index.html                        ← la app entera: HTML, CSS y JS
├── assets/
│   └── logo-nero.png                 ← logo del restaurante (cabecera y favicon)
├── referencia/
│   └── checklist-compartida.html     ← prototipo original, solo consulta
├── README.md
└── .gitignore
```

**La carpeta se llama `assets/` y no `public/` a propósito.** Cuando Vercel no detecta
framework y existe un directorio `public/`, lo toma como raíz del sitio y publica solo su
contenido — es decir, serviría el logo y dejaría fuera el `index.html`, dando un 404 en la
página principal. Con cualquier otro nombre, Vercel sirve la raíz del repo, que es lo que
queremos. **No renombrar `assets/` a `public/`.**

`referencia/checklist-compartida.html` es el prototipo del que salió todo esto. Se guarda
como referencia histórica; **no se usa y no hay que tocarlo**. La app es `index.html`.
