# React Router

## Especificación rutas
Cada vez que se cree una vista, la ruta de esta se debe especificar en `App.tsx` a través de  `<Route>`

Debemos de importar la vista creada, por ejemplo:

```import Home from './Home'; ```

Y luego establecer el path:

```<Route path="/" element={<Home />} />```

Llevando esto a nuestra aplicación tenemos:

```
import React from 'react';
import { BrowserRouter, Route, Routes } from 'react-router-dom';
import Navbar from './components/Navbar';
import InicioSesion from './components/InicioSesion';
import NotFound from './components/NotFound';
import ClientView from './ClientView';
import './App.css';

function App() {
  return (
    <BrowserRouter>
      <div className="App">
        <Navbar />
        <div className="content">
          <Routes>
            <Route path="/" element={<ClientView />} />
            <Route path="/login" element={<InicioSesion />} />
            <Route path="*" element={<NotFound />} />
          </Routes>
        </div>
      </div>
    </BrowserRouter>
  );
}

export default App;

```

`<BrowserRouter>` debe envolver toda la aplicación para que los demás componentes funcionen de forma correcta

## Creación ruta 404

Notemos que en nuestro ejemplo anterior (nuestra app), tenemos:

`import NotFound from './components/NotFound';`

`<Route path="*" element={<NotFound />} />`

Esto significa que cada vez que nuestra aplicación no encuentre la ruta especificada, se cargará la vista de `<NotFound />`.

Y en particular en `./components/NotFound.tsx` tenemos: 


```
import React from 'react';
import { Link } from 'react-router-dom';

function NotFound() {
  return (
    <div>
      <h1>¡Ups! Pareces estar perdido.</h1>
      <p>Aquí tienes algunos enlaces útiles:</p>
      <Link to="/">Inicio</Link>
      <p> </p>
      <Link to="/login">Iniciar sesión</Link>
    </div>
  );
}

export default NotFound;
```
## Utilización `<Link>` para la navegación

`<Link>` permite realizar cambios de rutas sin recargar la página. Según la guía oficial de React Router, podemos definir `<Link>` como:

Un `<Link>` es un elemento que permite al usuario navegar a otra página haciendo clic o tocándola. En `react-router-dom`, un `<Link>` representa un elemento `<a>` accesible con un href real que apunta al recurso al que se vincula. Esto significa que cosas como hacer clic con el botón derecho en un `<Link>` funcionan como cabría esperar. Puede usar `<Link reloadDocument>` para omitir el enrutamiento del lado del cliente y dejar que el navegador maneje la transición normalmente (como si fuera un `<a href>`).

Ahora podemos utilizar las rutas ya especificadas en el <BrowserRouter>, para navegar entre ellas con <Link>. Como podemos ver en `./components/NotFound.tsx`:

`<Link to="/">Inicio</Link>`

`<Link to="/login">Iniciar sesión</Link>`

### `<Link>` e imágenes:

Clickeando la imagen nos lleva a la ruta `/` , la cual especificamos en `App.tsx`:

```
<Link to="/">
  <img src={plaglabsLogo} className="logo react" alt="React logo" />
</Link>
```
### `<Link>` y botones:
Clickeando el boton nos lleva a la ruta `/` , la cual especificamos en `App.tsx`:
```
<Link to="/">
   <button>
        Click Me!
   </button>
</Link>
```

## Links Utiles
- https://www.makeuseof.com/react-router-404-page-create/
- https://reactrouter.com/en/main/start/tutorial
- https://bobbyhadz.com/blog/react-image-link
- https://stackoverflow.com/questions/72246368/link-to-in-my-react-router-is-not-working
