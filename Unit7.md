# Experiencia de aprendizaje 7: Gráficas

## **Introducción**

En esta unidad vas a interactuar con un dispositivo del computador que te permite pintar en pantalla a altas velocidades. Este dispositivo es la tarjeta gráfica o Graphics Processing Unit (GPU). La GPU es un dispositivo que se encarga de procesar y enviar señales de video a la pantalla del computador. Es un dispositivo especializado en procesar gráficos y video. Aunque actualmente también se usa, y mucho, para trabajar con inteligencia artificial y aprendizaje profundo.

La idea de esta experiencia de aprendizaje es que te familiarices con los conceptos básicos de la programación de la GPU, es decir, que experimentes a nivel introductorio con ***shaders*** y que además veas cómo comunicar la CPU con la GPU para realizar aplicaciones interactivas.

## **Investigación**

Para la fase de investigación te vas a concentrar en el tutorial Introducing Shaders hecho por Lucasz Karluk, Joshua Noble y Jordi Puig. Este es un tutorial oficial del material de aprendizaje de openframeworks. Ten presente que todos los ejemplos que se presentan en este tutorial están la carpeta examples/shaders numerados del 01 al 09.

### Actividad 1

</aside>
⚠️

**Advertencia**
¿Cómo sacar el máximo de los videos educativos?

- Mira el video una vez.
- Luego, de memoria, trata de listar los conceptos fundamentales y hacer un resumen de estos. Puedes también hacer diagramas o mapas conceptuales. Trata de conectar estos con conceptos que ya conoces.
- Observa por segunda vez el video y compara tus notas con lo que el video presenta.
- Busca material para realizar experimentos donde puedas ver aplicados los conceptos que has aprendido. Los experimentos tienen otra bondad, y es que te permiten hacer la pregunta mágica: ¿Qué pasa si…?
- ¿Qué pasa si cambio este parámetro? ¿Qué pasa si cambio este otro? ¿Qué pasa si …? Cada pregunta te propondrá que generes una hipótesis y que la pongas a prueba. Esto es lo que se llama el método científico. Y es una de las mejores maneras de aprender.
- Si algún experimento no genera el resultado que esperabas, no te preocupes. Todo lo contrario, es un motivo para celebrar. Has encontrado algo nuevo. Tienes una oportunidad de aprender algo nuevo.

</aside>

