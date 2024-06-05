---
layout: default
title: Scoping Guide
nav_order: 4
parent: Communicating Findings
---

# Guía de alcance del proyecto de ciencia de datos

**Recursos en esta publicación:** Hoja de trabajo en blanco sobre el alcance del proyecto, presentación sobre el alcance , plan de estudios de muestra para un taller sobre el alcance 

**Cómo utilizar esta guía:** Esta Guía de alcance complementa la Hoja de trabajo de alcance del proyecto . Para obtener un breve recorrido, consulte la Hoja de trabajo en blanco para determinar el alcance del proyecto . Para obtener más detalles sobre cualquier sección de la hoja de trabajo, utilice esta guía.

En los últimos años, Data Science for Social Good ha trabajado en más de 100 proyectos de ciencia de datos y una lección (como era de esperar) que hemos aprendido durante esos años es que es fundamental definir bien el alcance de estos proyectos desde el principio. 

Hay muchas organizaciones (agencias gubernamentales, organizaciones sin fines de lucro, empresas sociales, corporaciones) que trabajan en problemas importantes que pueden tener un gran impacto en la sociedad. También hay muchas personas talentosas, apasionadas e inteligentes con habilidades en ciencia de datos que pueden ayudarlos a abordar esos problemas. Sin embargo, cuando estos dos grupos de personas se unen, los resultados a menudo son contradictorios debido a los desafíos asociados con la formulación de un proyecto con un alcance bien definido. Hemos descubierto que es necesario contar con personas que puedan mediar entre los dos grupos y formular un problema que sea a la vez solucionable e impactante. Es incluso mejor si ambos grupos tienen estas habilidades de alcance para poder trabajar juntos de manera más efectiva. 

Después de analizar el alcance de cientos de proyectos en los últimos años, hemos aprendido varias lecciones sobre el alcance de los proyectos que queríamos compartir con la comunidad más amplia de ciencia de datos para el bien social. Nos encantaría recibir comentarios y opiniones sobre nuestro enfoque y que la gente nos ayude a mejorarlo. 

Aunque esto está escrito específicamente para beneficiar a las personas que analizan el alcance de los proyectos de ciencia de datos para el bien social, las lecciones aquí se generalizan también a proyectos socialmente neutrales (y desafortunadamente, socialmente malvados). De hecho, mucho de esto se basa en las lecciones que hemos aprendido al trabajar en proyectos de ciencia de datos en el mundo empresarial en nuestras vidas laborales anteriores.

## Criterios de evaluación inicial

Asumiremos aquí que ya hemos repasado los criterios básicos para hacer ciencia de datos para proyectos de bien social:

1. Impactante : el problema que estamos resolviendo es real, importante y tiene impacto social.
2. Soluble : los datos pueden desempeñar un papel en la solución del problema y la organización tiene acceso a los datos correctos (consulte nuestro marco de madurez de datos para ayudarlo a evaluar si tiene los datos correctos).
3. Accionable : la organización ha priorizado este problema, está lista para tomar acciones basadas en el trabajo y está dispuesta a comprometer recursos para validarlo e implementarlo. (consulte nuestro marco de madurez organizacional para evaluar dónde se encuentra).

## Descripción general del alcance

Una vez que hemos pasado por el proceso de selección inicial, comenzamos el proceso de determinación del alcance. Hay muchos enfoques para abordar un problema. Nos centramos en proyectos que son viables y conducen a resultados sociales positivos tangibles. El enfoque que describimos a continuación nos ha funcionado, pero ciertamente no creemos que sea la única forma de alcanzar un proyecto exitoso. Háganos saber si tiene enfoques alternativos que utilice y de los que podamos beneficiarnos. Como siempre, el proceso de determinación del alcance es bastante iterativo y el alcance se perfecciona tanto durante el proceso de determinación del alcance como durante el proyecto.

**¿Quién necesita estar involucrado?** Los participantes ideales en el proceso de determinación del alcance incluyen varias partes interesadas en el proyecto, incluidas personas que comprenden el problema empresarial/político, personas que comprenden qué datos están disponibles, personas que consumirán los resultados del sistema o tomarán medidas al utilizarlos, y las personas que se verá afectado por ello.

- **Paso 0: Comprensión del problema** : ¿cuál es el problema? ¿A quién afecta y en qué medida? ¿Cómo se está resolviendo hoy y cuáles son algunas de las lagunas? 
- **Paso 1: Metas** – ¿Cuáles son las metas del proyecto? ¿Cómo sabremos si nuestro proyecto tiene éxito? 
- **Paso 2: Acciones** – ¿Qué acciones o intervenciones informará este trabajo? 
- **Paso 3: Datos** : ¿a qué datos tiene acceso internamente? ¿Qué datos necesitas? ¿Qué puedes aumentar de fuentes externas y/o públicas? 
- **Paso 4: Análisis** : ¿Qué análisis es necesario realizar? ¿Implica descripción, detección, predicción o cambio de comportamiento? ¿Cómo se validará el análisis? 
- **Consideraciones éticas** : ¿Cuáles son los problemas de privacidad, transparencia, discriminación/equidad y responsabilidad en torno a este proyecto y cómo los abordará? 
- **Consideraciones adicionales**: ¿Cómo implementará su análisis como un nuevo sistema para que pueda actualizarse e integrarse en las operaciones de la organización? ¿Cómo evaluará el nuevo sistema en el campo para asegurarse de que cumpla sus objetivos? ¿Cómo supervisará su sistema para asegurarse de que siga funcionando bien con el tiempo?

El proceso de determinación del alcance es iterativo y no estrictamente lineal. Si bien comprender el problema y definir las metas de los proyectos debe ser anterior a la identificación de acciones, el proceso de identificación de acciones puede ayudar a discernir si una meta es factible y debe redefinirse. De manera similar, evaluar los datos disponibles para el proyecto puede llevarnos a repensar qué problemas, objetivos y acciones pueden ser informados por un proyecto de ciencia de datos. Nuestro análisis puede llevarnos a repensar nuestro problema y nuestros objetivos y comenzar de nuevo el proceso de determinación del alcance. Entonces, si bien cada paso sigue al anterior, debemos tomar cada paso como una oportunidad para evaluar los pasos anteriores.

En todo momento, la ética debe ser el centro de nuestro proceso de determinación de alcance. Las cuestiones éticas deben considerarse en cada fase del alcance y la ejecución del proyecto, en lugar de considerarse como un “paso” discreto en ese proceso. Desarrollar una comprensión clara y explícita de tus objetivos a este respecto es fundamental para hacerlo bien. Fundamentalmente, la integración de consideraciones éticas en el proyecto no debe ser una ocurrencia tardía ni una carga, sino más bien un área de enfoque crítica y continua que involucre a todas las partes interesadas, especialmente a las personas que se verán afectadas por este sistema.

## Paso 0: comprender el problema

Antes de comenzar a evaluar el alcance del proyecto, debemos asegurarnos de comprender el **problema** y su **impacto** . El problema debe ser una prioridad para la organización que pueda abordarse utilizando los datos que la organización tiene o puede acceder. Si el problema no es una prioridad, entonces ni siquiera un modelo bien diseñado ayudará a resolverlo porque la organización carecerá de la motivación para actuar sobre la información resultante del análisis. 

