# Release notes Mercado Pago 2018

Cada release note describe los cambios que aplican a una versión. Estos cambios pueden incluir:

- **Actualizaciones en APIs:** lanzamiento, modificación o eliminación de recursos, parámetros o campos en nuestras APIs.

- **Nuevos productos o funcionalidades:** Lanzamiento de herramientas que harán que puedas aceptar pagos de forma más fácil.

- **Anuncios:** Novedades relacionadas a alguno de nuestros productos o cambios a futuro.

- **Actualizaciones en la documentación:** Guías, referencias y tutoriales para ayudarte a monetizar tu negocio integrando Mercado Pago.


## 10 de diciembre de 2018

En Mercado Pago buscamos siempre optimizar nuestra plataforma ofreciendo la más alta eficiencia y seguridad en el procesamiento de pagos.

En esta ocasión, estamos trabajando en la migración de nuestra API versión 0 a la versión 1 con el objetivo de mantener los más altos estándares de calidad.

Después de ese plazo, la versión 0 dejara de tener soporte.

La migración afecta a los siguientes recursos:

| Uso                     | Método | URI del Recurso deprecado                | URI del Recurso equivalente        |
|-------------------------|--------|------------------------------------------|------------------------------------|
| Devoluciones            | `POST` | /collections/`$payment_id`/refunds       | /v1/payments/`$payment_id`/refunds |
| Devoluciones            | `PUT`  | /collections/`$payment_id`               | /v1/payments/`$payment_id`/        |
| Actualización de pagos  | `PUT`  | /payments/`$payment_id`                  | /v1/payments/`$payment_id`/        |
| Actualización de pagos  | `PUT`  | /collections/`$payment_id`               | /v1/payments/`$payment_id`/        |
| Pagos                   | `GET`  | /payments/`$payment_id`                  | /v1/payments/`$payment_id`/        |
| Pagos                   | `GET`  | /collections/`$payment_id`               | /v1/payments/`$payment_id`/        |
| Notificaciones de pagos | `GET`  | /collections/notifications/`$payment_id` | /v1/payments/`$payment_id`/        |
| Búsqueda de pagos       | `GET`  | /payments/search                         | /v1/payments/search                |
| Búsqueda de pagos       | `GET`  | /collections/search                      | /v1/payments/search                |

Más información [en este artículo](https://www.mercadopago.com.ar/developers/es/guides/localization/migrating-v0-v1).

## 13 de septiembre de 2018

**Apagado de Mercado Envíos para integraciones de Mercado Pago en Brasil**

Por problemas de performance se decidió el apagado de la funcionalidad de Mercado Envíos para  integraciones de Mercado Pago en Brasil.

Mercado Envíos dentro de la plataforma de Mercado Libre seguirá funcionando con normalidad.

Por favor tener en cuenta que este cambio puede tener afectación sobre algunas integraciones realizadas con anterioridad, en tal caso solicitamos te contactes con nuestro equipo de soporte indicando la/las cuentas con las que operabas para que tu caso pueda ser analizado  en particular.

## 30 de Junio de 2018

- Estamos trabajando en el **apagado de TLS 1.0** para los dominios [https://api.mercadopago.com](https://api.mercadopago.com) y [https://pagamento.mercadopago.com](https://pagamento.mercadopago.com) con el objetivo de mantener los más altos estándares de calidad y promover la seguridad de los datos de nuestros clientes.

- A partir  del 30 de Junio del 2018 requeriremos que las conexiones a esos dominios sean a través del protocolo de cifrado TLS 1.1 o superior. Más información en [este artículo](https://www.mercadopago.com.ar/developers/es/guides/pci-compliant-merchants/disabling-tls-10)


## 14 de Junio de 2018


Por Information Disclosure de los datos de contacto de los usuarios, vamos a ocultar la información del `payer` para todos los casos, salvo pagos aprobados.

Es decir, cualquier `GET` o `POST` a **/v1/payments** de un pago no aprobado, pasará a ser similar a este:

```json
...
    "payer": {
        "type": null,
        "id": 12345,
        "email": null,
        "identification": {
            "type": null,
            "number": null
        },
        "phone": {
            "area_code": null,
            "number": null,
            "extension": null
        },
        "first_name": null,
        "last_name": null,
        "entity_type": null
    },
```



- **¿Qué pasa con sandbox?**: Vamos a devolver datos mock y estáticos de los usuarios.
- Estos cambios aplican **sólo a pagos fuera de la plataforma Mercado Libre.**
- Estos cambios tendrán impacto a partir del Jueves 16 de Junio.