Ya conoces cómo funciona una CPU, ahora es momento de aprender cómo funciona una GPU. Mira este [**video**](https://youtu.be/h9Z4oGN89MU?si=QBevEhhiFn1P5lE3) y tendrás una buena idea.

Ahora dale una mirada a este otro [**video](https://youtu.be/C8YtdC8mxTU?si=710jq1R2Z88m4jtz)** donde podrás ver, un poco más profundo, cómo funciona una GPU.

Te voy a plantear algunas preguntas para que reflexiones sobre lo que acabas de ver. Recuerda que puedes conversar con ChatGPT para profundizar y aclarar tus dudas, pero antes de pedirle una respuesta intenta responderlas por ti mismo y luego compara tus respuestas con las de ChatGPT. Si ves que hay diferencias, intenta entender por qué hay diferencias.

- ¿Qué son los vértices?
- ¿Con qué figura geométrica se dibuja en 3D?
- ¿Qué es un shader?
- ¿Cómo se le llaman a los grupos de píxeles de un mismo triángulo?
- ¿Qué es un fragment shader?
- ¿Qué es un vertex shader?
- ¿Al proceso de determinar qué pixels del display va a cubrir cada triángulo de una mesh se le llama?
- ¿Qué es el render pipeline?
- ¿Hay alguna diferencia entre aplicar un color a una superficie de una mesh o aplicar una textura?
- ¿Cuál es la diferencia entre una textura y un material?
- ¿Qué transformaciones se requieren para mover un vértice del 3D world al View Screen?
- ¿Al proceso de convertir los triángulos en fragmentos se le llama?
- ¿Qué es el framebuffer?
- ¿Para qué se usa el Z-buffer o depth buffer en el render pipeline?

Luego de ver el segundo video entiendes por qué la GPU tiene que funcionar tan rápido y de manera paralela. ¿Por qué?

¿Te gustaron los videos? Hay uno más que te podría llamar la atención. Te propongo que sigas con las demás actividades, pero si tienes tiempo y ganas, mira [este](https://youtu.be/iOlehM5kNSk?si=yBRNVjRU3lULY0hr) video más adelante.

### Actividad 2

Comienza realizando la lectura de la introducción del tutorial [Introducing Shaders](https://openframeworks.cc/ofBook/chapters/shaders.html). Realiza la sección Your First Shader, pero antes de ejecutar el código, realiza un pequeño experimento. Modifica ligeramente el método draw:

```cpp
void ofApp::draw(){
    ofSetColor(255);

    //shader.begin();

    ofDrawRectangle(0, 0, ofGetWidth(), ofGetHeight());

    //shader.end();
}
```

Observa la salida.

Ahora ejecuta el código original. Analiza los resultados y responde:

- ¿Cómo funciona?
- ¿Qué resultados obtuviste?
- ¿Estás usando un vertex shader?
- ¿Estás usando un fragment shader?
- Analiza el código de los shaders. ¿Qué hace cada uno?

### Actividad 3

Ahora vas a pasar información personalizada de tu programa a los shaders. Vas a leer con detenimiento el tutorial Adding Uniforms.

- ¿Qué es un uniform?
- ¿Cómo funciona el código de aplicación, los shaders y cómo se comunican estos?

Modifica el código de la actividad para cambiar el color de cada uno de los píxeles de la pantalla personalizando el fragment shader.

### Actividad 4

Vas a realizar la última actividad de esta experiencia de aprendizaje. Yo sé que quieres seguir haciendo más, pero tenemos un tiempo muy limitado.

Analiza el ejemplo Adding some interactivity.

- ¿Qué hace el código del ejemplo?
- ¿Cómo funciona el código de aplicación, los shaders y cómo se comunican estos?
- Realiza modificaciones a ofApp.cpp y al vertex shader para conseguir otros comportamientos.
- Realiza modificaciones al fragment shader para conseguir otros comportamientos.

## **Reto**

Con lo que aprendiste en esta unidad vas a realizar una aplicación interactiva que utilice shaders.

</aside>
⚠️

**Advertencia**
No uses ChatGPT esta vez.
Con los conocimientos que has adquirido en esta unidad, realiza la aplicación interactiva que se describe a continuación. No uses ChatGPT para realizar esta actividad. Regálate la oportunidad de aplicar lo que has aprendido. Experimenta y diviértete.

</aside>

### Requisitos

- Utilizando **C++** y **openFrameworks**.
- Modifica los vértices de una malla en el vertex shader.
- Modifica los colores de los fragmentos en el fragment shader.

### Evidencias de los resultados de aprendizaje

</aside>
⚠️

**Advertencia**
**MUY IMPORTANTE**
¿Recuerdas los resultados de aprendizaje específicos (RAE) de este curso?

- RAE1: construyo aplicaciones interactivas aplicando patrones y estrategias que permitan alcanzar los requisitos funcionales y no funcionales establecidos. Se espera que llegues a un nivel resolutivo.
- RAE2: aplico pruebas de las partes y del todo de un software siguiendo metodologías, técnicas y estándares de la industria para garantizar el correcto funcionamiento de las aplicaciones. Se espera que llegues a un nivel autónomo.

</aside>

## **El RAE1 lo evidenciarás con:**

- La construcción de la aplicación que propone el reto.
- Vas a explicar detalladamente cómo funciona la aplicación.
- El código fuente de tu aplicación.
- 📽️ Un ENLACE a un video que muestre en funcionamiento la aplicación.

## El RAE2 lo evidenciarás con

- Explica y muestra cómo probaste la aplicación en ofApp.cpp.
- Explica y muestra cómo probaste el vertex shader.
- Explica y muestra cómo probaste el fragment shader.
- Explica y muestra cómo probaste toda la aplicación completa.
