# anti-zoio-v1

### o site n percebe q foi ausentado 
```javascript
Object.defineProperty(document,'visibilityState',{get:function(){return'visible'},configurable:false});Object.defineProperty(document,'hidden',{get:function(){return false},configurable:false});const impedirEventos=e=>{if(['visibilitychange','blur','mouseleave'].includes(e.type)){e.stopImmediatePropagation();e.stopPropagation()}};window.addEventListener('visibilitychange',impedirEventos,true);document.addEventListener('visibilitychange',impedirEventos,true);window.addEventListener('blur',impedirEventos,true);window.addEventListener('mouseleave',impedirEventos,true);const originalAddEventListener=EventTarget.prototype.addEventListener;EventTarget.prototype.addEventListener=function(type,listener,options){if(['visibilitychange','blur','mouseleave'].includes(type))return;return originalAddEventListener.call(this,type,listener,options)};function liberarSelecaoECopia(){const style=document.createElement('style');style.id='liberar-selecao-estilo';style.textContent='*,*::before,*::after{user-select:text!important;-webkit-user-select:text!important;-moz-user-select:text!important;-ms-user-select:text!important}img{user-drag:auto!important;-webkit-user-drag:auto!important;pointer-events:auto!important}';document.documentElement.appendChild(style);const eventosBloqueados=['contextmenu','selectstart','copy','cut','dragstart','mousedown'],permitirEvento=e=>{e.stopImmediatePropagation()};eventosBloqueados.forEach(evento=>{window.addEventListener(evento,permitirEvento,true);document.addEventListener(evento,permitirEvento,true)});document.querySelectorAll('*').forEach(el=>{el.oncontextmenu=null;el.onselectstart=null;el.ondragstart=null;el.oncopy=null;el.oncut=null;el.style.setProperty('user-select','text','important');el.style.setProperty('-webkit-user-select','text','important')})}liberarSelecaoECopia();

```
# personalizar bookmarklet 

```javascript
javascript:(()=>{fetch('XXXteu bookmarklet raw aqXXX').then(r=>r.text()).then(eval).catch(console.error)})()

```
