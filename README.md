# anti-zoio-v1

### Script
```javascript
javascript:function Object.defineProperty(document, 'visibilityState', { get: function() { return 'visible'; }, configurable: true }); Object.defineProperty(document, 'hidden', { get: function() { return false; }, configurable: true }); const impedirEventos = (e) => { if (['visibilitychange', 'blur', 'mouseleave'].includes(e.type)) { e.stopImmediatePropagation(); e.stopPropagation(); } }; window.addEventListener('visibilitychange', impedirEventos, true); document.addEventListener('visibilitychange', impedirEventos, true); window.addEventListener('blur', impedirEventos, true); const originalAddEventListener = EventTarget.prototype.addEventListener; EventTarget.prototype.addEventListener = function(type, listener, options) { if (['visibilitychange', 'blur', 'mouseleave'].includes(type)) { return;  } return originalAddEventListener.call(this, type, listener, options); }; console.log("Proteção de visibilidade ativada. O site sempre achará que esta aba está em foco.");
```