Para empezar, es importante comprender el alcance del problema. Primero pedimos a las organizaciones que describan el problema que enfrentan, incluyendo quién o qué se ve afectado por el problema, cuántos y en qué medida (es decir, la magnitud del problema). Por ejemplo, un distrito escolar puede estar preocupado por las bajas tasas de graduación de la escuela secundaria. Deberían poder decirnos quién está afectado, tal vez estudiantes de bajos ingresos o estudiantes que de otro modo están en riesgo. También deberían poder decirnos la magnitud del problema: por ejemplo, que menos del 90% de los estudiantes de secundaria se gradúan a tiempo y menos de la mitad de los estudiantes en riesgo. 

Luego le pedimos a la organización que explique por qué el problema es una prioridad ahora y cómo lo han estado abordando. Comprender cómo la organización ha abordado el problema puede ayudarnos a identificar formas en que el análisis de datos puede informar las acciones de la organización para lograr sus objetivos. Por ejemplo, un distrito escolar puede estar preocupado por las tasas de graduación de la escuela secundaria porque recientemente descubrió que eran particularmente bajas entre los estudiantes en riesgo. Es posible que el distrito escolar esté inscribiendo a estudiantes en riesgo en programas de tutoría después de la escuela que ayuden a reforzar el aprendizaje en la escuela. Si el espacio en los programas extracurriculares es limitado, entonces el análisis correcto podría ayudar al distrito escolar a priorizar la inscripción de los estudiantes que probablemente no se gradúen a tiempo. 

Finalmente, es importante identificar los grupos o partes interesadas dentro y fuera de su organización que deben participar en el alcance y la implementación del proyecto. Normalmente, los proyectos de ciencia de datos necesitan la participación de las partes interesadas dentro de su organización, como formuladores de políticas, administradores, propietarios de datos, propietarios de infraestructura de TI y las personas que intervendrán, como los trabajadores de la salud. Los proyectos también suelen requerir la participación de personas y grupos externos a su organización, como grupos comunitarios que se verán afectados por este trabajo. Por ejemplo, un distrito escolar que esté analizando el alcance de un proyecto de ciencia de datos que identifique a los estudiantes que corren el riesgo de no graduarse de la escuela secundaria querrá involucrar a los responsables políticos de alto nivel, así como a los trabajadores de datos y TI, desde el principio de su planificación. También querrán involucrar a los administradores escolares, maestros y trabajadores del programa de tutoría para ayudar a comprender el problema y determinar el alcance del proyecto. El distrito también querrá involucrar a la junta escolar y a los padres de los estudiantes que probablemente se verán afectados por el proyecto, especialmente en las comunidades más afectadas por las bajas tasas de graduación.

Una vez que se comprende adecuadamente el problema, podemos comenzar a definir los objetivos de la organización. 

## Paso 1: Definir los objetivos
2
El objetivo aquí es tomar el **resultado** que estamos tratando de lograr y convertirlo en una meta que sea **mensurable y alcanzable** . Este es el paso más crítico en el proceso de determinación del alcance. En el contexto de nuestros proyectos, una meta es un objetivo o resultado concreto, específico y medible que la organización logrará al abordar el problema. A menudo nos encontramos con esfuerzos en los que una organización definirá el objetivo de su proyecto como la creación de una solución técnica, como un modelo predictivo, un panel o un mapa. **Sostenemos que la solución técnica (modelo, panel, mapa) no es en sí misma el objetivo de un proyecto de ciencia de datos. Más bien, el objetivo del proyecto debe ser resolver alguna política o problema operativo que afecte la misión de la organización.** La creación de una solución de ciencia de datos puede (y si se hace correctamente, debería) ayudarle a alcanzar el objetivo que persigue. 

La mayoría de los proyectos comienzan con un objetivo muy vago y abstracto (digamos, mejorar la educación), se vuelven un poco más concretos (aumentar el porcentaje de estudiantes que se graduarán a tiempo) y siguen perfeccionándose hasta que el objetivo es concreto, inequívoco y logra el objetivo. objetivos sociales de la organización. Por ejemplo, “mejorar la educación” es demasiado abstracto y vago para ser el objetivo de un proyecto específico de ciencia de datos, mientras que “aumentar el número de estudiantes que se gradúan a tiempo de la escuela secundaria” es un objetivo más apropiado. Este paso suele ser difícil porque muchas organizaciones no han definido explícitamente objetivos analíticos concretos para muchos de los problemas que están abordando. A veces, estos objetivos existen pero están implícitos en la mente de las personas dentro de la organización. Otras veces, hay varios objetivos que diferentes partes de la organización intentan alcanzar. 

Un enfoque que encontramos útil para definir objetivos es relacionarlo directamente con el problema que hemos identificado y, por lo general, mejorar/maximizar/aumentar o disminuir/mitigar/reducir un resultado o métrica relevante (por ejemplo, aumentar el porcentaje de estudiantes de secundaria que se gradúan). a tiempo) que queremos cambiar.

A menudo tendremos objetivos (posiblemente) contradictorios en torno a la eficiencia (por ejemplo, ayudar al mayor número de personas necesitadas con recursos limitados), la eficacia (por ejemplo, maximizar la mejora total en los resultados para las personas a las que ayuda) y la equidad (por ejemplo, asignar recursos entre grupos). para lograr resultados equitativos). No sólo debemos definirlos explícitamente durante el proceso de determinación del alcance, sino también intentar priorizarlos en esta etapa.

Por lo general, las metas también incluyen limitaciones. Las limitaciones suelen ser las que hacen necesario un proyecto de ciencia de datos. Por ejemplo, si una agencia de salud pública pudiera inspeccionar todas las propiedades de alquiler en la ciudad en busca de violaciones del código de vivienda, probablemente lo haría. Sin embargo, puede haber una limitación en la cantidad de propiedades que una agencia puede inspeccionar dentro de un período determinado, por lo que es posible que desee priorizar aquellas que tienen más probabilidades de ser inseguras para vivir. Un programa preventivo de salud pública podría querer que su objetivo sea minimizar el número de visitas no planificadas a la sala de emergencias (ER). Un enfoque trivial (y malvado) para lograrlo sería cerrar todas las salas de emergencia, lo que daría como resultado cero visitas. Agregar una restricción que requiera que la solución mejore los resultados de salud, y no solo reduzca las visitas a emergencias, nos ayudará a identificar soluciones que tengan el impacto social deseado. 

Otras limitaciones típicas relacionadas con los objetivos son la limitación de presupuesto, personal y/o tiempo; restricciones legales o falta de voluntad política; o falta de licencia social. 

Tomemos algunos problemas de impacto social y veamos cómo podemos definir los objetivos.

**Ejemplo 1: Envenenamiento por plomo:** En 2014, trabajamos con el Departamento de Salud Pública de Chicago para reducir las tasas de envenenamiento por plomo entre los niños de Chicago. El objetivo inicial era reducir el envenenamiento por plomo aumentando la eficacia de sus limitadas inspecciones de peligros de plomo. Una forma de lograr ese objetivo sería centrar las inspecciones en hogares que probablemente tengan riesgos de plomo. Aunque útil, este enfoque no lograría su objetivo real, que era evitar que los niños sufrieran envenenamiento por plomo. Encontrar una casa con peligros de plomo y remediarla solo es beneficioso si existe una alta probabilidad de que haya un niño en la casa (actualmente o en el futuro) que probablemente quede expuesto al plomo (y desarrolle envenenamiento por plomo). La siguiente iteración del objetivo fue aumentar la cantidad de inspecciones que encuentran peligros de plomo en hogares donde hay un niño en riesgo (antes de que el niño quede expuesto al plomo). Finalmente, llegamos al objetivo final: reducir la cantidad de niños que sufrirán envenenamiento por plomo en el futuro debido a los peligros del plomo en su residencia actual al 1) identificar qué niños tienen un alto riesgo de envenenamiento por plomo en el futuro y luego 2) dirigiendo intervenciones en los hogares de esos niños para eliminar los peligros del plomo.

