# trigger-ajuda-checkout
## Como Configurar Trigger de ajuda por tempo determinado no checkout
Visitar pagina de edição de Checkout: https://minhaloja.myvtex.com/admin/portal/#/sites/default/code/templates/checkout-header

Inserir o seguinte codigo HTML em seu arquivo: checkout-header

```HTML
<div class="precisa-ajuda">
<span class="close-button">x</span>
<div class="chat-image">
<img src="URL_IMAGEM_50x50"/>
</div>
<div class="chat-text">
<span class="first">Precisa de Ajuda?</span><br><span class="second">Nós podemos te ajudar a finalizar sua compra!</span></div>
</div>
```


Inserir o seguinte codigo CSS em seu arquivo: checkout5-custom.css ou checkout6-custom.css
```CSS
.precisa-ajuda{background-color:#1f1f1fab;padding:20px;height:90px;width:300px;color:#fff;bottom:-100px;position:fixed;left:10px;font-family:arial;border-radius:5px;z-index:999;}.chat-image,.chat-text{display:inline-block;float:left;cursor:pointer}.chat-image{width:20%}.chat-text{width:80%}.chat-text span.first{font-size:1rem;font-weight:700;float:left}.chat-text span.second{font-size:.9rem;float:left}.close-button{cursor:pointer;position:absolute;top:5px;right:10px;color:#fff}
@media screen and (max-width:736px){.precisa-ajuda{display:none}}
```

Inserir o seguinte codigo JS em seu arquivo: checkout5-custom.js ou checkout6-custom.js
Obs: Trocar os termos: 
- LINK_PARA_SEU_CHAT : Link do chat de sua loja
- NOME_LOJA : Nome de sua loja
- TEMPO_ESTIPULADO : Tempo para que a trigger mostre a mensagem (em milisegundos, ex: 30s = 30000)
```Javascript
function openChatBot(){mywindow=window.open("LINK_PARA_SEU_CHAT","Atendimento - NOME_LOJA","location=1,status=1,scrollbars=0,resizable=0,width=357,height=560");mywindow.moveTo(0,0)};
$(window).on('load', function(){
setTimeout(function(){$(".precisa-ajuda").animate({bottom:"20px"})},TEMPO_ESTIPULADO);$(".chat-image,.chat-text").click(openChatBot);$(".close-button").click(function(){$(".precisa-ajuda").hide()})
})
```
