# 🗄️ Unidad I: Introducción a Base de Datos

**Autor:** 🧑‍💻 Ing. Elvis Sanchez

---

## 🌍 Introducción

La información es un recurso muy importante para cualquier sistema de información. En muchos casos, la información es volátil y se pierde al terminar el sistema, pero habrá ocasiones en que sea necesario guardar la información. Por ello, debemos conocer las **bases de datos**. Las bases de datos son un componente esencial en el desarrollo de sistemas de información, ya que permiten almacenar, organizar y gestionar grandes volúmenes de datos de manera eficiente, segura y accesible. En un mundo donde la información se ha convertido en uno de los recursos más valiosos, las bases de datos juegan un papel estratégico para empresas, organizaciones y aplicaciones de todo tipo. Desde sistemas bancarios y plataformas de comercio electrónico hasta redes sociales y aplicaciones móviles, las bases de datos están presentes en prácticamente todos los aspectos de la tecnología moderna, actuando como el núcleo que sustenta la operación de estos sistemas.

En esta unidad, nos adentraremos en los conceptos fundamentales de las bases de datos, explorando su importancia y funcionalidad en diversos contextos. Analizaremos los diferentes tipos de bases de datos que existen, desde las relacionales hasta las NoSQL, y evaluaremos sus ventajas y desventajas según las necesidades específicas de cada proyecto. Además, estudiaremos los sistemas de gestión de bases de datos (DBMS, por sus siglas en inglés), que son las herramientas clave para administrar y manipular estos repositorios de información.

Profundizaremos también en los modelos conceptuales, lógicos y físicos de las bases de datos, entendiendo cómo cada nivel contribuye al diseño y funcionamiento eficiente de un sistema. Finalmente, abordaremos el proceso de **normalización**, una técnica crucial para eliminar redundancias, optimizar el almacenamiento y garantizar la integridad de los datos. Este proceso no solo mejora el rendimiento de las bases de datos, sino que también facilita su mantenimiento y escalabilidad a largo plazo.

---

## 🗃️ Base de Datos

Una **Base de Datos** es un sistema organizado y estructurado diseñado para almacenar, gestionar y recuperar información de manera eficiente, segura y confiable. En esencia, funciona como un repositorio centralizado donde los datos se almacenan de forma lógica y coherente, lo que permite que sean accesibles, modificables y utilizables por aplicaciones, sistemas o usuarios autorizados. Este componente es fundamental en la mayoría de las aplicaciones modernas, ya que proporciona una infraestructura robusta para manejar grandes volúmenes de datos de manera escalable, minimizando errores, redundancias y tiempos de acceso.

Las bases de datos no solo son un medio para almacenar información, sino también una herramienta crítica para garantizar su integridad, consistencia y seguridad. Gracias a su diseño estructurado, permiten organizar datos complejos en formatos comprensibles y manejables, lo que facilita su análisis, consulta y manipulación. Además, ofrecen mecanismos avanzados para proteger la información contra accesos no autorizados, pérdida de datos o corrupción, asegurando que los datos permanezcan disponibles y confiables en todo momento.

Estas también se pueden organizar de acuerdo a diferentes modelos y paradigmas, cada uno dotado de características, ventajas y desventajas, según su estructura, su jerarquía, su capacidad de transmisión o de interrelación, entre otros criterios posibles. Estas diferencias constituyen el campo de los modelos de base de datos y permiten el diseño y la implementación de algoritmos y otros mecanismos lógicos de gestión para administrar los datos guardados.

Actualmente, el manejo de las bases de datos se lleva a cabo mediante sistemas de gestión llamados **DBMS** (siglas en inglés de Database Management Systems, “Sistemas de Gestión de Bases de Datos”). Este tipo de software permite el almacenamiento ordenado y la rápida recuperación de la información, sacando así provecho a la automatización y las interfaces digitales.

El uso de bases de datos trae ciertos beneficios, pero también trae sus problemas. Vamos a ver algunos de estos:

| **✅ Ventajas**                              | **❌ Desventajas**                            |
|---------------------------------------------|---------------------------------------------|
| Integridad y consistencia de los datos      | Complejidad en el diseño y mantenimiento    |
| Acceso eficiente a los datos                | Costo inicial y operativo                   |
| Reducción de redundancia                    | Dependencia del SGBD                        |
| Seguridad y control de acceso               | Rendimiento en grandes volúmenes de datos   |
| Compartición de datos                       | Vulnerabilidades de seguridad               |
| Mantenimiento simplificado                  | Rigidez en el esquema                       |
| Escalabilidad                               | Curva de aprendizaje                        |
| Soporte para toma de decisiones             | Consistencia en entornos distribuidos       |

