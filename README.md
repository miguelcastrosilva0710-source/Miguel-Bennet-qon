<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Site Encerrado</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
body { font-family: 'Inter', sans-serif; margin:0; background:#000; color:white; overflow-x:hidden; }
canvas { position:fixed; top:0; left:0; width:100%; height:100%; z-index:0; pointer-events:none; }
.fade-slide { opacity:0; transform:translateY(20px); animation: fadeSlideIn 1s forwards; }
@keyframes fadeSlideIn { 0% {opacity:0; transform:translateY(20px);} 100%{opacity:1; transform:translateY(0);} }

/* Ícone flutuante */
@keyframes floatIcon {0%,100%{transform:translateY(0);}50%{transform:translateY(-8px);}}
@keyframes glowPulse {0%,100%{text-shadow:0 0 8px #ff5555;}50%{text-shadow:0 0 20px #ff5555;}}
.icon-float { animation: floatIcon 3s ease-in-out infinite, glowPulse 2s ease-in-out infinite; }

/* Discord */
.discord-icon { transition: transform 0.3s ease, filter 0.3s ease; }
@keyframes rotatePulseDiscord {
 0% { transform: scale(1) rotate(0deg); filter: drop-shadow(0 0 4px #5865F2); }
 25% { transform: scale(1.1) rotate(90deg); filter: drop-shadow(0 0 6px #5865F2); }
 50% { transform: scale(1.2) rotate(180deg); filter: drop-shadow(0 0 10px #5865F2); }
 75% { transform: scale(1.1) rotate(270deg); filter: drop-shadow(0 0 6px #5865F2); }
 100% { transform: scale(1) rotate(360deg); filter: drop-shadow(0 0 4px #5865F2); }
}
.discord-btn:hover .discord-icon { animation: rotatePulseDiscord 1s ease-in-out infinite; }

/* Status pulse */
@keyframes pulseStatus {0%,100%{transform:scale(1);opacity:1;}50%{transform:scale(1.2);opacity:0.7;}}
.pulse-status { animation: pulseStatus 1s infinite cubic-bezier(0.4,0,0.6,1); }

/* Botões de contato */
.contact-btn { display:inline-flex; align-items:center; gap:0.5rem; padding:0.75rem 1.5rem; border-radius:0.75rem; font-weight:600; transition:all 0.2s; border:1px solid; }
.contact-btn:hover { transform:translateY(-2px); }

/* Caixa info */
.info-box { background: linear-gradient(135deg, rgba(30,30,40,0.9), rgba(50,0,50,0.8)); border:1px solid #333; border-radius:1rem; padding:1.5rem; box-shadow:0 8px 20px rgba(0,0,0,0.5); margin-bottom:1.5rem; position:relative; overflow:hidden; color:white; }
.info-box::after { content:""; position:absolute; top:-50%; left:-50%; width:200%; height:200%; pointer-events:none; background: linear-gradient(45deg, rgba(255,0,0,0.15) 0%, rgba(255,0,0,0.05) 20%, transparent 50%, rgba(255,0,0,0.05) 80%, rgba(255,0,0,0.15) 100%); transform: translateX(-100%) translateY(-100%); animation: moveRedSlash 3s linear infinite; }
@keyframes moveRedSlash {0%{transform:translateX(-100%) translateY(-100%);}100%{transform:translateX(100%) translateY(100%);}}

/* Links sem preview */
.all-links { cursor:pointer; text-decoration:none; }
.all-links:hover { text-decoration:underline; }

/* Pseudo-páginas */
.section.hidden { display:none; }
.section.active { display:block; }
</style>
</head>
<body>
<canvas id="rainCanvas"></canvas>

<div class="relative max-w-3xl w-full mx-auto text-center space-y-8" style="position:relative; z-index:10; padding-top:60px; padding-bottom:60px;">

  <!-- Ícone -->
  <div class="mb-6 icon-float">
    <div class="inline-flex items-center justify-center w-20 h-20 bg-gray-900 rounded-full border border-gray-800 shadow-2xl">
      <span class="text-6xl">❌</span>
    </div>
  </div>

  <!-- Título -->
  <h1 class="text-4xl md:text-6xl font-bold text-white mb-2 fade-slide" style="animation-delay:0.2s">
    <%= store.settings.title %>
  </h1>
  <h2 class="text-3xl md:text-5xl font-extrabold mb-4 text-red-500 fade-slide" style="animation-delay:0.4s">
    Projeto Encerrado
  </h2>
  <p class="text-lg md:text-xl text-gray-400 mb-8 font-light fade-slide" style="animation-delay:0.6s">
    Este projeto foi descontinuado permanentemente em <time datetime="2025-10-19">19/10/2025</time>
  </p>

  <!-- Conteúdo principal -->
  <div id="conteudo-principal">
    <div id="home-section" class="section active fade-slide" style="animation-delay:0.8s">
      <div class="info-box">
        <h3 class="text-yellow-400 font-semibold text-xl mb-3">Aviso Importante</h3>
        <p class="text-gray-300 leading-relaxed mb-4">
          Nosso projeto com a empresa Mginex foi encerrado permanentemente. Confira nosso novo site:
          <span class="text-yellow-400 hover:text-yellow-300 font-medium underline decoration-dotted all-links" data-target="site-novo">
            https://qon.erby.site/
          </span>
        </p>
      </div>

      <div class="info-box">
        <h3 class="text-blue-400 font-semibold text-lg mb-2">Informação Adicional #1</h3>
        <p class="text-gray-300">Espaço para notas, links ou detalhes relevantes.</p>
        <button class="text-blue-400 all-links mt-2" data-target="info1">Ver detalhes →</button>
      </div>
      <div class="info-box">
        <h3 class="text-green-400 font-semibold text-lg mb-2">Informação Adicional #2</h3>
        <p class="text-gray-300">Atualizações, lembretes ou observações extras.</p>
        <button class="text-green-400 all-links mt-2" data-target="info2">Ver detalhes →</button>
      </div>
      <div class="info-box">
        <h3 class="text-purple-400 font-semibold text-lg mb-2">Informação Adicional #3</h3>
        <p class="text-gray-300">Mais conteúdos que você quiser mostrar aos visitantes.</p>
        <button class="text-purple-400 all-links mt-2" data-target="info3">Ver detalhes →</button>
      </div>
    </div>

    <div id="info1" class="section hidden fade-slide" style="animation-delay:0.8s">
      <h1 class="text-3xl text-blue-400 font-semibold mb-4">Informação Adicional #1</h1>
      <p class="text-gray-300 mb-6">Aqui você coloca o conteúdo completo da primeira seção.</p>
      <button class="text-yellow-400 all-links" data-target="home-section">← Voltar</button>
    </div>

    <div id="info2" class="section hidden fade-slide" style="animation-delay:0.8s">
      <h1 class="text-3xl text-green-400 font-semibold mb-4">Informação Adicional #2</h1>
      <p class="text-gray-300 mb-6">Aqui você coloca o conteúdo completo da segunda seção.</p>
      <button class="text-yellow-400 all-links" data-target="home-section">← Voltar</button>
    </div>

    <div id="info3" class="section hidden fade-slide" style="animation-delay:0.8s">
      <h1 class="text-3xl text-purple-400 font-semibold mb-4">Informação Adicional #3</h1>
      <p class="text-gray-300 mb-6">Aqui você coloca o conteúdo completo da terceira seção.</p>
      <button class="text-yellow-400 all-links" data-target="home-section">← Voltar</button>
    </div>
  </div>

  <!-- Contatos -->
  <div class="flex flex-col sm:flex-row gap-4 justify-center items-center fade-slide" style="animation-delay:1.8s">
    <button 
       class="contact-btn bg-gray-800 text-gray-300 border-gray-700 hover:bg-gray-700 hover:text-white hover:border-gray-600 no-underline-link"
       onclick="window.location.href='mailto:miguelbennet42@gmail.com'">
      <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" 
              d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
      </svg>
      E-mail de contato (clique aqui)
    </button>

    <button
       class="discord-btn contact-btn bg-gray-800 text-gray-300 border border-gray-700 flex items-center gap-2 px-4 py-2 rounded-lg transition hover:bg-gray-700 no-underline-link"
       onclick="window.open('https://discord.gg/qon', '_blank')">
      <img src="https://www.svgrepo.com/show/353655/discord-icon.svg"
           alt="Discord"
           class="discord-icon w-5 h-5">
      Abra ticket!
    </button>
  </div>

  <div class="text-center mt-8 fade-slide" style="animation-delay:2s">
    <p class="text-gray-500 text-sm">Agradecemos sua compreensão.</p>
    <p class="text-gray-600 text-xs mt-2">© <%= new Date().getFullYear() %> <%= store.settings.title %>. Todos os direitos reservados.</p>
  </div>
</div>

<script>
// Controle das pseudo-páginas
document.querySelectorAll('.all-links').forEach(el => {
  el.addEventListener('click', () => {
    const target = el.getAttribute('data-target');
    if (target === "site-novo") {
      window.open('https://qon.erby.site/', '_blank');
    } else if (target) {
      document.querySelectorAll('.section').forEach(sec => sec.classList.add('hidden'));
      document.getElementById(target).classList.remove('hidden');
    }
  });
});

// Chuva
const canvas = document.getElementById('rainCanvas');
const ctx = canvas.getContext('2d');
let width = canvas.width = window.innerWidth;
let height = canvas.height = window.innerHeight;

class Drop { constructor(){ this.reset(); } reset(){ this.x=Math.random()*width; this.y=Math.random()*-height; this.length=Math.random()*15+10; this.speed=Math.random()*4+2; this.opacity=Math.random()*0.3+0.1;} draw(){ ctx.strokeStyle='rgba(255,255,255,'+this.opacity+')'; ctx.lineWidth=1; ctx.beginPath(); ctx.moveTo(this.x,this.y); ctx.lineTo(this.x,this.y+this.length); ctx.stroke(); this.y+=this.speed; if(this.y>height) this.reset(); } }
class Particle { constructor(){ this.reset(); } reset(){ this.x=Math.random()*width; this.y=Math.random()*height; this.size=Math.random()*2+1; this.speed=Math.random()*0.3; this.opacity=Math.random()*0.2+0.05;} draw(){ ctx.fillStyle='rgba(255,255,255,'+this.opacity+')'; ctx.beginPath(); ctx.arc(this.x,this.y,this.size,0,Math.PI*2); ctx.fill(); this.y+=this.speed; if(this.y>height) this.reset(); } }

const drops=[]; const particles=[];
for(let i=0;i<120;i++) drops.push(new Drop());
for(let i=0;i<60;i++) particles.push(new Particle());

function animate(){ ctx.clearRect(0,0,width,height); drops.forEach(d=>d.draw()); particles.forEach(p=>p.draw()); requestAnimationFrame(animate); }
animate();

window.addEventListener('resize', ()=>{ width=canvas.width=window.innerWidth; height=canvas.height=window.innerHeight; });
</script>
</body>
</html>