**Ejemplo 2: Graduación a tiempo de la escuela secundaria:** Uno de los desafíos que enfrentan las escuelas hoy en día es ayudar a sus estudiantes a graduarse a tiempo. Están interesados ​​en identificar a los estudiantes que corren el riesgo de no graduarse a tiempo y necesitan apoyo adicional. Cuando se habla inicialmente con la mayoría de los distritos escolares, comienzan con un objetivo muy limitado de predecir qué niños tienen pocas probabilidades de graduarse a tiempo. El primer paso en nuestro proceso de determinación del alcance es volver al objetivo de aumentar las tasas de graduación y preguntar si hay un subconjunto específico de estudiantes en riesgo que quieran identificar. 

¿Qué pasaría si pudiéramos identificar a los estudiantes que tienen solo un 5% de probabilidades de no graduarse a tiempo frente a aquellos que tienen un 95% de probabilidades de graduarse sin apoyo adicional? Si el objetivo es simplemente aumentar las tasas de graduación, es (probablemente) más fácil intervenir e influir en el primer grupo, mientras que el segundo grupo puede ser más desafiante debido a los recursos que necesitan. ¿El objetivo es maximizar la probabilidad promedio de graduarse, o es centrarse en los niños con mayor riesgo y aumentar la probabilidad de que el 10% inferior de los estudiantes se gradúe? ¿O el objetivo es crear más equidad y reducir la diferencia en las tasas de graduación a tiempo entre quienes tienen más probabilidades de graduarse y quienes tienen menos probabilidades de graduarse? 

Todos estos son objetivos razonables, pero las escuelas deben comprender, evaluar y decidir qué objetivos son más importantes para ellos. Esta conversación a menudo les hace pensar más profundamente acerca de definir cuáles son sus objetivos organizacionales, así como las compensaciones entre ellos. **Un objetivo razonable que podemos alcanzar después del proceso de determinación del alcance es minimizar las disparidades en las tasas de graduación entre diferentes grupos raciales y al mismo tiempo maximizar las tasas generales de graduación.**

**Ejemplo 3 – Inspecciones:** Hemos trabajado en varios proyectos que involucraron inspecciones. Algunos ejemplos incluyen: 

la Agencia de Protección Ambiental de EE. UU. y el Departamento de Conservación Ambiental del Estado de Nueva York, que priorizan qué instalaciones inspeccionar para detectar violaciones en la eliminación de desechos;
la ciudad de Cincinnati, identificando propiedades en riesgo de violaciones del código; y 
Grupo del Banco Mundial, dando prioridad a las denuncias de fraude y colusión para investigar. 
En la mayoría de los problemas de inspección, hay muchas más entidades (hogares, edificios, instalaciones, negocios, contratos) para inspeccionar que los recursos disponibles necesarios para realizar esas inspecciones. 

El objetivo con el que comienzan la mayoría de las organizaciones es centrar sus inspecciones en entidades que probablemente infrinjan las regulaciones existentes. Si bien este es un buen comienzo, la mayoría de estas organizaciones nunca pueden inspeccionar todo lo que pueda no cumplir. El objetivo que realmente quieren lograr es **la disuasión: reducir el número total de instalaciones que estarán en infracción** . Un proceso de inspección ideal tendría como resultado reducir el número real de infracciones, ya sea que se encuentren o no, lo que puede no ser lo mismo que un proceso de inspección cuyo objetivo sea ser eficiente y aumentar la tasa de aciertos (% de inspección que resulta en violaciones).

**Ejemplo 4: programación de la recogida de residuos**: Hace unos años, trabajamos con Sanergy, una empresa social con sede en Kenia. Implementan baños portátiles en asentamientos urbanos informales y uno de sus mayores costos es contratar personas para vaciar los baños recogiendo los desechos de cada uno de ellos. Dado que el uso de los retretes varía, es ineficiente vaciar todos los retretes todos los días, como se hacía cuando comenzó el proyecto. Para poder crecer y mantener bajos los costos, necesitaban un enfoque más adaptable que pudiera “optimizar” el cronograma de vaciado de los inodoros. El objetivo, en este caso, es asegurarte de no vaciar demasiado el inodoro cuando no está lleno pero tampoco dejar que se quede lleno porque entonces no se podrá utilizar. Esto se traduce en una formulación que **maximiza el número de veces que se vacían los inodoros cuando están lo más cerca posible del 100 %** de su capacidad sin llegar al 100 % . Una formulación diferente del objetivo podría ser **minimizar el número de veces que una persona va a usar el baño (pero no puede) porque estaba lleno y no se podía utilizar con las limitaciones de recursos de personal que tienen para vaciar los baños** . 

### Considerar las compensaciones al decidir los 

A medida que comenzamos a definir y priorizar objetivos, a menudo en torno a la eficiencia, la eficacia y la equidad, la conversación conduce a compensaciones. 

Cuando trata con estudiantes que pueden necesitar apoyo adicional para graduarse a tiempo, ¿qué es lo que más le importa: encontrar a cada estudiante que pueda necesitar ayuda (que tal vez no necesite el apoyo y posiblemente sea ineficiente) o priorizar la eficiencia y centrarse solo en los estudiantes que ¿Está muy seguro de que necesitará apoyo adicional (y, por lo tanto, perderá a muchos estudiantes) o priorizará la equidad para asegurarse de que los estudiantes que ya están en desventaja y que tal vez no tengan otros recursos disponibles no se queden atrás?

¿Preferiría inspeccionar más hogares sin encontrar peligros de plomo en ellos (lo cual es ineficiente), o preferiría pasar por alto hogares con niños que terminarán intoxicados por plomo? 

Al enviar y colocar vehículos de respuesta a emergencias, ¿desea asegurarse de poder llegar a todas las emergencias posibles en 10 minutos o desea asegurarse de poder llegar a las emergencias críticas en 3 minutos y a las no críticas en 20 minutos? 

**¿Qué tipo de errores estás más dispuesto a cometer?** Ésta es una pregunta crítica que plantea un buen proceso de determinación del alcance y que intenta responder en función de las prioridades de la organización.

En términos de ciencia de datos, ¿preferiría tener más falsos positivos o más falsos negativos? ¿Quiere que estos falsos positivos o falsos negativos se equilibren entre diferentes grupos raciales, de género, de edad o socioeconómicos? Por supuesto, esta decisión depende del impacto y el costo de esos errores, que a menudo son difíciles (y a veces incómodos) de cuantificar. Esta es una conversación sobre valores sociales y políticos que usted desea incorporar en sus operaciones, y los formuladores de políticas deben decidir qué objetivos políticos quieren alcanzar, qué recursos tienen y qué resultados quieren priorizar. Luego, el trabajo de ciencia de datos se utiliza para respaldar e implementar esos objetivos políticos. La ciencia de datos puede ayudar a explorar el impacto de esos objetivos y comprender mejor las implicaciones, pero en última instancia es una decisión política decidir qué objetivos optimizar y debe incluir a todas las partes interesadas afectadas por este sistema.

## Paso 2: ¿Qué acciones/intervenciones estás informando?

El trabajo que hacemos sólo puede tener un impacto si es viable. ¿Qué acciones puede tomar la organización para lograr estos objetivos? ¿Cómo podemos informar esas acciones para hacerlas más efectivas? Estas acciones a menudo deben ser bastante concretas: inspecciones de viviendas, inscribir a un estudiante en uno de los tres programas extraescolares, correos electrónicos dirigidos a recaudación de fondos o promoción, envío de un vehículo de emergencia o programación de una recogida de residuos. 

