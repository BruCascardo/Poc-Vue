
# Currency Converter (Conversor de Divisas)

Este proyecto es un conversor de divisas simple desarrollado en **Vue.js**. Permite convertir entre USD (dólares estadounidenses) y PESOS con tasas de conversión predefinidas. Es ideal como un ejemplo básico de cómo implementar una aplicación de conversión de moneda utilizando el framework Vue.

## Características

- Conversión entre USD y PESOS.
- Tasas de conversión predefinidas (simuladas).
- Interfaz simple y fácil de usar.
  
## Requisitos previos

Si no tienes `Vue CLI` instalado, puedes hacerlo ejecutando el siguiente comando en tu terminal:

```bash
npm install -g @vue/cli
```

## Instalación

Sigue estos pasos para instalar y ejecutar el proyecto en tu máquina local:

1. **Clonar el repositorio:**

   ```bash
   git clone https://github.com/BruCascardo/Poc-Vue
   cd currency-converter
   ```

2. **Instalar dependencias:**

   Antes de ejecutar el proyecto, necesitas instalar todas las dependencias que utiliza. Para hacerlo, ejecuta el siguiente comando:

   ```bash
   npm install
   ```

3. **Iniciar el servidor de desarrollo:**

   Una vez instaladas las dependencias, puedes iniciar el servidor de desarrollo con el siguiente comando:

   ```bash
   npm run serve
   ```

4. **Acceder a la aplicación:**

   Después de ejecutar el comando anterior, puedes abrir tu navegador y acceder a la aplicación en:

   ```
   http://localhost:8080
   ```

   La aplicación debería mostrarse correctamente y podrás usar el conversor de divisas.

## Uso

1. Introduce la cantidad que deseas convertir.
2. Selecciona la moneda de origen (USD o PESOS).
3. Selecciona la moneda de destino.
4. Haz clic en el botón "Convert" para ver el resultado de la conversión.


## Notas

- Las tasas de conversión están definidas de manera estática en el código para simplificar el ejemplo. En un entorno real, podrías utilizar una API como **Exchangerate-API** o **Fixer.io** para obtener tasas de cambio actualizadas.
- Este proyecto utiliza un servidor local de desarrollo para mostrar la aplicación en tiempo real y facilitar el desarrollo.
