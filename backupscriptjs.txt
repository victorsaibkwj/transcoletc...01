const noticias = {
  "Transcol": [
    { title: ". Entrega de novos ônibus com ar-condicionado e motor sustentável" },
    { title: "Futuro sustentável: elétricos e biometano" },
    { title: " Linhas alimentadoras ampliadas em Vitória" },
    { title: "Transcol adiciona nova linha expressa entre Vitória e Cariacica", url: "#", date: "2025-07-07" },
    { title: "Aplicativo do Transcol agora mostra ônibus em tempo real", url: "#", date: "2025-07-06" },
    { title: "Passageiros reclamam de instabilidade no app ÔnibusGV", url: "https://es360.com.br/dia-a-dia/noticia/passageiros-do-transcol-reclamam-de-instabilidade-no-app-onibusgv/", date: "2025-07-07" },
    { title: "App vai mostrar em tempo real lotação do Transcol via InBus", url: "https://es360.com.br/dia-a-dia/noticia/app-vai-mostrar-em-tempo-real-lotacao-do-transcol/", date: "2025-06-24" },
    { title: "Mais 100 ônibus do Transcol passam a contar com Wi‑Fi", url: "https://www.es.gov.br/Noticia/duzentos-veiculos-do-transcol-passam-a-contar-com-o-servico-de-wi-fi", date: "2025-06-24" }
  ],
  "Vitória": [
    { title: "Festival Gastronômico movimenta a Praia do Canto", url: "#", date: "2025-07-07" },
    { title: "Prefeitura lança programa de mobilidade urbana", url: "#", date: "2025-07-06" }
  ],
  "Vila Velha": [
    { title: "Reforma do Convento da Penha entra na reta final", url: "#", date: "2025-07-07" },
    { title: "Novos pontos de Wi-Fi gratuito são instalados", url: "#", date: "2025-07-05" }
  ],
  "Serra": [
    { title: "Feira de Empreendedorismo atrai jovens no Parque da Cidade", url: "#", date: "2025-07-07" },
    { title: "Serra amplia vacinação contra gripe em bairros prioritários", url: "#", date: "2025-07-03" }
  ],
  "Guarapari": [
    { title: "Guarapari registra aumento no turismo durante as férias de julho", url: "#", date: "2025-07-07" },
    { title: "Projeto ambiental recolhe mais de 2 toneladas de lixo nas praias", url: "#", date: "2025-07-05" }
  ]
};

function renderNoticias() {
  const container = document.getElementById('news-container');
  for (const cidade in noticias) {
    const secao = document.createElement('section');
    secao.className = 'city-news';
    const h2 = document.createElement('h2');
    h2.textContent = `Notícias de ${cidade}`;
    secao.appendChild(h2);
    const ul = document.createElement('ul');
    ul.className = 'news-list';
    noticias[cidade].forEach(noticia => {
      const li = document.createElement('li');
      const a = document.createElement('a');
      a.href = noticia.url || "#";
      a.textContent = noticia.title;
      const time = document.createElement('time');
      time.dateTime = noticia.date || "";
      time.textContent = noticia.date ? ` (${noticia.date})` : "";
      li.appendChild(a);
      li.appendChild(time);
      ul.appendChild(li);
    });
    secao.appendChild(ul);
    container.appendChild(secao);
  }
}

function gerarIdentificadorUnico(tamanho = 128) {
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%&*-_+=?';
  let resultado = '';
  for (let i = 0; i < tamanho; i++) {
    resultado += chars.charAt(Math.floor(Math.random() * chars.length));
  }
  return resultado;
}

function iniciarSlider() {
  const slides = document.querySelectorAll('#slider img');
  let index = 0;
  setInterval(() => {
    slides[index].classList.remove('active');
    index = (index + 1) % slides.length;
    slides[index].classList.add('active');
  }, 4000);
}

document.addEventListener('DOMContentLoaded', () => {
  renderNoticias();
  document.getElementById('data-atualizacao').textContent = new Date().toLocaleString('pt-BR');
  document.getElementById('unique-id').textContent = `Identificador único: ${gerarIdentificadorUnico()}`;
  iniciarSlider();
});