Idealmente, un proyecto con un buen alcance tiene un conjunto de acciones que la organización está tomando y que pueden informarse mejor mediante la ciencia de datos. Por ejemplo, si un departamento de salud pública está inspeccionando propiedades en busca de plomo, la ciencia de datos puede ayudar a determinar qué casas inspeccionar. 

No es necesario limitar esto a mejorar las acciones existentes. A menudo, también terminamos creando un nuevo conjunto de acciones. Sin embargo, generalmente es una buena estrategia centrarse primero en informar las acciones existentes en lugar de comenzar con acciones completamente nuevas con las que la organización no está familiarizada con la implementación. 

Enumerar el conjunto de acciones que existen (o que se pueden agregar fácilmente) permite que el proyecto sea viable. Si el análisis que se realizará más adelante no informa una acción, generalmente no ayudará a la organización a alcanzar sus objetivos.

Volvamos a nuestro ejemplo de aumentar las tasas de graduación a tiempo para los estudiantes de secundaria. Las escuelas tienen una variedad de acciones que pueden tomar, incluyendo:

1. Creando nuevos programas de apoyo,
2. Inscribir estudiantes en programas de apoyo existentes, y
3. Programar una conversación con un consejero o mentor.

Todas estas acciones varían en varias dimensiones y necesitan varias piezas clave de información para ejecutarse.

1. Crear nuevos programas de apoyo: Necesitamos saber qué programas deben crearse, qué capacidad deben tener y a quién inscribir en esos programas.
2. Inscribir estudiantes en programas de apoyo existentes: Cada programa tendrá algunas limitaciones de capacidad y necesitamos saber qué estudiantes deben tener prioridad para qué programa.
3. Programar una conversación con un consejero/mentor: Esta es una intervención que requiere muchos recursos y necesitaremos saber a qué estudiantes se les debe dar prioridad para esta intervención.

### Desglosando acciones

Al elegir una acción para informar, es importante tener en cuenta los objetivos y pensar en diferentes aspectos de la acción. En primer lugar, debe crear una lista de acciones que una organización está tomando o podría tomar para lograr su objetivo. Luego, debes pensar en quién tomará esta acción y quién se verá afectado por ella. Por ejemplo, en el caso de las inspecciones de plomo, un inspector de plomo inspecciona las casas para buscar evidencia de plomo que pueda remediarse para evitar que un niño quede expuesto. También se debe considerar cómo la organización elige actualmente las prioridades y con qué frecuencia lo hace. Por ejemplo, ¿se selecciona la lista de propiedades para inspeccionar todos los días? ¿Cada semana? ¿Cuantos son los seleccionados? 

También debes considerar a través de qué canales se puede realizar una acción. El canal a través del cual se puede tomar una acción puede tener implicaciones importantes en cuanto a las limitaciones de capacidad. Por ejemplo, generalmente se necesitan menos recursos para enviar un correo electrónico, un mensaje SMS o incluso una carta que para hacer una llamada telefónica en vivo o realizar actividades de divulgación en persona. Las limitaciones de capacidad pueden ayudarle a decidir qué tan valioso puede ser un proyecto de ciencia de datos para priorizar sus acciones, así como cuántas acciones puede completar la organización a la vez. 

Finalmente, siempre debe considerar las implicaciones éticas de las acciones que informará con su proyecto de ciencia de datos y si priorizar la acción utilizando un análisis de ciencia de datos podría exacerbar las desigualdades u otros resultados indeseables. 

## Paso 3: ¿Qué datos tienes y qué datos necesitas?

Notarás que hasta ahora en el proceso de determinación del alcance no hemos hablado de datos en absoluto. Esto es intencional ya que queremos que estos proyectos se centren en los problemas y no en los datos. Sí, los datos son importantes y a todos nos encantan, pero comenzar con ellos a menudo conduce a análisis que pueden no ser procesables o relevantes para los objetivos que queremos lograr. 

Una vez que entendemos nuestro problema y hemos determinado nuestros objetivos y acciones, el siguiente paso es determinar a qué datos tenemos acceso dentro y fuera de la organización que serán relevantes para resolver el problema, así como qué fuentes de datos podemos necesitar. obtener acceso a. 

Primero desea hacer una lista de fuentes de datos que están disponibles dentro de la organización. Este es un proceso iterativo, ya que es posible que muchas organizaciones no tengan una lista completa de sus fuentes de datos. A veces (si tiene suerte) los datos pueden estar en un almacén de datos central e integrado, pero incluso entonces puede encontrar personas o departamentos que tengan datos adicionales o diferentes versiones del almacén de datos. Consulte nuestro Marco de madurez de datos para evaluar la preparación de su organización para un proyecto de ciencia de datos.

Es una buena práctica recopilar información detallada sobre cada fuente de datos. Por ejemplo, querrás saber su:

- **Granularidad o detalle:** el nivel al que se recopilan los datos. Por ejemplo, se pueden recopilar algunos datos sobre estudiantes individuales, algunos sobre escuelas y otros sobre vecindarios o distritos escolares.
- **Frecuencia:** Con qué frecuencia se actualizan los datos. Por ejemplo, los datos pueden actualizarse anualmente, mensualmente, semanalmente, diariamente o incluso inmediatamente (en tiempo real). Es posible que algunos datos solo se actualicen de forma ad hoc, por ejemplo, cada vez que la organización reciba un conjunto de datos actualizado.
- **Historia:** hasta dónde se remontan los datos. Tener más datos históricos mejorará el análisis. 
- **Identificadores:** por lo general, querrá que los datos incluyan identificadores únicos y confiables que le permitan vincularse a otras fuentes de datos, como números de seguro social, números de seguro, números de identificación de estudiantes o direcciones. 
- **Propietario:** La organización, departamento, grupo o personas que controlan el acceso a los datos. Por ejemplo, los distritos escolares pueden ser propietarios de algunos datos de los estudiantes, pero otros datos de los estudiantes pueden ser propiedad de escuelas individuales o agencias educativas locales. 
- **Almacenamiento:** Cómo se almacenan los datos. Algunos datos se almacenan en bases de datos, mientras que otros datos pueden almacenarse en hojas de cálculo, archivos PDF, almacenes de datos o incluso archivos impresos.
- **Ética:** Cuestiones éticas que pueden estar asociadas con el uso de las fuentes de datos. Por ejemplo, el uso de algunas fuentes de datos puede requerir el consentimiento de las personas cuyos datos se utilizan. También pueden existir ciertos protocolos de seguridad necesarios para acceder y utilizar los datos. 

### Hacer coincidir los datos con las acciones

Antes de comenzar un proyecto de ciencia de datos, es importante determinar si los datos a los que tiene acceso coinciden con las acciones que necesita informar. Por ejemplo, si las acciones que queremos tomar para lograr nuestros objetivos son a nivel individual, entonces lo más probable es que necesites datos a nivel individual. Si es necesario decidir las acciones una vez al día, entonces necesita que sus datos se actualicen todos los días. Es importante hacer coincidir la granularidad, frecuencia y horizonte temporal de las acciones con la granularidad, frecuencia y horizonte temporal de los datos que tiene.

### Datos Externos y/o 

