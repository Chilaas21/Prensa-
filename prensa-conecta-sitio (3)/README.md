# Prensa Conecta · sitio estático

Archivos: `index.html` (todo el sitio), `assets/logo.png` (logotipo con transparencia real), `netlify.toml`.

## Ejecutar localmente
`python3 -m http.server 8000` dentro de esta carpeta y abrir http://localhost:8000
(Netlify Forms sólo funciona ya publicado en Netlify; en local el respaldo mostrará "no se pudo guardar".)

## Configuración central (inicio del `<script>` en index.html)
- `CONFIG.whatsapp`: número de 10 dígitos (hoy 7298568419). El 52 se antepone automáticamente.
- `CONFIG.email`: vacío. No existe correo configurado.
- `CONFIG.mostrarDemo`: `false` oculta los negocios de demostración.
- `NEGOCIOS`: datos del directorio. Domicilio: `dom:{o:"si"|"no",t:"gratis|fijo|distancia|pedido|consultar",m:35,n:"nota"}`. Sin `dom` se muestra "Servicio a domicilio por confirmar".

## Publicar en Netlify
1. Netlify > tu sitio > Deploys > arrastra esta carpeta completa (con `assets/`) o conecta el repositorio.
2. Site configuration > Forms > confirma que "Form detection" esté activado (en sitios nuevos suele estarlo; si no, actívalo y vuelve a desplegar).
3. Tras el despliegue, Forms debe listar `registro-negocio`. Haz un envío de prueba y revisa Forms > registro-negocio > Submissions.
4. Notificaciones (opcional, no vienen activadas): Forms > Form notifications > Add notification > Email. Se hace en tu cuenta de Netlify.

## Datos y administración (actualización de demostración)
Todo se edita en `index.html`, bloque `NEGOCIOS`, `PROMOS` y `BANNERS` (comentados en el código). Fotos: guárdalas en `assets/` y usa `foto:"assets/nombre.jpg"`.
- Estados de negocio: `borrador` (oculto), `pendiente` (con etiqueta; sólo si `CONFIG.mostrarPendientes:true`), `publicado`. Para producción pon `mostrarPendientes:false` y `mostrarDemo:false`.
- Banner: estados `borrador | demo | publicado | archivado`; retirar = poner `estado:"archivado"` o una `fin` pasada.
- WhatsApp autorizado de un negocio: `w:"5512345678"` (sin él, el botón no aparece).
- Calificaciones: la interfaz es sólo demostración (se guarda en el dispositivo). `cal:{prom,n}` está reservado para resultados reales.
