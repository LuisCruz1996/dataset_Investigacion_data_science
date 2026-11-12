# Precios de combustibles en Guatemala: compras de una estación de servicio

Dataset de apoyo para el proyecto de investigación *Anticipación de los cambios de precio de compra de combustibles en una estación de servicio de Guatemala*, del curso Investigación en Data Science (Universidad Galileo).

## Pregunta de investigación

¿En qué medida los precios internacionales y el tipo de cambio permiten anticipar los cambios de precio de compra de combustibles de una estación de servicio en Guatemala, y con cuánta antelación respecto al momento en que la estación conoce el nuevo precio?

## Contenido

| Archivo | Descripción |
|---|---|
| `datos/Dataset_Compras_Combustible.xlsx` | Libro con LEEME, detalle por producto y resumen por tancada |
| `datos/compras_estacion/detalle_producto.csv` | Una fila por tancada y producto, con galones, costo unitario, IDP y totales |
| `datos/compras_estacion/resumen_tancada.csv` | Una fila por tancada, con galones, flete, total de compra, vencimiento y pago |
| `datos/fuentes_externas/` | Plantillas para precios de referencia del MEM, precios de la Costa del Golfo y tipo de cambio, pendientes de completar, y el archivo de periodos de subsidio y exención fiscal de 2026 |

## Cobertura

- Compras del 30 de diciembre de 2025 al 8 de noviembre de 2026.
- 90 tancadas y 251 filas de detalle por producto.
- Productos: diésel, gasolina regular y gasolina súper.
- Unidades: quetzales por galón para valores unitarios, quetzales para totales y galones para volumen.

## Depuración

1. Cada archivo mensual original repite la última compra del mes anterior con la fecha corrida un mes. Se conservó solo la compra en su mes original.
2. Se excluyeron los días sin compra.
3. Los códigos no son únicos entre meses, por eso `id_tancada` combina fecha y código.
4. Los galones por mes coinciden con los totales de los archivos originales.

## Alertas conocidas

- Desde el 1 de octubre de 2026 el IDP aparece en 0 porque el Decreto 22-2026 exime el IDP y el IVA de los combustibles del 1 de octubre al 31 de diciembre de 2026. La columna `exencion_idp_iva` marca esas compras y conviene usar el costo unitario sin IDP.
- El IDP de regular baja a 4.14 desde el 29 de agosto porque entró la gasolina regular con etanol al 10 %, ya que el impuesto se aplica a 90 % de la mezcla. La columna `mezcla_etanol_e10` marca la gasolina regular desde el 29 de agosto, incluso durante la exención, y corresponde a un cambio de producto.
- En tres tancadas el total de compra registrado es menor a tancada más flete por un valor igual al IDP.
- Faltan fechas de pago o interés en varias tancadas.
- La estación conoce el precio de compra solo al recibir la factura. La fecha de factura es el proxy del momento en que se conoce el precio.

## Privacidad

El nombre de la estación no se incluye. Bancos, personas y transportistas se reemplazaron por códigos.

## Fuentes externas por completar

- Precios de referencia semanales del Ministerio de Energía y Minas de Guatemala.
- Precios spot de la Costa del Golfo de Estados Unidos de la EIA.
- Tipo de cambio de referencia del Banco de Guatemala.
- Fecha de fin del subsidio del Decreto 11-2026, a confirmar en fuentes oficiales.

## Autor

Luis Manuel Cruz Chatá
