# VPN-Beta
````javascript
javascript:(()=>{
if(document.getElementById('vpn-proxy-bookmarklet')) return;
const style=document.createElement('style');
style.innerHTML=`
#vpn-proxy-bookmarklet{position:fixed;bottom:10px;right:10px;background:#111;color:#fff;border:2px solid #0f0;padding:10px;border-radius:8px;z-index:999999;font-family:sans-serif;width:280px;}
#vpn-proxy-bookmarklet h2{margin:0 0 8px 0;font-size:16px;text-align:center;}
#vpn-proxy-bookmarklet select,#vpn-proxy-bookmarklet input{width:100%;margin-bottom:6px;padding:4px;border:none;border-radius:4px;}
#vpn-proxy-bookmarklet button{width:49%;padding:5px;border:none;border-radius:4px;background:#0f0;color:#000;cursor:pointer;}
#vpn-proxy-bookmarklet button.close{background:#f00;color:#fff;}
`;
document.head.appendChild(style);
const div=document.createElement('div');
div.id='vpn-proxy-bookmarklet';
div.innerHTML=`
<h2>Proxy VPN Web</h2>
<select id="proxy-server">
  <option value="https://www.proxysite.com/?u=">🇺🇸 ProxySite (USA)</option>
  <option value="https://hidester.com/proxy/?u=">🇪🇺 Hidester (EU)</option>
  <option value="https://www.croxyproxy.com/?url=">🌍 CroxyProxy (Global)</option>
  <option value="https://www.filterbypass.me/?url=">🇬🇧 FilterBypass (UK)</option>
</select>
<input id="proxy-url" placeholder="https://site.com">
<div style="display:flex;gap:2%;">
<button id="open-proxy">Abrir</button>
<button class="close">Fechar</button>
</div>
`;
document.body.appendChild(div);
document.getElementById('open-proxy').onclick=()=>{
const server=document.getElementById('proxy-server').value;
const url=document.getElementById('proxy-url').value.trim();
if(!url)return alert('Digite um site válido!');
window.open(server+encodeURIComponent(url),'_blank');
};
div.querySelector('.close').onclick=()=>div.remove();
})();