Una vez que haya determinado qué datos necesita y qué datos existen dentro de la organización, deberá determinar qué datos externos o públicos puede obtener para llenar los vacíos. Cada dominio suele tener fuentes de datos de uso común que puede incorporar a su proyecto. La Encuesta sobre la Comunidad Estadounidense es un buen ejemplo de fuente de datos que desea utilizar en la mayoría de los proyectos que involucran algún componente geográfico en los Estados Unidos. Los portales de datos abiertos (a nivel federal, estatal y local) también tienen datos que pueden usarse para aumentar sus datos internos. Los datos de llamadas al 311, los datos de llamadas al 911 y los datos de incendios son ejemplos de algunas fuentes de datos locales que se encuentran comúnmente. También desea echar un vistazo a las fuentes de datos comerciales que puede comprar para aumentar sus datos internos. Los ejemplos incluyen datos de compra de organizaciones como Acxiom y Experian sobre comportamiento de compra o hábitos de compra de medios de Nielsen.

También puede haber otros datos que le gustaría incluir en su análisis a los que quizás no tenga acceso actualmente o a los que pueda resultar difícil acceder. Es importante pensar más allá de las fuentes de datos disponibles y considerar datos que podrían ser útiles para su proyecto, incluso si no están disponibles actualmente. Identificar datos útiles pero no disponibles puede ayudarle a identificar posibles fuentes de datos que pueden mejorar su análisis. También puede haber representantes de esos datos que existan. Esto puede incluir datos que son muy seguros o de difícil acceso, como videos de CCTV, registros telefónicos o registros de ADN. También puede incluir datos cuya recopilación requeriría un esfuerzo adicional, como resultados de encuestas, o datos cuya recopilación requeriría cambios en el sistema, como datos que se actualizan con más frecuencia o se recopilan con un nivel de granularidad diferente. 

Si bien es importante pensar en grande al considerar qué datos pueden mejorar su análisis, también es importante tener en cuenta consideraciones éticas, especialmente al acceder a fuentes de datos confidenciales. Las fuentes de datos externas que no son públicas pueden requerir acuerdos y requisitos legales adicionales para acceder.

## Paso 4: ¿Qué análisis hay que hacer?

Una vez que tengamos identificados los objetivos, las acciones y los datos disponibles, el paso final en el proceso de determinación del alcance es determinar los análisis que haremos para informar las acciones identificadas, utilizando los datos que tenemos, para lograr nuestros objetivos. Vale la pena reiterar que el análisis no es el objetivo de un proyecto de ciencia de datos y es recomendable dejar esta parte de lado hasta que los objetivos, las acciones y los datos disponibles estén claramente definidos. 

Los análisis pueden utilizar métodos y herramientas de diferentes áreas: informática, aprendizaje automático, ciencia de datos, estadística y ciencias sociales. Una forma de pensar en el análisis realizado es dividirlo en cinco tipos:

**Descripción**: Centrado principalmente en comprender eventos y comportamientos que sucedieron en el pasado. Normalmente, todos los proyectos contienen un componente de análisis descriptivo para comprender los datos. Sin embargo, es raro que un análisis descriptivo sea el único componente de análisis de un proyecto.

P.ej:

- Explorar datos sobre estudiantes que no se graduaron a tiempo en el pasado, potencialmente revelando "tipos" de estudiantes que sufren resultados adversos en comparación con otros con respecto a factores altamente correlacionados.

**Detección**: Menos centrado en el pasado y más centrado en los acontecimientos en curso. Las tareas de detección a menudo implican detectar eventos y anomalías que están sucediendo actualmente.

P.ej 

- Uso de datos de texto de proyectos de ley para identificar sus áreas temáticas 
- Detección de transacciones fraudulentas con tarjetas de crédito 

**Predicción**: Centrado en el futuro y prediciendo comportamientos y eventos futuros.

P.ej 

- Predecir la probabilidad de que un estudiante se gradúe a tiempo de la escuela secundaria al momento de ingresar al noveno grado, 
- Predecir la probabilidad de que un proyecto de ley se convierta en ley en el momento en que se presenta a la legislatura. 

**Optimización** : Enfocada en tomar los resultados de otros tipos de análisis y utilizarlos para asignar recursos o tomar decisiones.

P.ej 

- Identificar dónde ubicar las ambulancias para maximizar su cobertura. 
- Dada una lista de estudiantes clasificados según su probabilidad de no graduarse a tiempo, identifique el subconjunto de estudiantes para la intervención que tendría el mayor impacto

**Cambio de Comportamiento:**Enfocado a provocar un cambio de comportamientos de personas, organizaciones, barrios. Normalmente utiliza métodos de inferencia causal y economía del comportamiento.

P.ej 

- Dado que un estudiante corre el riesgo de no graduarse a tiempo y un conjunto de posibles intervenciones, identificar la intervención que maximizaría su probabilidad de graduarse a tiempo.

Por supuesto, hay muchos más tipos de análisis, pero aquí nos centraremos en estos cinco. 

Para cada análisis que hagamos en el proyecto, debemos buscar responder a lo siguiente

- ¿Qué tipo de análisis hay que hacer y cuál es el propósito?

¿Es este un análisis descriptivo, un modelo predictivo o una tarea de detección o cambio de comportamiento? A menudo, el proyecto implica varios de los tipos de análisis que describimos anteriormente, cada uno diseñado para informar acciones específicas y lograr objetivos específicos.

- ¿Cómo informará el análisis las acciones?

Cada análisis debe informar una o más de las acciones identificadas. Algunos análisis podrían informar múltiples acciones y, a veces, una acción podría informarse de múltiples análisis.

¿Cómo se validará el análisis? ¿Qué validación se puede hacer utilizando datos históricos existentes? 
Es importante pensar en cómo podemos validar cada análisis utilizando los datos históricos disponibles. Deberíamos elegir la configuración de validación para reflejar el escenario de implementación (cómo un usuario usaría este modelo, por ejemplo) lo más fielmente posible. Normalmente, para las tareas de predicción, crearíamos múltiples conjuntos de validación de trenes y elegiríamos una métrica que refleje con precisión cómo usamos el modelo y observaríamos cómo se desempeñan nuestros modelos a lo largo del tiempo. Un aspecto fundamental en el que tendríamos que pensar es en las líneas de base con las que comparamos nuestros modelos. Si la organización está realizando esta tarea hoy de alguna manera, una buena base de referencia es el desempeño del “sistema existente”. Otras buenas líneas de base incluyen heurísticas simples (basadas en conocimientos de expertos o investigaciones previas). Queremos que nuestro nuevo análisis sea “lo suficientemente mejor” que los enfoques existentes o más simples para que valga la pena implementar el sistema de ciencia de datos, más costoso de construir y mantener.

1. ¿Cuáles son las cuestiones éticas asociadas con el análisis? 

¿Existen implicaciones de equidad que nos preocupen? ¿Cómo afectarían los errores en su análisis a los individuos y a la sociedad? 

Lo demostraremos con algunos ejemplos. 

**Reducir las tasas de envenenamiento por plomo**

**Meta:** Reducir la cantidad de niños que sufrirán envenenamiento por plomo en el futuro debido a los peligros del plomo en su residencia actual. 

**Acciones: Inspecciones** proactivas de viviendas limitadas por recursos de inspección limitados.

**Análisis**: Necesitamos responder la pregunta clave: "¿Qué casas debemos priorizar para las inspecciones proactivas?" En otras palabras, queremos identificar los hogares de los niños que corren riesgo de sufrir intoxicación por plomo en el futuro. 

Como queremos intervenir antes de que un niño esté expuesto al plomo, predeciríamos la probabilidad de que todos los niños menores de 2 años estén expuestos al plomo en sus hogares. Podríamos usar nuestras predicciones para clasificar las casas según el riesgo de que un niño quede expuesto al plomo en ellas y priorizarlas para su inspección. Si consideramos los cinco tipos de análisis que mencionamos anteriormente, esta sería una tarea de predicción.

