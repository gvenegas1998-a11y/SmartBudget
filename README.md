JUSTIFICACIÓN METODOLÓGIA Y ARQUITECTURA WEB DE SMARTBUDGET

1. Reflexión sobre el Rol del Desarrollador Front-End (Lección 1)
El rol del desarrollador Front-End en el ciclo de vida de un producto digital es el de actuar como el puente crítico entre la visión conceptual y estética del equipo de diseño (Figma) y una solución tecnológica real, interactiva, accesible y comercialmente viable.
Este rol no se limita a una traducción literal o "copia" de elementos visuales a código, sino que implica una toma de decisiones constante basada en buenas prácticas:
    *	Garantizar la accesibilidad y el SEO: Mediante el uso estricto de HTML5 semántico para que el sitio sea legible tanto por motores de búsqueda como por tecnologías asistivas (lectores de pantalla).
    *	Optimización del rendimiento: Asegurar que los recursos visuales, hojas de estilo y scripts carguen con la máxima velocidad y eficiencia.
    *	Diseño adaptativo: Lograr que la experiencia de usuario sea fluida, lógica y estéticamente impecable en cualquier resolución, desde el dispositivo móvil más compacto hasta pantallas de escritorio de gran formato.
En conclusión, el Front-End transforma maquetas estáticas en experiencias dinámicas, asegurando que el producto digital final cumpla con los estándares técnicos de la industria moderna.


2. Justificación de la Metodología CSS Seleccionada: BEM (Lección 2)
Para la organización y nomenclatura de los estilos de SmartBudget, se seleccionó la metodología BEM Esta decisión se fundamenta en tres pilares técnicos:
    *	Escalabilidad y Mantenibilidad: Al estructurar el código en bloques independientes (como .hero o .feature-card), el proyecto queda preparado para crecer. Se pueden añadir nuevas secciones o páginas completas en el futuro sin temor a que las reglas CSS se "peleen" entre sí o generen efectos colaterales por cascada accidental.
    *	Legibilidad Inmediata: La nomenclatura que utiliza dobles guiones bajos (__) para elementos y dobles guiones medios (--) para modificadores permite que cualquier desarrollador entienda la jerarquía visual del sitio con solo leer las clases en el HTML (ej: .hero__title es claramente el título dentro del bloque hero).
    *	Coexistencia Armónica con Bootstrap: Dado que el proyecto integra Bootstrap 4, usar BEM evita la sobreescritura accidental de clases globales del framework. Al aplicar clases específicas creadas bajo la metodología BEM, se incrementa la especificidad de manera limpia y controlada cuando se requiere personalizar un componente nativo.


3. Lógica de la Estructura SASS y el Patrón 7-1 (Lección 3)
Para gestionar los estilos de forma modular, limpia y eficiente, se implementó el preprocesador SASS bajo una arquitectura inspirada en el Patrón 7-1. Este patrón distribuye el código en carpetas especializadas que dividen las responsabilidades del diseño:
    *	scss/abstracts/: Contiene archivos que no generan CSS directamente al compilar, sino que almacenan herramientas y configuraciones. Aquí se ubica _variables.scss, centralizando la paleta de colores de la marca, las fuentes tipográficas y las escalas de espaciado.
    *	scss/base/: Define las reglas globales del sitio, tales como el reseteo de márgenes (_reset.scss) y los comportamientos por defecto de la tipografía base (_typography.scss).
    *	scss/layout/: Alberga los estilos de las macro-secciones compartidas o estructurales de la landing page, como la sección principal de bienvenida (_hero.scss) y el pie de página (_footer.scss).
    *	scss/components/: Dedicado a piezas visuales más pequeñas, atómicas y altamente reutilizables en todo el sitio, tales como botones personalizados (_buttons.scss), tarjetas de beneficios (_cards.scss) y las ventanas emergentes (_modals.scss).
Todos estos módulos son centralizados e importados mediante la directiva @import en un único archivo raíz llamado main.scss, el cual se compila eficientemente en un solo archivo css/main.css optimizado para el navegador.


4. Control de Layout y Modelo de Cajas (Lección 4)
El diseño responsivo y la distribución espacial de SmartBudget se implementaron bajo estrictas reglas del modelo de cajas y técnicas modernas de CSS:
    *	Alineación con Flexbox: Se utilizó Flexbox para resolver problemas complejos de alineación vertical y distribución de elementos internos (como centrar el texto del Hero respecto a la imagen o alinear el contenido de las tarjetas de beneficios).
    *	Estrategia Mobile-First y Media Queries: Los layouts se diseñaron pensando en la adaptabilidad móvil. Mediante el uso de puntos de quiebre (breakpoints) estratégicos, los elementos que se muestran en columnas horizontales en pantallas de escritorio se reorganizan fluidamente en filas verticales en dispositivos móviles para evitar desbordamientos y mantener la legibilidad de los textos.
    *	Propiedades del Modelo de Cajas: Se aplicó de forma global la propiedad box-sizing: border-box para asegurar que los cálculos de padding y border no alteren el ancho total asignado a los contenedores, evitando errores de maquetación comunes.


5. Integración Eficiente de Bootstrap 4 (Lección 5)
La incorporación de Bootstrap 4 se realizó con el objetivo de acelerar el desarrollo y garantizar la consistencia visual de los componentes estándar de la interfaz:
    *	Estructura Base: Se aprovechó el potente sistema de grillas nativo (.container, .row, .col-*) para resolver la adaptabilidad macro del sitio sin necesidad de escribir código CSS repetitivo.
    *	Componentes Clave Reutilizados: Se integraron de forma limpia componentes robustos como la barra de navegación responsiva (.navbar), las tarjetas contenedoras de información (.card) y el sistema interactivo de ventanas emergentes (.modal) para el formulario de registro.
    *	Cero Sobreescritura Innecesaria: En lugar de alterar drásticamente el código de Bootstrap, se utilizaron sus clases utilitarias de espaciado (como mb-5 o py-4) combinadas con selectores BEM propios, manteniendo el código limpio, desacoplado y profesional.
