# Envio-Multiple-Woo Cannactiva
Introducción

Esta documentación describe la implementación de funcionalidades para manejar envíos múltiples en nuestra pagina Checkout, permitiendo a los usuarios elegir métodos de envío diferentes para cada producto en el checkout.

Modificaciones Realizadas:

1. Añadir Opciones de Envío por Producto

Archivo afectado: functions.php

Descripción:
Se añadió una función que muestra opciones de envío para cada producto en el área de revisión del pedido (order review). Esta función se engancha en el hook woocommerce_checkout_cart_item_quantity.

Código:

add_action('woocommerce_checkout_cart_item_quantity', 'cannactiva_add_shipping_options_select', 10, 3);

function cannactiva_add_shipping_options_select($cart_item_quantity, $cart_item, $cart_item_key) {
    // Código incluye la recuperación de métodos de envío y la generación de radio buttons.
}

2. Guardar la Opción de Envío Seleccionada

Archivo afectado: functions.php

Descripción:
Función para guardar la opción de envío seleccionada por el usuario en los metadatos de cada línea de pedido.

Código:

add_action('woocommerce_checkout_create_order_line_item', 'cannactiva_save_delivery_option_to_order_item', 10, 4);

function cannactiva_save_delivery_option_to_order_item($item, $cart_item_key, $values, $order) {
    // Código para guardar el método de envío seleccionado.
}

3. Ocultar Etiquetas de Envío en la Administración

Archivo afectado: functions.php

Descripción:
Ocultar las etiquetas de envío en la interfaz de administración de pedidos para mantener la claridad y evitar confusiones.

Código:

add_action('admin_enqueue_scripts', 'custom_admin_order_styles');

function custom_admin_order_styles() {
    // Código para añadir estilos CSS que ocultan las etiquetas de envío.
}

4. Identificación de Envíos Múltiples

Archivo afectado: functions.php

Descripción:
Detectar y manejar situaciones donde se seleccionan múltiples métodos de envío para un pedido, mostrando un etiquetado especial "Envío Mixto".

Código:

add_filter('woocommerce_package_rates', 'change_shipping_label_on_checkout', 10, 2);
add_filter('woocommerce_order_shipping_to_display_shipped_via', 'change_shipping_display_on_order_details', 10, 2);

// Funciones para cambiar etiquetas y manejar la visualización de múltiples métodos de envío.

5. Ajustes de Visibilidad y Diseño con CSS

Descripción:
Se realizaron ajustes de CSS para mejorar la visibilidad y el diseño de las nuevas opciones en la página de checkout, adaptando también la visualización para dispositivos móviles y PCs.

Conclusión

Estas modificaciones permiten a los usuarios de la tienda seleccionar métodos de envío individuales para cada producto en su pedido, mejorando la flexibilidad y la experiencia de compra. Esta implementación incluye no solo ajustes funcionales sino también visuales para asegurar una integración fluida con el diseño existente de la tienda.
