
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta name="description" content=" - Tecnologia de la mejor calidad, precios accesibles y envío a toda la  Argentina.">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0; padding: 0;
      background: #f8f9fa; color: #111;
      transition: background 0.3s, color 0.3s;
    }
    header {
      background: #111; color: white;
      padding: 15px 30px;
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap;
    }
    header img { height: 50px; }
    nav { display: flex; align-items: center; gap: 20px; flex-wrap: wrap; }
    nav a { color: white; text-decoration: none; font-weight: bold; }
    nav a:hover { color: #00bfff; }
    .telefono { font-size: 14px; color: #00bfff; font-weight: bold; }
    .modo-btn, .carrito-btn {
      margin-left: 10px; padding: 6px 12px;
      border: none; border-radius: 5px;
      cursor: pointer; background: #00bfff; color: white;
      font-weight: bold; transition: 0.3s;
    }
    .modo-btn:hover, .carrito-btn:hover { background: #008ccc; }
    .hero { text-align: center; padding: 60px 20px; background: linear-gradient(to right, #111, #333); color: white; }
    .productos { padding: 40px; }
    .productos-header { text-align: center; margin-bottom: 20px; }
    .productos-header input, .productos-header select {
      padding: 10px; margin: 5px; border-radius: 5px; border: 1px solid #ccc;
    }
    .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
    .card {
      background: white; border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      padding: 20px; text-align: center;
      transition: transform 0.3s;
    }
    .card:hover { transform: translateY(-5px); }
    .card img { width: 100%; max-height: 200px; object-fit: contain; border-radius: 10px; }
    .precio { font-size: 18px; font-weight: bold; margin: 10px 0; color: #00bfff; }
    .btn {
      display: inline-block; background: #00bfff; color: white;
      padding: 10px 20px; border-radius: 5px; text-decoration: none; transition: 0.3s;
      cursor: pointer;
    }
    .btn:hover { background: #008ccc; }
    .stars { color: gold; margin: 5px 0; }
    .opiniones, .faq, .about, .metodos { padding: 40px; text-align: center; background: #eee; }
    .review-form { margin-top: 20px; }
    .review-form input, .review-form textarea, .review-form select {
      width: 100%; max-width: 400px;
      margin: 5px auto; padding: 10px;
      border-radius: 5px; border: 1px solid #ccc;
      display: block;
    }
    .faq details {
      margin: 10px auto; max-width: 600px; text-align: left;
      background: #000; color: white;
      padding: 10px; border-radius: 5px; cursor: pointer;
    }
    footer { background: #fffafa; text-align: center; padding: 20px; }
    footer a { color: #00bfff; margin: 0 10px; text-decoration: none; }
    .whatsapp-float {
      position: fixed; width: 60px; height: 60px; bottom: 20px; right: 20px;
      background-color: #25d366; color: #FFF; border-radius: 50%;
      font-size: 30px; display: flex; justify-content: center; align-items: center;
      transition: 0.3s; box-shadow: 2px 2px 5px rgba(0,0,0,0.3);
    }
    .whatsapp-float:hover { background-color: #20b955; }

  /* 🌙 MODO OSCURO */
    body.dark { background: #111; color: #f1f1f1; }
    body.dark .card { background: #222; color: #f1f1f1; }
    body.dark .opiniones, body.dark .faq, body.dark .about, body.dark .metodos { background: #1a1a1a; }
    body.dark footer { background: #111; color: white; }

  /* 🛒 Carrito */
    .carrito-panel {
      position: fixed; top: 0; right: -100%;
      width: 320px; height: 100%;
      background: white; box-shadow: -3px 0 5px rgba(0,0,0,0.2);
      padding: 20px; transition: 0.3s;
      overflow-y: auto; z-index: 200;
    }
    .carrito-panel.active { right: 0; }
    .carrito-item { border-bottom: 1px solid #ccc; padding: 10px 0; }
    .carrito-total { font-weight: bold; margin-top: 10px; }
    .cerrar-carrito {
      position: absolute; top: 10px; right: 15px;
      background: transparent; border: none;
      font-size: 22px; cursor: pointer; color: #333;
    }
    .cerrar-carrito:hover { color: red; }
  </style>
</head>
<body>
  <header>
    <img src="logo.png" alt="Logo LT TECNOLOGY COMPUTER">
    <nav>
      <a href="#inicio">Inicio</a>
      <a href="#productos">Productos</a>
      <a href="#opiniones">Opiniones</a>
      <a href="#faq">FAQ</a>
      <a href="#contacto">Contacto</a>
      <span class="telefono">📞 +54 381 511-1428</span>
      <button class="modo-btn" id="modoToggle">🌙 Oscuro</button>
      <button class="carrito-btn" id="carritoBtn">🛒 Carrito (<span id="carritoCount">0</span>)</button>
    </nav>
  </header>

  <section class="hero" id="inicio">
    <h2>Los mejores auriculares al mejor precio</h2>
    <p>Calidad de sonido superior y diseños modernos</p>
    <a href="#productos" class="btn">Ver catálogo</a>
  </section>

  <section class="productos" id="productos">
    <div class="productos-header">
      <input type="text" id="buscador" placeholder="Buscar producto...">
      <select id="filtro">
        <option value="todos">Todos</option>
        <option value="gaming">Gaming</option>
        <option value="inalambricos">Inalámbricos</option>
        <option value="musica">Música</option>
        <option value="cables">Cable Red</option>
      </select>
    </div>
    <div class="grid" id="listaProductos">
      <div class="card" data-cat="musica">
        <img src="https://http2.mlstatic.com/D_NQ_NP_781594-MLA91483107156_092025-O.webp" alt="Auricular 1">
        <h3>Teclado Mecánico Womier Sk80 Pantalla Multimedia Gamer Rgb Teclado Kanagawa Negro Idioma Inglés Internacional</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Este teclado Womier de alto rendimiento permite que puedas disfrutar de horas ilimitadas de juegos. Está diseñado especialmente para que puedas expresar tanto tus habilidades como tu estilo. Podrás mejorar tu experiencia de gaming, ya seas un aficionado o todo un experto y hacer que tus jugadas alcancen otro nivel.</p>
        <div class="precio">$150.200</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Teclado">
        <img src="https://http2.mlstatic.com/D_Q_NP_633051-MLA69945633453_062023-F.webp" alt="Teclado 2">
        <h3>Teclado gamer Redragon Kumara K552 QWERTY Red español latinoamérica color negro con luz rainbow</h3>
        <div class="stars">⭐⭐⭐⭐⭐</div>
        <p>Un teclado fuerte
Su construcción está realizada sobre ABS reforzado y placa de acero, que combinado con teclas moldeadas por inyección láser de doble disparo y posteriormente grabadas, generan un producto durable y de excelente calidad, ideal para uso intensivo.</p>
        <div class="precio">$63.900</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="gaming">
        <img src="https://http2.mlstatic.com/D_Q_NP_964954-MLU73992837406_012024-F.webp" alt="Auricular Gamer 3">
        <h3>Auriculares con micrófono para gaming, oficina, estudio Amitosai Ps4 Mts-drop conector plug 3.5mm compatible con consolas y computadoras Color Azul</h3>
        <div class="stars">⭐⭐⭐</div>
        <p>Increíble auricular gamer con el mejor diseño, sonido MUY potente y un micrófono de excelente calidad, con opción mute para poder silenciar justo cuando es necesario.
Funciona perfectamente en consolas Playstation 4, Playstation 4 Pro, Playstation 5 conectándolo directamente al Joystick, sin necesidad de adaptadores. Es un auricular diseñado por nuestro equipo de ingeniería especialmente para ser utilizado en consolas
En el caso de XBOX ONE se puede conectar directamente al Joystick nueva versión, con conector mini plug 3.5mm. También funciona en XBOX SERIES S / X
Perfecto para cualqueir juego.
También sirve para trabajar online, call center, conferencias, Skype, Zoom, etc..</p>
        <div class="precio">$29.900</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
         <div class="card" data-cat="cable">
        <img src="https://http2.mlstatic.com/D_NQ_NP_880520-MLA91482763050_092025-O.webp" alt="Cable red 4">
        <h3>Cable red</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>El Cable De Red Utp Rj-45 30 Mts Directo Internet Pc 5738b es un producto de alta calidad, reconocida por su compromiso con la excelencia y la innovación. Este cable de red es ideal para su uso tanto en interiores como en exteriores, lo que lo hace extremadamente versátil y adaptable a tus necesidades. Viene con conectores incluidos, lo que facilita su instalación y uso. El conector de entrada es RJ-45, un estándar en la industria que garantiza una conexión segura y estable.</p>
        <div class="precio">$15.000</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Mouse">
        <img src="https://http2.mlstatic.com/D_NQ_NP_959277-MLU72641778671_112023-O.webp" alt="Mouse gamer 5">
        <h3>Mouse gamer de juego Redragon Centrophorus2 M601-RGB black</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Mejora tu manera de jugar a tus juegos preferidos.</p>
        <div class="precio">$22.300</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Mouse pad">
        <img src="https://http2.mlstatic.com/D_NQ_NP_824267-MLA84846967779_052025-O.webp" alt="Mouse pad 6">
        <h3>Mouse Pad Gamer Omaigat Evangelion Eva01 Berserk L (600x285x3mm) Violeta</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Personaliza el setup de tu PC o consola de juegos con este increíble pad.
El material es una combinación de goma espuma de alta densidad, una capa de goma antideslizante y tela sintética en la superficie, lo que le da una textura suave pero no resbalosa al pad.
.</p>
        <div class="precio">$13.500</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Mouse inalambricos">
        <img src="https://http2.mlstatic.com/D_NQ_NP_897252-MLA83546107077_042025-O.webp" alt="Mouse inalambrico">
        <h3>Mouse Bluetooth Inalámbrico NEGRO Rgb 2.4 Ghz Recargable Wireless</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>El mouse perfecto para tu vida diaria, ya sea para uso profesional o personal. Dispone de una batería interna recargable mediante cable USB. Este mouse inalámbrico recargable, con un diseño brillante y sofisticado, tiene un clic silencioso, un diseño anatómico y cómodo y una batería interna recargable mediante un cable USB. Ofrece opciones de sensibilidad de 3 dpi para que pueda ajustar la velocidad óptima del cursor en su portátil u ordenador..</p>
        <div class="precio">$10.000</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Mouse">
        <img src="https://http2.mlstatic.com/D_Q_NP_844241-MLA85092740733_052025-F.webp" alt="Cable Hdmi 7">
        <h3>Cable Hdmi 2.1 2 Mts Premium Gamer 4k Hdr Earc 3d 8k Hokobox 8K 60Hz 4K 120Hz 1080p 240Hz Ultra High Speed</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>CABLE HDMI 2.1 HOKOBOX 2 METROS PREMIUM 48GBPS 8K 60HZ 4K 120HZ 1080P 240HZ PS5 XBOX SERIES SMART TV HDR EARC ULTRA HIGH SPEED CON ETHERNET UHD 3D
.</p>
        <div class="precio">$34.999</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Auriculares">
        <img src="https://http2.mlstatic.com/D_NQ_NP_683202-MLA90736236752_082025-O.webp" alt="Auriculares 8">
        <h3>Auricular Bluetooth Air25m Bulltec</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>• Conectividad Bluetooth 5.3.
• Compatibilidad Universal: Funciona con dispositivos Android, iOS, PC, MAC, etc.
• Micrófonos con cancelación de ruido ambiental.
• Brindan sonido estéreo HIFI
• Con una batería de litio de gran capacidad
• Puede cargar teléfonos móviles
• Distancia de Conexión: 15 a 20 metros
• Frecuencia: 2.4GHz
• Pantalla digital incorporad.</p>
        <div class="precio">$10.000</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Auriculares">
        <img src="https://http2.mlstatic.com/D_NQ_NP_883521-MLA92320569115_092025-O.webp" alt="Auriculares 9">
        <h3>Auriculares Bluetooth F9 Pro Bulltec
Agregar a favoritos
</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Inalámbricos
Bluetooth v5.3
Indicador de batería en Pantalla digital
Incluyen powerbank
Compatibles con: iOS y Android.</p>
        <div class="precio">$8.700</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Auriculares">
        <img src="https://http2.mlstatic.com/D_Q_NP_921969-MLU77724619049_072024-F.webp" alt="Auriculares 10">
        <h3>Auricular Bluetooth FanPro F10 PLUS</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>En la calle, en el colectivo o en la oficina, tené siempre a mano tu auricular Fan Pro y ¡escapate de la rutina por un rato! Vas a poder disfrutar de la música que más te gusta y recibir llamadas telefónicas claras donde sea que te encuentres, sin perder contacto con el entorno.

El formato perfecto para vos
Al ser in-ear, mejora la calidad del audio y es de tamaño pequeño para poder insertarse en tu oreja. Es ideal para acompañarte a la hora de hacer ejercicio mientras te sumergís en el mejor sonido envolvente..</p>
        <div class="precio">$15.000</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Auriculares">
        <img src="https://http2.mlstatic.com/D_NQ_NP_701723-MLA89229227487_082025-O.webp" alt="Auriculares 11">
        <h3>Auricular Bluetooth Air41m Bulltec Inalámbricos Violeta</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Auricular Bluetooth AIR41M BULLTEC: la elección perfecta para quienes buscan comodidad, calidad de sonido y tecnología inalámbrica avanzada en un solo accesorio.

Diseño compacto y ergonómico Este auricular Bluetooth AIR41M de BULLTEC presenta un diseño moderno y liviano, ideal para uso prolongado sin molestias. Su estructura ergonómica se adapta perfectamente a tu oído, garantizando comodidad y estabilidad durante todo el día.

Sonido claro y potente Disfrutá de una experiencia sonora superior con graves profundos y agudos nítidos. Perfecto para escuchar música, podcasts o atender llamadas con una calidad de audio excepcional.
.</p>
        <div class="precio">$21.860</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Nuevo Auriculares Bluetooth Cancelación De Ruido Y Pantalla">
        <img src="https://http2.mlstatic.com/D_NQ_NP_2X_981209-CBT94062881963_102025-F.webp" alt="auricular 12">
        <h3>Auriculares Bluetooth con reducción de ruido y pantalla táctil inteligente LCD, resistentes al agua y al sudor, batería de larga duración</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Rango de transmisión: 10 metros
Función: impermeable
Función: Reducción de ruido
Función: Batería de larga duración
Función: control por voz
Función: música de apoyo
Función: pantalla digital
Protocolo Bluetooth: 5.3
Uso: tipo intrauditivo
Ya sea simple y binaural: estéreo bilateral
Duración de la batería: más de 8 horass
Estilo: deportivo
Rendimiento impermeable: IPX5
Material: PC + ABS </p>
        <div class="precio">$30.000</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Soporte">
        <img src="https://http2.mlstatic.com/D_NQ_NP_2X_760284-MLA90648746220_082025-F.webp" alt="Soporte 13">
        <h3>Soporte Porta Celular Funda Impermeable 360° Moto Bici</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p></p>
        <div class="precio">$13.099 </div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
       <div class="card" data-cat="Soporte">
        <img src="https://http2.mlstatic.com/D_NQ_NP_2X_861088-MLA92267570476_092025-F.webp" alt="Soporte 14">
        <h3>Aro Luz Led 36 Cm Selfie 3 Luces + Tripode 2m Profesional Negro Blanco</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Aro de Luz LED para Fotografía y Video

Este aro de luz es una herramienta versátil para mejorar tus fotos y videos. Aquí están sus características principales:

-Tamaño y ajuste: Con un diámetro de 36cm, es lo suficientemente grande para proporcionar una iluminación uniforme. -Viene con una rótula y abrazadera para teléfono para facilitar su montaje en trípodes o soportes.
-Control de luz: Ofrece 3 ajustes de color de temperatura (3200K, 4500K y 6500K) para adaptarse a diferentes condiciones de iluminación. Además, puedes seleccionar entre 10 niveles de brillo para obtener la intensidad deseada.</p>
        <div class="precio">$43.468 </div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Lapiz">
        <img src="https://http2.mlstatic.com/D_NQ_NP_2X_754272-MLA94040989608_102025-F.webp" alt="Lapiz 15">
        <h3>Lápiz 3d Con Filamentos Incluidos Bolígrafo Creativo Dibujo Manualidades Usb Portátil Niños Juguete Educativo Arte Tinta Plástica Diy Escolar Tecnología</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>LÁPIZ 3D IMPRESORA CON FILAMENTOS INCLUIDOS – BOLÍGRAFO CREATIVO PARA MANUALIDADES, DIBUJO Y ARTE EN 3D

Descubre una nueva forma de crear, aprender y divertirte con este bolígrafo 3D profesional, ideal tanto para principiantes como para creativos avanzados. Utiliza tecnología FDM (Modelado por Deposición Fundida) para diseñar figuras tridimensionales, prototipos, decoraciones, arte, manualidades y mucho más.

Este lápiz permite transformar tus ideas en objetos reales, mientras fomenta la imaginación, la motricidad fina y el pensamiento espacial..</p>
        <div class="precio">$18.999</div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      <div class="card" data-cat="Cámara">
        <img src="https://http2.mlstatic.com/D_NQ_NP_2X_878141-MLU75496011759_032024-F.webp" alt="Cámara 16">
        <h3>Set Video Cámara + Timbre Gadnic Con Audio Bidireccional</h3>
        <div class="stars">⭐⭐⭐⭐</div>
        <p>Cámara y Timbre Gadnic con Audio Bidireccional

ACERCA DE ESTE PRODUCTO:

Experimenta la seguridad avanzada en tu hogar con la Cámara y Timbre Gadnic. Equipado con micrófono, detectores de movimiento y sensor de luz, este dispositivo monitorea constantemente su entorno para protección continua. Detecta movimientos sospechosos y tiene una función de detección de humanos para filtrar notificaciones no deseadas.

Captura detalles importantes con su lente gran angular. Su indicador LED y luces infrarrojas proporcionan visión clara en cualquier momento. Con el audio bidireccional, comunícate con visitantes o disuade intrusos desde tu teléfono.

Este dispositivo inteligente y conectado permite el acceso y recepción de notificaciones a través de una aplicación móvil. Cuenta con Bluetooth y Wi-Fi para una conexión estable.

Incluye un botón de timbre que se conecta a tu smartphone, permitiendo responder desde cualquier lugar.

La aplicación posibilita compartir el acceso con familiares o amigos, manteniendo a todos informados sobre la seguridad del hogar.

CARACTERÍSTICAS:

- Micrófono: Sí
- Sensor de movimiento: Sí
- Detección de humanos: Sí
- Gran angular: Sí
- Indicador LED: Sí
- Luces infrarrojas: Sí
- Sensor de luz: Sí
- Botón de timbre: Sí
- Audio bidireccional: Sí
- Puerto micro USB: Sí
- Funciona con la aplicación: Sí
- Bluetooth: Sí
- Wi-Fi: Sí
- Notificaciones: Sí
- Compartir cuentas: Sí

SE ENTREGA CON:

- 1x Timbre con cámara
- 1x Altavoz
- 1x Cable USB
- 1x Manual</p>
        <div class="precio">$68.449 </div>
        <button class="btn addCarrito">Agregar al carrito</button>
      </div>
      
  </section>

  <section class="opiniones" id="opiniones">
    <h2>Opiniones de Clientes</h2>
    <div id="listaReseñas"></div>
    <button class="btn" id="mostrarForm">➕ Escribir Reseña</button>
    <div class="review-form" id="formReseña" style="display:none;">
      <input type="text" id="nombreReseña" placeholder="Tu nombre" required>
      <textarea id="textoReseña" rows="3" placeholder="Escribe tu reseña..." required></textarea>
      <select id="estrellasReseña">
        <option value="5">⭐⭐⭐⭐⭐ (5)</option>
        <option value="4">⭐⭐⭐⭐ (4)</option>
        <option value="3">⭐⭐⭐ (3)</option>
        <option value="2">⭐⭐ (2)</option>
        <option value="1">⭐ (1)</option>
      </select>
      <button class="btn" id="enviarReseña">Enviar Reseña</button>
    </div>
  </section>

  <section class="about" id="about">
    <h2>Sobre Nosotros</h2>
    <p>En 🦾LT TECNOLOGI COMPUTER ofrecemos tecnologia de alta calidad al mejor precio, con atención personalizada y envíos a todo el país🦾.</p>
  </section>

  <section class="faq" id="faq">
    <h2>Preguntas Frecuentes</h2>
    <details><summary>¿Hacen envíos a todo el país?</summary><p>Sí, realizamos envíos a todo Argentina.</p></details>
    <details><summary>¿Qué garantía tienen los auriculares?</summary><p>Todos nuestros productos tienen garantía de 6 meses.</p></details>
    <details><summary>¿Qué métodos de pago aceptan?</summary><p>Aceptamos MercadoPago, Visa, Mastercard y transferencia bancaria.</p></details>
     <details><summary>¿Cual es nuestro horario de antencion al publico?</summary><p>Nuestros horarios de antencion al publico son de 8:30 AM a 13:30 PM luego a la tarde atendemos de 16:30 PM a 21:00</p></details>
  </section>

  <section class="metodos">
    <h2>Métodos de Pago y Envío</h2>
    <p>Pagá seguro con: 💳 Visa | 💳 Mastercard | 💳 MercadoPago</p>
    <p>📦 Envíos con Correo Argentino y Andreani</p>
  </section>

  <section class="contacto" id="contacto">
    <h2>Contáctanos</h2>
    <p>También puedes llamarnos al 📞 <strong>+54 381 511-1428</strong></p>
    <!-- modify this form HTML and place wherever you want your form -->
 <form class="form-register" action="https://formspree.io/f/xqayyvqa" method="POST">
    <h4>FORMULARIO</h4>
    <input class="controls" type="text" name="nombres" id="nombres" placeholder="Ingrese su Nombre">
    <input class="controls" type="text" name="apellidos" id="apellidos" placeholder="Ingrese su Apellido">
    <input class="controls" type="email" name="correo" id="correo" placeholder="Ingrese su Correo">
    <textarea class="controls" name="mensaje" placeholder="Asunto"></textarea>
    <input class="botons" type="submit" value="ENVIAR">
  </form>
  </section>

  <footer>
    <p>&copy; 2025 LT TECNOLOGI COMPUTER 🎮​🎧​🖥️​​📱​​ - Todos los derechos reservados</p>
    <p>Síguenos en: <a href="#">Facebook</a> | <a href="#">Instagram</a> | <a href="#">Twitter</a></p>
    <span class="telefono">📞 +54 381 511-1428</span>
  </footer>

  <!-- BOTÓN WHATSAPP -->
  <a href="https://wa.me/543815111428" class="whatsapp-float" target="_blank">💬</a>

  <!-- PANEL CARRITO -->
  <div class="carrito-panel" id="carritoPanel">
    <button class="cerrar-carrito" id="cerrarCarrito">&times;</button>
    <h3>🛒 Carrito</h3>
    <div id="carritoItems"></div>
    <div class="carrito-total" id="carritoTotal">Total: $00.00
    </div>
  </div>

  <script>
    // 🌙 MODO OSCURO
    const toggleBtn = document.getElementById('modoToggle');
    if(localStorage.getItem('tema') === 'oscuro'){
      document.body.classList.add('dark');
      toggleBtn.textContent = "☀️ Claro";
    }
    toggleBtn.addEventListener('click', () => {
      document.body.classList.toggle('dark');
      if(document.body.classList.contains('dark')){
        toggleBtn.textContent = "☀️ Claro";
        localStorage.setItem('tema','oscuro');
      } else {
        toggleBtn.textContent = "🌙 Oscuro";
        localStorage.setItem('tema','claro');
      }
    });

    // 🔍 BUSCADOR Y FILTRO
    const buscador = document.getElementById('buscador');
    const filtro = document.getElementById('filtro');
    const productos = document.querySelectorAll('#listaProductos .card');
    function filtrar(){
      const texto = buscador.value.toLowerCase();
      const cat = filtro.value;
      productos.forEach(p=>{
        const nombre = p.querySelector('h3').textContent.toLowerCase();
        const categoria = p.dataset.cat;
        p.style.display = (nombre.includes(texto) && (cat==="todos" || categoria===cat)) ? "block" : "none";
      });
    }
    buscador.addEventListener('input', filtrar);
    filtro.addEventListener('change', filtrar);

    // 🛒 CARRITO
    const carritoBtn = document.getElementById('carritoBtn');
    const cerrarCarrito = document.getElementById('cerrarCarrito');
    const carritoPanel = document.getElementById('carritoPanel');
    const carritoItems = document.getElementById('carritoItems');
    const carritoTotal = document.getElementById('carritoTotal');
    const carritoCount = document.getElementById('carritoCount');
    let carrito = [];

    document.querySelectorAll('.addCarrito').forEach((btn)=>{
      btn.addEventListener('click', ()=>{
        const card = btn.parentElement;
        const nombre = card.querySelector('h3').textContent;
        const precio = parseInt(card.querySelector('.precio').textContent.replace(/\D/g,''));
        carrito.push({nombre, precio});
        actualizarCarrito();
      });
    });

    function actualizarCarrito(){
      carritoItems.innerHTML = "";
      let total = 0;
      carrito.forEach(item=>{
        total += item.precio;
        carritoItems.innerHTML += `<div class="carrito-item">${item.nombre} - $${item.precio}</div>`;
      });
      carritoTotal.textContent = "Total: $" + total;
      carritoCount.textContent = carrito.length;
    }

    carritoBtn.addEventListener('click', ()=> carritoPanel.classList.add('active'));
    cerrarCarrito.addEventListener('click', ()=> carritoPanel.classList.remove('active'));

    // ⭐ RESEÑAS CON LOCALSTORAGE
    const mostrarForm = document.getElementById('mostrarForm');
    const formReseña = document.getElementById('formReseña');
    const enviarReseña = document.getElementById('enviarReseña');
    const listaReseñas = document.getElementById('listaReseñas');

    let reseñas = JSON.parse(localStorage.getItem('reseñas')) || [];
    function mostrarReseñas() {
      listaReseñas.innerHTML = "";
      reseñas.forEach(r => {
        listaReseñas.innerHTML += `<p>"${r.texto}" – ${r.nombre} ${"⭐".repeat(r.estrellas)}</p>`;
      });
    }
    mostrarReseñas();

    mostrarForm.addEventListener('click', () => {
      formReseña.style.display = formReseña.style.display === "none" ? "block" : "none";
    });

    enviarReseña.addEventListener('click', ()=>{
      const nombre = document.getElementById('nombreReseña').value.trim();
      const texto = document.getElementById('textoReseña').value.trim();
      const estrellas = parseInt(document.getElementById('estrellasReseña').value);

      if(nombre && texto){
        reseñas.unshift({nombre, texto, estrellas});
        localStorage.setItem('reseñas', JSON.stringify(reseñas));
        mostrarReseñas();
        document.getElementById('nombreReseña').value="";
        document.getElementById('textoReseña').value="";
        formReseña.style.display="none";
      }
    });
  </script>

