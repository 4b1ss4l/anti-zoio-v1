# anti-zoio-v1

### Script
```javascript
Object.defineProperty(document, 'visibilityState', { get: function() { return 'visible'; }, configurable: false });
Object.defineProperty(document, 'hidden', { get: function() { return false; }, configurable: false });
const impedirEventos = (e) => {
    if (['visibilitychange', 'blur', 'mouseleave'].includes(e.type)) {
        e.stopImmediatePropagation();
        e.stopPropagation();
    }
};
window.addEventListener('visibilitychange', impedirEventos, true);
document.addEventListener('visibilitychange', impedirEventos, true);
window.addEventListener('blur', impedirEventos, true);
window.addEventListener('mouseleave', impedirEventos, true);
const originalAddEventListener = EventTarget.prototype.addEventListener;
EventTarget.prototype.addEventListener = function(type, listener, options) {
    if (['visibilitychange', 'blur', 'mouseleave'].includes(type)) {
        return;
    }
    return originalAddEventListener.call(this, type, listener, options);
};
console.log("Proteção de visibilidade ativada. O site sempre achará que esta aba está em foco.");

```

```javascript
javascript:(()=>{fetch('XXXteu bookmark raw aqXXX').then(r=>r.text()).then(eval).catch(console.error)})()

```