---

## 🗂️ Tipos de Base de Datos

Las bases de datos se clasifican en diferentes tipos según su modelo de almacenamiento, estructura y funcionalidad. Cada una tiene su propósito y función, todo depende del proyecto en que se trabaje. Existen diversos tipos, estos solo son algunos:

- **📊 Bases de Datos Relacionales:** Organizan datos en relaciones predefinidas, en la que los datos se almacenan en una o más tablas, las cuales están conformadas por columnas y filas, lo que facilita la visualización y la comprensión de cómo se relacionan las diferentes estructuras de datos entre sí.
  
- **📦 Bases de Datos No Relacionales (NoSQL):** Diseñadas para manejar grandes volúmenes de información que no necesariamente se ajustan a un esquema estructurado en tablas, como ocurre en las bases de datos relacionales.

- **🧩 Bases de Datos Orientadas a Objetos:** Almacenan y manipulan información en forma de objetos, tal como se utilizan en la programación orientada a objetos (POO).

- **🌐 Bases de Datos Distribuidas:** Sistemas de gestión de datos en los que la información se almacena en múltiples servidores o ubicaciones físicas, conectados a través de una red.

- **🌳 Bases de Datos Jerárquicas:** Organizan la información en una estructura de árbol, donde cada registro tiene un único padre y puede tener varios hijos.

---

## 🛠️ Sistemas de Gestión de Bases de Datos (SGBD)

Los **Sistemas de Gestión de Bases de Datos (SGBD)**, también conocidos como DBMS (Database Management System), son software diseñados para crear, gestionar y administrar bases de datos, actuando como una interfaz entre la base de datos y los usuarios o aplicaciones que la utilizan, lo que permite almacenar, recuperar, actualizar y gestionar datos de manera eficiente y segura.

Los SGBD son fundamentales en cualquier sistema que maneje datos, ya que simplifican la interacción con las bases de datos y garantizan su integridad, consistencia y seguridad, aplicando reglas y restricciones como claves primarias, claves foráneas y validaciones para evitar duplicaciones y mantener relaciones precisas entre los datos.

Además, permiten a los desarrolladores y usuarios centrarse en la funcionalidad de sus aplicaciones sin preocuparse por los detalles técnicos del almacenamiento y la gestión de datos, ofreciendo herramientas para control de acceso, respaldo y recuperación, optimización del rendimiento y gestión de transacciones, lo que asegura que las operaciones sean atómicas, consistentes, aisladas y duraderas (ACID).

---

## 🧩 Modelado de Base de Datos

El **Modelado de Bases de Datos** es un proceso estructurado que consiste en representar y organizar los datos de manera integral para definir la estructura lógica de una base de datos. Este proceso permite determinar cómo se almacenarán, relacionarán y gestionarán los datos dentro de un sistema, asegurando que sean funcionales, confiables y fáciles de entender tanto para los desarrolladores como para los usuarios finales.

### Niveles de Modelado
1. **🌐 Modelo Conceptual:** Representación abstracta de un sistema, compuesta por conceptos y reglas que permiten representar de manera global los aspectos lógicos de un dominio específico.
2. **📊 Modelo Lógico:** Representación más detallada y estructurada de los datos y sus relaciones, que se deriva del modelo conceptual.
3. **💾 Modelo Físico:** Define cómo se implementarán y almacenarán los datos en un sistema específico, considerando todos los detalles técnicos y de infraestructura.

---

## 🔄 Normalización de Bases de Datos

La **Normalización de Bases de Datos** es un proceso de diseño que organiza los datos en una base de datos relacional para reducir la redundancia, mejorar la integridad y facilitar el mantenimiento. Este proceso consiste en aplicar una serie de reglas o formas normales para estructurar las tablas y sus relaciones de manera eficiente.

### Formas Normales
1. **1️⃣ Primera Forma Normal (1FN):** Asegura que los datos estén organizados de manera atómica y estructurada.
2. **2️⃣ Segunda Forma Normal (2FN):** Elimina dependencias parciales, asegurando que todos los atributos no clave dependan completamente de la clave primaria.
3. **3️⃣ Tercera Forma Normal (3FN):** Elimina las dependencias transitivas, asegurando que ningún atributo no clave dependa de otro atributo no clave.
4. **🔷 Forma Normal de Boyce-Codd (FNBC):** Versión más estricta de la 3FN, aborda dependencias funcionales complejas.
5. **4️⃣ Cuarta Forma Normal (4FN):** Elimina las dependencias multivaluadas no triviales, asegurando que no haya relaciones independientes entre atributos.

---