**Validación**:   digamos que la cantidad de hogares que la agencia puede inspeccionar en un mes es 100. Teniendo en cuenta esto, podemos optimizar el análisis para predecir los 100 hogares donde es más probable que un niño esté expuesto al plomo cada mes, una métrica que llamamos Precisión en K (o P@K). 

En este ejemplo, el vínculo causal entre la acción (inspección y eliminación del plomo) y el objetivo (proteger a los niños de la exposición al plomo) está bien establecido. Puede que ese no sea el caso en todos los proyectos. Tomemos el ejemplo de la graduación oportuna de la escuela secundaria:

**Mejorar las tasas de graduación**

**Meta**: Aumentar el porcentaje de estudiantes de secundaria que se gradúan a tiempo, al tiempo que se reduce la disparidad en las tasas de graduación entre grupos raciales. 

**Acciones:** Brindar apoyo adicional a los estudiantes identificados como en riesgo de no graduarse a tiempo

**Análisis:**

1. Al igual que con el proyecto de peligros del plomo, tenemos que realizar un análisis predictivo; predecir qué estudiantes tienen menos probabilidades de graduarse a tiempo. Podemos utilizar estas predicciones para priorizar un subconjunto de estudiantes para mayor alcance y apoyo. 
2. Una vez que se predice el riesgo para cada estudiante, seleccionar el subconjunto de estudiantes para la intervención puede no ser tan sencillo como priorizar a los estudiantes con el mayor riesgo previsto. Dada la naturaleza de las intervenciones y la métrica que le interesa mejorar, los mejores estudiantes para la intervención podrían cambiar. Por ejemplo, si el objetivo es mejorar la tasa promedio de graduación con el mínimo esfuerzo, priorizar a los estudiantes con una puntuación de riesgo más media podría resultar más eficaz que priorizar a aquellos que tienen muchas probabilidades de no graduarse a tiempo. Un análisis de optimización podría ayudar a identificar el conjunto óptimo de estudiantes a los que se dará prioridad para la intervención. 
3. Incluso si seleccionamos el conjunto “óptimo” de estudiantes para la intervención, podría haber múltiples tipos de apoyo adicionales disponibles (por ejemplo, tutoría después de la escuela, asesoramiento, ayuda con el transporte, ayuda financiera). Identificar las intervenciones más efectivas para estudiantes individuales podría requerir un análisis de inferencia causal. 


## Cuestiones éticas:

Como recordatorio, la consideración de las cuestiones éticas debe integrarse en cada fase del alcance y la ejecución de un proyecto, en lugar de considerarse como un “paso” discreto en ese proceso. A menudo, la conversación inicial sobre la ética en la fase de determinación del alcance se centrará en los valores éticos y sociales que queremos incorporar al sistema. Tenga en cuenta que esta conversación no es específica de las aplicaciones de la ciencia de datos o la IA, sino más bien de los valores que, en términos generales, deben incorporarse en los procesos de toma de decisiones que afectan la vida de las personas. Como tal, estas decisiones no pueden ser tomadas unilateralmente por los científicos de datos o tecnólogos encargados de construir el sistema. Si bien tienen un papel importante en la discusión, es importante que incluya a todas las partes interesadas relevantes: los formuladores de políticas, quienes toman medidas, los desarrolladores de sistemas, los propietarios de datos y la comunidad afectada por el sistema tendrán perspectivas importantes sobre estos asuntos.

A medida que avanza en el proceso de determinación del alcance (y el proyecto en sí), ser explícito acerca de cómo su trabajo refleja esos valores puede ayudar a actuar como un principio rector en el curso de las muchas decisiones que deben tomarse para llevar a cabo un proyecto. Para resaltar su naturaleza central, hemos consolidado muchos de ellos aquí y planteamos algunas preguntas motivadoras para ayudarlo a explorar estos temas. Esta lista está lejos de ser exhaustiva, pero más bien proporciona un punto de partida para esa conversación: 

**Privacidad, confidencialidad y seguridad**

Las preocupaciones sobre la privacidad y la seguridad de los datos son comunes en las aplicaciones de la ciencia de datos a problemas de impacto social, particularmente cuando están involucradas decisiones de alto riesgo, como la atención médica, la justicia penal y la educación. En algunos casos, puede haber requisitos legales que rijan sobre cómo se pueden utilizar los datos y los pasos que se deben implementar para protegerlos, pero las consideraciones éticas pueden ir más allá de lo que se requiere legalmente. Particularmente importante aquí es cómo las personas podrían sentirse acerca de los datos que se utilizan sobre ellos, así como sus expectativas sobre qué tan públicamente están disponibles esos datos. Las preguntas para hacer aquí incluyen:

- ¿Cuáles son las consideraciones de privacidad (tanto legales como éticas)?
- ¿Cómo se protege la privacidad de las personas en los datos?
- ¿Qué pasa con la confidencialidad?
- ¿Cuáles son las consideraciones y protecciones de seguridad? ¿Quién tiene acceso a qué partes de los datos? - ¿Con qué fines? ¿Cuál es el proceso de auditoría de seguridad?

**Transparencia**

Las consideraciones de transparencia para la construcción e implementación de sistemas de ciencia de datos pueden involucrar a muchas partes interesadas diferentes: actores internos y tomadores de decisiones, personas cuyos datos se utilizan, personas que se verán afectadas por las decisiones que informa el sistema y el público en general. Al considerar las siguientes preguntas, tenga en cuenta las perspectivas de cada una de estas partes interesadas:

- ¿Qué partes interesadas deben conocer el proyecto?
- ¿Las personas cuyos datos estás usando saben que los estás usando?
- ¿Cómo afectarán a las personas las acciones que está tomando basándose en este análisis? ¿Cuáles son los costos o beneficios de esta acción para las personas afectadas?
- ¿Las personas a las que estás dando prioridad saben si se les está dando prioridad y por qué?
- ¿Qué recurso tienen las personas para cuestionar o cambiar una decisión informada por su análisis que les ha impactado?

**Discriminación, equidad y justicia**

Comprender y mejorar la equidad de los sistemas de aprendizaje automático ha sido objeto de muchos escritos e investigaciones recientes, tanto en trabajos académicos como en la prensa popular. Durante el proceso de determinación del alcance, es importante comprender los tipos de disparidades que podrían resultar de su proyecto y cómo podrían afectar a las personas, teniendo en cuenta las perspectivas de las personas afectadas por su análisis y cualquier discriminación histórica y actual que pueda afectarlas.

Por ejemplo, en el contexto de la detección de llamadas a líneas directas de bienestar infantil, las disparidades en los falsos negativos (no dar seguimiento a un informe con una investigación cuando en realidad debería haberlo hecho) significarían más daño para los niños de una comunidad que de otra. Por el contrario, las disparidades en los falsos positivos (realizar una investigación innecesaria) podrían dar lugar a una vigilancia excesiva en algunas comunidades, lo que provocaría daños sociales más amplios. Dos herramientas de nuestro trabajo que pueden ser útiles aquí son el Árbol de Equidad, que utilizamos para ayudar a facilitar estas conversaciones, y Aequitas, que ayuda a auditar los resultados del modelo para detectar disparidades; ambas se pueden encontrar aquí . Algunas de las preguntas clave que debemos plantearnos con respecto a la discriminación y la justicia son:

