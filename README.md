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

Lo único obligatorio es **poner tu nombre** arriba antes de tocar nada. Sirve para que
quede constancia de quién apunta, quién marca y quién cambia las cantidades. El nombre se
queda guardado en ese móvil, así que solo hay que escribirlo la primera vez.

Tres pestañas independientes, cada una con su propia lista:

| Pestaña | Para qué |
|---|---|
| **General** | Material y suministros generales del evento |
| **Coctelería** (José Alexis) | Lo que necesite la barra |
| **Cocina** (Jordan) | Lo que necesite la cocina |

Qué se puede hacer con cada punto de la lista:

- **Marcarlo / desmarcarlo** con el círculo de la izquierda. El texto se tacha, no
  desaparece.
- **Editarlo** tocando directamente el texto. Es para cuando cambia la cantidad sobre la
  marcha ("tres cajas" → "cinco cajas").
- **Borrarlo** con la ✕ de la derecha.

Debajo de cada punto queda escrito quién lo apuntó y el historial completo de cambios:
quién lo marcó, quién lo desmarcó y quién cambió qué por qué. **Ese historial no se borra
nunca**, es a propósito.

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
queda escuchando el documento de la sección abierta con `onSnapshot`: cuando alguien
guarda un cambio desde otro móvil, Google lo empuja a todos los que están mirando esa
misma lista y la pantalla se actualiza sola.

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
  ]
}
```

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
