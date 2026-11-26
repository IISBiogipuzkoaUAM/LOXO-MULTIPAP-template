# Cómo usar esta plantilla

Esta plantilla deja el repositorio listo para que cada *release* se archive en Zenodo con los metadatos correctos, dentro de la comunidad del proyecto y vinculada a la financiación.

## 1. Crear tu repositorio

1. En GitHub, abre el repositorio plantilla y pulsa **Use this template → Create a new repository**.
2. Elige la organización del proyecto, ponle nombre y márcalo como **Public** (Zenodo solo archiva repos públicos).

## 2. Rellenar los ficheros (5 minutos)

| Fichero | Qué cambiar |
|---|---|
| `README.md` | Borra el bloque de instrucciones y sustituye todo lo que va entre `[CORCHETES]`. |
| `.zenodo.json` | Parte del título tras «LOXO-MULTIPAP –», **primer párrafo** de la descripción (qué hace el software), autores (nombre, afiliación, ORCID), licencia y palabras clave. **No cambies** `communities` ni el párrafo de financiación. |
| `CITATION.cff` | Mismo título y autores que en `.zenodo.json`. |
| `LICENSE` | Solo si tu código necesita una licencia distinta de la del proyecto (consúltalo antes). Cambia también `license` en `.zenodo.json` y `CITATION.cff`. |
| `data/raw/README.md` | Lista las fuentes de los datos de entrada. |

Notas:

- Si hay `.zenodo.json`, Zenodo usa solo ese fichero e ignora `CITATION.cff`. `CITATION.cff` sirve para el botón *Cite this repository* de GitHub. Mantén los dos coherentes.
- La financiación (ISCIII) va en el párrafo final de la descripción. Tras la primera release, comprueba en Zenodo que el campo *Funding* está vinculado; si no, añádelo a mano (Edit).
- `data/processed/` está excluido de git por defecto: nunca subas datos personales o de salud individuales a un repositorio público.
- Borra las carpetas que no uses (`R/` o `src/`).

## 3. Entorno reproducible

- **R**: ejecuta `renv::init()` al empezar y `renv::snapshot()` antes de cada release. Sube `renv.lock`, `renv/activate.R` y `.Rprofile`.
- **Python**: `conda env export --from-history > environment.yml` (o un `requirements.txt` con versiones fijadas).

## 4. Activar Zenodo (una sola vez por repositorio)

1. Entra en Zenodo con **Log in with GitHub**.
2. Ve a https://zenodo.org/account/settings/github/ y activa el repositorio (**On**).
3. Si el repo es de una organización y no aparece, pide a un owner de la organización que apruebe la app de Zenodo.

## 5. Publicar una versión

1. Actualiza el fichero de entorno y `version` / `date-released` en `CITATION.cff`.
2. En GitHub: **Releases → Draft a new release**, etiqueta `vX.Y.Z`, describe los cambios y publica.
3. Zenodo crea el registro (o una nueva versión del existente) y asigna DOI en unos minutos.
4. Tras la **primera** release: copia el *concept DOI* al badge del `README.md` y a `doi` en `CITATION.cff`.

Dudas: escribe a los responsables de datos antes de publicar:

- Jone Renteria – jone.renteriaaguirregabiria@bio-gipuzkoa.eus
- Claudia Iglesias-Carabias – claudia.icarabias@urjc.es
- Alejandro Santos-Mejías – asantosm@ext.aragon.es