- ¿Qué grupos específicos podrían verse afectados de manera desigual por su análisis y cómo debería tener esto en cuenta?
- Desde la perspectiva de cada uno de estos grupos, ¿cómo definen la justicia en este contexto? ¿Qué tan bien alineadas están estas definiciones?
- ¿Durante qué horizonte temporal está intentando mejorar la equidad en este trabajo?
- ¿Cómo detectará sesgos o desigualdades en su sistema?
- ¿Qué disparidades existen en el actual proceso de toma de decisiones?
- Si existen desigualdades, ¿cómo abordará su reducción en su sistema o mitigará su impacto en las decisiones e intervenciones posteriores?
- ¿Existen fuentes más amplias de desigualdades, ya sean históricas o actuales, que afecten los resultados que se intenta mejorar? ¿Cómo debería su sistema tenerlos en cuenta?

**Responsabilidad**

La rendición de cuentas debe considerarse con respecto a todo el proceso, incluidas tanto las decisiones técnicas tomadas mientras se trabaja con los datos como las decisiones tomadas sobre cómo se utilizará el sistema en la práctica y se describirá al público. Garantizar que haya claridad desde el principio sobre quién es el responsable de cada aspecto del sistema, particularmente con respecto a posibles aspectos y consideraciones éticos, puede ayudar a reducir tanto los riesgos de que surjan problemas (al establecer límites y hacer que la supervisión sea responsabilidad explícita de alguien) como daños potenciales si estos problemas surgen (al tener planes de contingencia implementados). Por ejemplo, nuestro grupo ha trabajado en varios proyectos que buscan reducir el riesgo de encarcelamiento proporcionando intervenciones de asistencia como apoyos de salud mental o servicios sociales. Sin embargo, el mismo modelo que predice el riesgo de arrestos futuros también podría usarse de maneras más preocupantes y punitivas que nuestros acuerdos con socios deben definir cuidadosamente y protegerse contra ellas. Algunas preguntas que se pueden hacer sobre la rendición de cuentas incluyen:

- Si se utilizan datos confidenciales para el proyecto, ¿quién es responsable de mantenerlos seguros? ¿Qué planes de contingencia existen en caso de que haya una fuga y quién será el responsable?
- ¿Qué limitaciones existen sobre cómo se utilizará su análisis? ¿Quién asume la responsabilidad si se utiliza con fines dañinos o no deseados?
- ¿Cómo monitoreará las consecuencias no deseadas (por ejemplo, si los estudiantes que se predice que corren el riesgo de tener un bajo desempeño internalizan esta predicción)? ¿Qué procesos se implementarán para reducir cualquier daño potencial que puedan causar?
- ¿Cómo determinará si el sistema está aumentando las disparidades con el tiempo? ¿Quién es responsable de monitorear esto y tomar decisiones sobre cómo responder?
- ¿Quién tiene la responsabilidad de determinar qué revelar al público sobre el sistema y cómo describirlo? Si la gente se opone, ¿quién es responsable y qué se debe hacer?
- ¿Qué recursos tienen las personas afectadas por el nuevo sistema si comete errores al respecto o hace recomendaciones basadas en datos inexactos? ¿Quién es responsable de responder a estos problemas y realizar las mejoras necesarias al modelo o análisis subyacente?

**Licencia Social**

El concepto de licencia social está relacionado con las ideas de transparencia y rendición de cuentas, pero con un marco diferente que puede proporcionar un útil ejercicio de reflexión. Independientemente de sus planes reales en torno a la transparencia descrita anteriormente o de cuántas personas podrían conocer los detalles del proyecto en la práctica, aquí desea pensar en cómo las personas podrían responder a su proyecto si recibiera una cobertura amplia. ¿Se presentaría uniformemente bajo una luz positiva o negativa, o en qué medida diferentes personas reaccionarían de manera diferente ante él? Algunas preguntas que le ayudarán a considerar la licencia social para su proyecto incluyen:

- Si toda la población del país se entera de su proyecto, ¿estará de acuerdo con él? ¿Por qué?
- Si estuviera en la portada del periódico, ¿cuál sería el titular? ¿Sería positivo o negativo?
- Incluso si cree que la población podría apoyar su proyecto en general, ¿hay algún grupo que podría oponerse? ¿Quiénes son y qué preocupaciones tendrían?

**Otras consideraciones éticas**

Finalmente, es importante tener en cuenta que la lista aquí es sólo un punto de partida y puede haber otras consideraciones éticas relevantes para su contexto específico. ¿Existen requisitos legales, políticos u organizativos adicionales que no se hayan cubierto anteriormente? ¿Necesita obtener el consentimiento informado de las personas potencialmente afectadas por este trabajo? ¿Existen procedimientos específicos de supervisión, presentación de informes o revisión ética? Como es el caso con las otras consideraciones anteriores, aquí puede ser útil pensar en el proyecto a través de las perspectivas de diferentes partes interesadas y explorar si podrían surgir consideraciones o inquietudes que no encajen bien en las otras categorías aquí.

## Consideraciones adicionales

**Evaluación**

Una vez que haya completado su análisis y lo haya validado con los datos disponibles, es importante evaluarlo en el campo para asegurarse de que ayude a lograr sus objetivos. Las pruebas de campo son un tema complicado y pueden ser bastante específicas del proyecto y sus objetivos, por lo que no las abordaremos en detalle aquí. Sin embargo, su evaluación debe ser una aplicación del análisis a las acciones que se propusieron para informar y debe medirse con respecto a sus objetivos predefinidos. 

Una evaluación de este tipo a menudo requiere la participación de personas dentro y fuera de la organización y un compromiso significativo de tiempo y recursos de la organización. Incluso antes de embarcarse en un nuevo proyecto, la organización debe estar segura de que puede comprometer el tiempo y los recursos necesarios y debe involucrar a cualquiera que participe en la evaluación y aplicación del análisis. Estas conversaciones y compromisos deben ocurrir al comienzo del proceso de determinación del alcance para garantizar que el proyecto sea exitoso.

La evaluación puede mostrar si el análisis tiene o no éxito en el logro de los objetivos de la organización. La evaluación no debe verse como una oportunidad para demostrar que el análisis es exitoso, sino como una oportunidad para probar su efectividad y tal vez mejorarlo de manera iterativa reevaluando otros aspectos del alcance del proyecto, como el análisis en sí, los datos utilizados. para el análisis, o las acciones a las que se aplica el análisis. 

**Despliegue**

Si el análisis resulta eficaz en la evaluación, entonces querrá implementarlo como un nuevo sistema en la infraestructura de la organización para que pueda actualizarse periódicamente e incorporarse a sus operaciones. Una de las consideraciones más importantes al implementar un nuevo sistema es si se construyó o no en la infraestructura de la organización. Si el sistema se construyó sobre la infraestructura de la organización, a menudo (aunque no siempre) será más fácil de implementar, porque ya debería ser consistente con la infraestructura técnica de la organización. Los científicos de datos que trabajan dentro de la organización generalmente tendrán acceso a la infraestructura interna de la organización y deben trabajar en estrecha colaboración con los ingenieros de producción para asegurarse de que su sistema se integre con ella. Los voluntarios y otros científicos de datos externos también pueden acceder a la infraestructura de la organización a través de acuerdos comerciales o de voluntariado, lo que hace que el proceso de implementación sea más fluido. 

