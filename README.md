# anti-zoio-v1
´´´javascript

// 1. Bloqueia a alteração do estado de visibilidade
Object.defineProperty(document, 'visibilityState', {
    get: function() { return 'visible'; },
    configurable: true
});

Object.defineProperty(document, 'hidden', {
    get: function() { return false; },
    configurable: true
});

// 2. Intercepta e impede o disparo de eventos de ocultação
const impedirEventos = (e) => {
    if (['visibilitychange', 'blur', 'mouseleave'].includes(e.type)) {
        e.stopImmediatePropagation();
        e.stopPropagation();
    }
};

// Remove ouvintes existentes (captura ampla)
window.addEventListener('visibilitychange', impedirEventos, true);
document.addEventListener('visibilitychange', impedirEventos, true);
window.addEventListener('blur', impedirEventos, true);

// 3. Sobrescreve o addEventListener padrão para ignorar novas tentativas de monitoramento
const originalAddEventListener = EventTarget.prototype.addEventListener;
EventTarget.prototype.addEventListener = function(type, listener, options) {
    if (['visibilitychange', 'blur', 'mouseleave'].includes(type)) {
        return; // Ignora o registro do script do site
    }
    return originalAddEventListener.call(this, type, listener, options);
};

console.log("Proteção de visibilidade ativada. O site sempre achará que esta aba está em foco.");

´´´
