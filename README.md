# Uv y Zensical

Guía para instalar `uv`, configurar **Zensical**, levantar el servidor de desarrollo y aprovechar la recarga en tiempo real.

---

## Paso 1: Instalar `uv`

`uv` es un gestor de paquetes y entornos de Python, abre tu terminal y ejecuta:

```
curl -sSf https://astral.sh/uv/install.sh | sh
```

> **Nota:** Tras completar la instalación, cierra y vuelve a abrir tu terminal para asegurarte de que el comando `uv` está disponible.

**Comprobar la ruta del ejecutable:**
   
```
which uv
```
*(Debería apuntar habitualmente a `~/.cargo/bin/uv` o `~/.local/bin/uv`)*

---

## Paso 2: Crear la carpeta del proyecto e inicializarlo

Crea un directorio para tu proyecto y entra en él:

```
mkdir mi-proyecto-docs
cd mi-proyecto-docs
```

A continuación, inicializa el proyecto con `uv`:

```
uv init
```

---

## Paso 3: Añadir la dependencia de Zensical

Instala **Zensical** dentro de tu proyecto mediante `uv`:

```
uv add zensical
```

`uv` gestionará automáticamente la descarga e instalación del paquete en el entorno virtual del proyecto.

> **Nota:** Para asegurarte de que Zensical solo se instale como herramienta de desarrollo (y no en el entorno de producción), utiliza la bandera `--dev`:

```
uv add --dev zensical
```

*Esto registrará `zensical` bajo el bloque `[tool.uv.dev-dependencies]` o `[dependency-groups]` en tu archivo `pyproject.toml`.*

---

## Paso 4: Levantar el servidor local

Para compilar la documentación y poner en marcha el servidor web de desarrollo, ejecuta:

```
uv run zensical serve
```

Verás una salida en la terminal indicando la dirección URL local, normalmente:

http://127.0.0.1:8000

Abre esa URL en tu navegador preferido para ver el sitio web generado.

---

## Paso 5: Edición y actualización en tiempo real (Live Reload)

El servidor de desarrollo de Zensical cuenta con un motor de recarga en tiempo real:

1. **Abre y edita:** Modifica cualquier archivo `.md` en tu editor de código.
2. **Guarda los cambios:** Al guardar el archivo, el servidor detectará la modificación de inmediato.
3. **Sincronización instantánea:** La página web abierta en el navegador reflejará los cambios automáticamente sin necesidad de recargar manualmente la página.

<br>
<br>

# Como usar UV sin recargar el terminal

Para evitar reiniciar el terminal, existen dos opciones:

1. **Recargar el archivo de configuración en la sesión actual**

```bash
# Bash
source ~/.bashrc

#Zsh
source ~/.zshrc

# Fish
source ~/.config/fish/config.fish
```

Esto vuelve a ejecutar el archivo que el instalador moddificó, sin cerrar y abrir la terminal.

2. **Añadir el PATH manualmente en la sesión actual**

`uv` suele instalarse en `~/.cargo/bin` o `~/.local/bin`:

```bash
export PATH="$HOME/.local/bin:$PATH" 
```

(o `$HOME/.cargo/bin`, según dónde lo haya puesto el instalador - el propio script suele indicarlo al terminar)