Sin embargo, a menudo los sistemas de ciencia de datos se construyen fuera de la infraestructura de la organización, posiblemente debido a problemas de seguridad o privacidad que limitan el acceso. Cuando esto sucede, la implementación puede resultar más complicada. Los profesionales de ingeniería y datos internos de la organización que trabajan con y mantienen su infraestructura técnica deben incorporarse tempranamente al proceso de determinación del alcance para garantizar que el sistema construido por los científicos de datos asociados se ajuste a la infraestructura de la organización y pueda integrarse e implementarse con bastante facilidad. El proyecto debe ser una prioridad para los profesionales técnicos y de datos de la organización que son necesarios para la implementación, y debe haber tiempo en sus agendas para dedicarlo a este proyecto, como a cualquier otro. Si los propios datos y profesionales técnicos de la organización no participan en el proyecto y no tienen el tiempo presupuestado para el proyecto, entonces estará condenado al fracaso. Es posible que los mismos profesionales técnicos y de datos que ayudan a implementar el nuevo sistema necesiten mantenerlo en producción, y esto debe incluirse en su cronograma y carga de trabajo. 

Los sistemas de ciencia de datos también requieren recursos informáticos para su implementación. Se debe lograr una buena comprensión de la capacidad informática de la organización antes de iniciar el proyecto. Durante la implementación, los sistemas de ciencia de datos utilizarán memoria y llevarán tiempo actualizarlos. Esto debe tenerse en cuenta dentro de la infraestructura de la organización, y los profesionales técnicos y de datos internos deben asegurarse de que las actualizaciones periódicas de los sistemas de ciencia de datos no entren en conflicto ni compitan por recursos con otros procesos técnicos importantes.

Los sistemas de ciencia de datos también dependen de actualizaciones periódicas y consistentes de las fuentes de datos subyacentes. Los profesionales técnicos y de datos de la organización deben asegurarse de que las actualizaciones periódicas del nuevo sistema sean coherentes con las actualizaciones de los datos subyacentes. Si los datos son antiguos, están retrasados ​​o son inconsistentes con las actualizaciones del nuevo sistema, entonces el valor de ese sistema se reducirá e incluso puede deteriorarse con el tiempo. 

Finalmente, será importante considerar quién en la organización utilizará los resultados del sistema y cómo accederán a ellos. La clave para esto es pensar en cómo el usuario final utilizará realmente la información. ¿El usuario final examinará los casos individuales uno por uno o creará una lista para priorizar? Si el usuario final está considerando los casos uno por uno, entonces puede resultar útil una interfaz de usuario visual que le proporcione el resultado junto con otra información sobre el caso. Si, en cambio, el usuario final está creando una lista priorizada (de lugares para inspeccionar, por ejemplo), entonces puede ser mejor entregarle una lista de los casos principales, tal vez en una interfaz de usuario visual o incluso como un correo electrónico o un documento imprimible. ! Estas decisiones deben tener en cuenta los procesos operativos actuales del usuario final, su acceso a la tecnología en su trabajo y su alfabetización (digital y de otro tipo), entre otras consideraciones. La formación también será una parte clave del despliegue, tanto para el mantenimiento técnico del sistema como para los usuarios finales que lo utilizarán para tomar decisiones. 

**Supervisión**

Una vez que el sistema de ciencia de datos se implemente e integre en las operaciones de la organización, será necesario monitorearlo continuamente para garantizar que continúe funcionando bien y proporcione información que mejore la toma de decisiones. El rendimiento de los sistemas de ciencia de datos puede deteriorarse con el tiempo por diversas razones, incluidos cambios en los datos subyacentes o en la calidad de los datos, cambios en las políticas u operaciones de la organización o incluso cambios en las tendencias del mundo real. Para garantizar que la información que proporciona el sistema siga siendo útil, las organizaciones deben tener un plan y comprometer recursos para monitorear el desempeño del sistema a lo largo del tiempo como parte regular de sus operaciones. 

Primero, debe crear un plan sobre cómo se monitoreará el sistema, incluidos qué datos y métricas se deben usar para evaluar su desempeño a lo largo del tiempo. Es probable que estos datos sean actualizaciones futuras de los mismos datos que se utilizaron para desarrollar el análisis original y pueden utilizar algunas de las mismas métricas y diagnósticos que se utilizaron para validarlo. Al monitorear el rendimiento, debe tener cuidado de garantizar que los datos utilizados para evaluar el sistema no se filtren en los datos utilizados para actualizarlo. Esto podría llevar a sobreestimar el rendimiento del sistema y enmascarar cualquier deterioro. 

La organización también necesitará comprometer personal técnico para monitorear el desempeño del sistema y administrarlo si falla o si el desempeño se deteriora. Esto requiere comprender no sólo el sistema sino también los datos que se utilizan para actualizarlo y evaluarlo. Es posible que sea necesario capacitar al personal técnico para comprender, evaluar y actualizar el sistema, y ​​se recomienda cierta redundancia para que la organización tenga las habilidades necesarias para mantener el sistema, incluso si un miembro del personal se va. 

La organización también debe planificar la realización de evaluaciones de campo adicionales (como la descrita anteriormente) a intervalos regulares para garantizar que el sistema siga proporcionando información procesable y que mejore las operaciones. Esto requiere el compromiso no solo de los profesionales de datos sino también de los usuarios finales con la evaluación del sistema. La frecuencia de estas evaluaciones puede variar según la capacidad de la organización, la frecuencia con la que se actualizan los datos y el sistema, y ​​la frecuencia de los cambios en las operaciones de la organización y el entorno político general. Sin embargo, es importante que la organización planee dedicar recursos al seguimiento y evaluación continuos del sistema. Después de todo, ¡un sistema que proporciona información deficiente podría ser peor que ningún sistema!

Finalmente, debe planificar lo que hará si el sistema muestra signos de deterioro. Este plan debe considerar cuáles pueden ser las fuentes del deterioro, incluidos cambios en los datos de entrada o de evaluación, cambios en las políticas u operaciones de la organización o cambios en las tendencias del mundo real. Las respuestas diferirán según las fuentes de deterioro del rendimiento. 

También debe considerar qué hará la organización con el sistema si cambia su infraestructura, datos, políticas u operaciones. El sistema debe evaluarse según los nuevos cambios y se debe determinar si todavía proporciona información útil y procesable, o si será necesario actualizarlo o retirarlo. Esto es importante porque los cambios en los datos de entrada o la infraestructura que respaldan el sistema podrían afectar su desempeño, mientras que los cambios en las políticas u operaciones pueden significar que el sistema ya no proporciona información relevante para esos nuevos procesos.

## Resumen

Con suerte, esto brindará a las agencias gubernamentales y organizaciones sin fines de lucro una descripción general de cómo abarcar los proyectos de análisis/ciencia de datos y qué preguntas deben responder antes de lanzar el proyecto.

Paso 1: Metas – Definir las metas del proyecto

Paso 2: Acciones – ¿Qué acciones/intervenciones tienes que informarán este proyecto?

Paso 3: Datos : ¿a qué datos tiene acceso internamente? ¿Qué datos necesitas? ¿Qué puedes aumentar de fuentes externas y/o públicas?

Paso 4: Análisis : ¿Qué análisis es necesario realizar? ¿Implica descripción, detección, predicción, optimización o cambio de comportamiento? ¿Cómo se validará el análisis?

Consideraciones éticas : ¿Cómo ha pensado en las cuestiones de privacidad, transparencia, discriminación/equidad y responsabilidad en torno a este proyecto?

También hemos creado una hoja de trabajo en blanco para determinar el alcance del proyecto que puede utilizar. Nos encantaría recibir comentarios sobre su uso, ya que con frecuencia organizamos talleres y capacitación sobre el alcance de proyectos para estudiantes, así como para agencias gubernamentales y organizaciones sin fines de lucro. Si estás interesado en ser parte de esta capacitación, háznoslo saber .

