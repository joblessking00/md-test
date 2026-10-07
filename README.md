<!doctype html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>MD Editor 로고 애니메이션</title>
<style>
  :root{--bg:#2d2c2a;--fg:#fdfdfd;--page:#1c1b1a;--line:#45433f;--muted:#a8a49c}
  *{box-sizing:border-box}
  html{height:100%}
  body{min-height:100%;margin:0;background:var(--page);color:var(--fg);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;padding:16px;font:14px/1.4 system-ui,-apple-system,"Segoe UI","Malgun Gothic",sans-serif}
  .stage{width:min(100%,544px,calc(100vh - 110px));min-width:200px;aspect-ratio:1/1;background:var(--bg);border-radius:14px;overflow:hidden}
  .stage svg{display:block;width:100%;height:100%}
  .bar{display:flex;align-items:center;gap:10px;width:min(100%,544px)}
  .bar button{flex:none;border:1px solid var(--line);background:#33322f;color:var(--fg);border-radius:8px;padding:7px 12px;font:inherit;cursor:pointer}
  .bar button:hover{background:#3d3b38}
  .bar button:focus-visible,.bar input:focus-visible{outline:2px solid #8ab4f8;outline-offset:2px}
  .bar input[type=range]{flex:1;min-width:0;accent-color:#fdfdfd}
  .bar output{flex:none;width:4.2em;text-align:right;color:var(--muted);font-variant-numeric:tabular-nums}
</style>
</head>
<body>

<div class="stage">
  <!-- 영상(544×544)을 4배 한 좌표계. 모든 도형은 벡터이며 이미지·영상·웹폰트 파일을 쓰지 않습니다. -->
  <svg id="logo" viewBox="0 0 2176 2176" role="img" aria-label="MD Editor">
    <defs>
      <!-- 펜 윗부분을 글자 높이에 맞춰 잘라 두는 선 (펜이 올라올 때 열림) -->
      <clipPath id="penCut"><rect id="cutRect" x="-3000" y="0" width="9000" height="9000"/></clipPath>
      <!-- 마지막에 번지는 흰 빛 -->
      <filter id="glow" filterUnits="userSpaceOnUse" x="-360" y="-760" width="3760" height="1960" color-interpolation-filters="sRGB">
        <feGaussianBlur in="SourceGraphic" stdDeviation="26" result="near"/>
        <feGaussianBlur in="SourceGraphic" stdDeviation="84" result="far"/>
        <feComponentTransfer in="near" result="nearA"><feFuncA type="linear" slope="0.44"/></feComponentTransfer>
        <feComponentTransfer in="far" result="farA"><feFuncA type="linear" slope="0.32"/></feComponentTransfer>
        <feMerge><feMergeNode in="farA"/><feMergeNode in="nearA"/></feMerge>
      </filter>
    </defs>

    <g id="lock" transform="translate(415,689)">
      <use id="glowUse" href="#mark" filter="url(#glow)" opacity="0"/>
      <g id="mark" fill="#fdfdfd">
        <!-- M 의 왼쪽 (세로 기둥 + 왼쪽 사선) -->
        <path d="M0 0H170L371 402L297 546L140 244V831H0Z"/>
        <!-- D (왼쪽 위가 펜이 지나가는 길만큼 비스듬히 열려 있음) -->
        <path d="M861 0H965A385 415.5 0 0 1 965 831H668V366L809 95V707H970A229 291 0 0 0 970 125H861Z"/>
        <!-- 펜촉이 지나간 자리에 남는 가는 선 -->
        <line id="ink" x1="305" y1="795" x2="305" y2="795" stroke="#fdfdfd" stroke-width="10" stroke-linecap="round" opacity="0"/>
        <!-- 펜: 펜촉 끝이 원점, 위쪽이 펜대 방향인 자체 좌표로 그리고 28도 기울여 놓음 -->
        <g clip-path="url(#penCut)">
          <g id="pen" transform="matrix(.88295 .46947 .46947 -.88295 305 795)">
            <path id="penBody" d=""/>
            <path d="M-56 223H56L74 167L4 0V114.5A17 17 0 1 1 -4 114.5V0L-74 167Z"/>
          </g>
        </g>
        <!-- "Editor" 글자 (Poppins SemiBold 의 외곽선을 도형으로 넣음, SIL OFL 1.1) -->
        <g id="word" transform="translate(1419.6,637)" opacity="0"><path d="M122.2 -342.2V-239.8H259.7V-174.9H122.2V-66.7H277.2V0H40.4V-408.8H277.2V-342.2Z"/><path d="M463.8 -329.3Q495.4 -329.3 524.1 -315.5Q552.7 -301.8 569.7 -279V-432.8H652.7V0H569.7V-48Q554.5 -24 527 -9.4Q499.5 5.3 463.2 5.3Q422.3 5.3 388.4 -15.8Q354.4 -36.8 334.8 -75.2Q315.2 -113.5 315.2 -163.2Q315.2 -212.3 334.8 -250.3Q354.4 -288.3 388.4 -308.8Q422.3 -329.3 463.8 -329.3ZM484.3 -257.3Q461.5 -257.3 442.2 -246.2Q422.9 -235.1 410.9 -213.8Q398.9 -192.4 398.9 -163.2Q398.9 -133.9 410.9 -112Q422.9 -90.1 442.5 -78.4Q462.1 -66.7 484.3 -66.7Q507.1 -66.7 527 -78.1Q546.9 -89.5 558.6 -110.8Q570.3 -132.2 570.3 -162Q570.3 -191.8 558.6 -213.2Q546.9 -234.5 527 -245.9Q507.1 -257.3 484.3 -257.3Z"/><path d="M708.9 -410.6Q708.9 -431.1 723.2 -444.8Q737.5 -458.5 759.2 -458.5Q780.8 -458.5 795.1 -444.8Q809.5 -431.1 809.5 -410.6Q809.5 -390.1 795.1 -376.4Q780.8 -362.6 759.2 -362.6Q737.5 -362.6 723.2 -376.4Q708.9 -390.1 708.9 -410.6ZM799.5 -324V0H717.6V-324Z"/><path d="M960.4 -256.8V-100Q960.4 -83.6 968.3 -76.3Q976.2 -69 994.9 -69H1032.9V0H981.4Q877.9 0 877.9 -100.6V-256.8H839.3V-324H877.9V-404.2H960.4V-324H1032.9V-256.8Z"/><path d="M1056.3 -162Q1056.3 -211.7 1078.2 -249.7Q1100.2 -287.8 1138.2 -308.5Q1176.2 -329.3 1223 -329.3Q1269.8 -329.3 1307.8 -308.5Q1345.8 -287.8 1367.7 -249.7Q1389.7 -211.7 1389.7 -162Q1389.7 -112.3 1367.2 -74.3Q1344.6 -36.3 1306.3 -15.5Q1268 5.3 1220.6 5.3Q1173.9 5.3 1136.4 -15.5Q1099 -36.3 1077.6 -74.3Q1056.3 -112.3 1056.3 -162ZM1305.4 -162Q1305.4 -208.2 1281.2 -233.1Q1256.9 -257.9 1221.8 -257.9Q1186.7 -257.9 1163 -233.1Q1139.3 -208.2 1139.3 -162Q1139.3 -115.8 1162.4 -90.9Q1185.5 -66.1 1220.6 -66.1Q1242.9 -66.1 1262.5 -76.9Q1282.1 -87.7 1293.8 -109.4Q1305.4 -131 1305.4 -162Z"/><path d="M1616 -328.7V-242.7H1594.4Q1555.8 -242.7 1536.2 -224.6Q1516.6 -206.5 1516.6 -161.4V0H1434.7V-324H1516.6V-273.7Q1532.4 -299.5 1557.8 -314.1Q1583.3 -328.7 1616 -328.7Z"/></g>
      </g>
    </g>
  </svg>
</div>

<div class="bar">
  <button type="button" id="replay">다시 재생</button>
  <input type="range" id="seek" min="0" max="6.7" step="0.01" value="0" aria-label="재생 위치">
  <output id="clock">0.00초</output>
</div>

<script>
(function(){
  'use strict';
  const DUR = 6.7;                       // 전체 길이(초). 원본 영상은 6.04초이며 끝의 빛이 사그라드는 부분만 조금 더 이어 붙임
  const AX = 0.46947, AY = -0.88295;     // 펜대 방향 (세로에서 28도)
  const TIP = [305, 795];                // 펜촉 끝이 쉬는 자리
  const TRAVEL = 390;                    // 펜이 올라가는 거리
  const LOCK_W = 3035.7, MARK_W = 1350, MARK_H = 831;
  const END_SCALE = 0.578;               // 마지막에 줄어드는 비율
  const CX = 1090, CY0 = 1104.5, CY1 = 1078;

  const $ = id => document.getElementById(id);
  const lock = $('lock'), pen = $('pen'), body = $('penBody'), ink = $('ink'), cut = $('cutRect'), word = $('word'), glow = $('glowUse');
  const seek = $('seek'), clock = $('clock');

  const clamp = v => v < 0 ? 0 : v > 1 ? 1 : v;
  const seg = (t, a, b) => clamp((t - a) / (b - a));
  const inOut = x => x < .5 ? 4 * x * x * x : 1 - Math.pow(-2 * x + 2, 3) / 2;
  const soft = x => Math.pow(Math.sin(x * Math.PI / 2), 1.3);
  const lerp = (a, b, k) => a + (b - a) * k;
  const n = v => Math.round(v * 100) / 100;

  // 펜대 모양. L = 펜촉 끝에서 펜대 윗모서리까지의 길이
  function bodyPath(L){
    const w = 69, b = 246, r = 8;
    return 'M' + (-w) + ' ' + (b + r) + 'V' + n(L) +
           'C' + (-w + 3) + ' ' + n(L + 26) + ' ' + (w - 3) + ' ' + n(L + 26) + ' ' + w + ' ' + n(L) +
           'V' + (b + r) + 'Q' + w + ' ' + b + ' ' + (w - r) + ' ' + b + 'H' + (-w + r) + 'Q' + (-w) + ' ' + b + ' ' + (-w) + ' ' + (b + r) + 'Z';
  }

  function render(t){
    // 1) 펜: 윗부분이 드러남(0~0.25초) → 올라감(~1초) → 잠깐 멈춤 → 내려옴(1.25~2초) → 윗부분이 다시 가려짐(~2.4초)
    const reveal = t < 1 ? inOut(seg(t, 0, .25)) : 1 - inOut(seg(t, 2.0, 2.4));
    const up     = t < 1.25 ? inOut(seg(t, .22, 1.0)) : 1 - inOut(seg(t, 1.25, 2.02));
    const s = TRAVEL * up;
    const tx = TIP[0] + AX * s, ty = TIP[1] + AY * s;
    pen.setAttribute('transform', 'matrix(.88295 .46947 .46947 -.88295 ' + n(tx) + ' ' + n(ty) + ')');
    body.setAttribute('d', bodyPath(938 - 45 * up));
    cut.setAttribute('y', reveal >= 1 ? -5000 : n(-115 * reveal));
    if(s > 6){
      ink.setAttribute('x2', n(tx - AX * 4)); ink.setAttribute('y2', n(ty - AY * 4));
      ink.setAttribute('opacity', 1);
    }else ink.setAttribute('opacity', 0);

    // 2) 로고가 줄어들며 왼쪽으로 가고 "Editor" 가 오른쪽에서 들어옴 (3.4초~)
    const zoom = soft(seg(t, 3.4, 5.7));
    const pan  = soft(seg(t, 3.4, 5.0));
    const sc = lerp(1, END_SCALE, zoom);
    const focus = lerp(MARK_W / 2, LOCK_W / 2, pan);
    const x = CX - focus * sc, y = lerp(CY0, CY1, zoom) - MARK_H / 2 * sc;
    lock.setAttribute('transform', 'translate(' + n(x) + ' ' + n(y) + ') scale(' + Math.round(sc * 1e4) / 1e4 + ')');
    word.setAttribute('opacity', n(seg(t, 3.72, 4.14)));

    // 3) 빛: 4초부터 밝아졌다가 5.2초 뒤로 사그라듦
    const g = t < 5.2 ? Math.sin(seg(t, 4.0, 5.15) * Math.PI / 2) : 1 - inOut(seg(t, 5.2, 6.7));
    if(g > .004){ glow.setAttribute('opacity', n(g)); glow.style.display = ''; }
    else glow.style.display = 'none';

    seek.value = t; clock.textContent = t.toFixed(2) + '초';
  }

  let raf = 0, t0 = 0;
  function stop(){ if(raf){ cancelAnimationFrame(raf); raf = 0; } }
  function tick(now){
    const t = Math.min(DUR, (now - t0) / 1000);
    render(t);
    raf = t < DUR ? requestAnimationFrame(tick) : 0;
  }
  function play(from){
    stop();
    t0 = performance.now() - (from || 0) * 1000;
    raf = requestAnimationFrame(tick);
  }

  $('replay').addEventListener('click', () => play(0));
  seek.addEventListener('input', () => { stop(); render(+seek.value); });

  window.mdLogo = { render, play, stop, duration: DUR };   // 다른 페이지에 넣을 때 쓰는 손잡이

  const q = new URLSearchParams(location.search).get('t');
  const still = window.matchMedia && matchMedia('(prefers-reduced-motion: reduce)').matches;
  if(q !== null && isFinite(+q)) render(Math.max(0, Math.min(DUR, +q)));   // ?t=1.2 → 그 시점에서 멈춘 화면
  else if(still) render(DUR);                                               // 움직임 줄이기 설정이면 완성된 모습만
  else { render(0); play(0); }
})();
</script>
</body>
</html>
