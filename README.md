# infochl.github.io
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Entraînement Python</title>
<style>
:root{--bg:#f6f7fb;--card:#fff;--tx:#1b1f2a;--mut:#667085;--bd:#d9dde7;--ac:#3b5bdb;--code:#0f172a;--codetx:#e6edf7;--ok:#e3f6e8;--okb:#2f9e55;--ko:#fde8e8;--kob:#d64545;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#10131a;--card:#1a1f2b;--tx:#eef1f7;--mut:#9aa4b8;--bd:#2d3546;--ac:#7c93ff;--code:#0a0d13;--codetx:#e6edf7;--ok:#16301f;--okb:#4cc27a;--ko:#3a1c1c;--kob:#ff7a7a}}
:root[data-theme="dark"]{--bg:#10131a;--card:#1a1f2b;--tx:#eef1f7;--mut:#9aa4b8;--bd:#2d3546;--ac:#7c93ff;--code:#0a0d13;--codetx:#e6edf7;--ok:#16301f;--okb:#4cc27a;--ko:#3a1c1c;--kob:#ff7a7a}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:17px/1.45 system-ui,-apple-system,"Segoe UI",Roboto,sans-serif}
main{max-width:640px;margin:0 auto;padding:14px 14px 28px}
header{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
h1{font-size:1.05rem;margin:0}
.score{color:var(--mut);font-size:.95rem;font-variant-numeric:tabular-nums}
.zone{background:var(--card);border:1px solid var(--bd);border-radius:14px;padding:14px;margin-bottom:14px}
.lbl{font-size:.8rem;text-transform:uppercase;letter-spacing:.06em;color:var(--mut);margin:0 0 8px}
pre{margin:0;background:var(--code);color:var(--codetx);border-radius:10px;padding:16px;font:1.05rem/1.5 ui-monospace,SFMono-Regular,Menlo,Consolas,monospace;white-space:pre-wrap;word-break:break-word;overflow-x:auto}
.opts{display:flex;flex-direction:column;gap:10px}
.opt{display:block;width:100%;min-height:48px;text-align:left;font:inherit;color:inherit;background:var(--bg);border:2px solid var(--bd);border-radius:12px;padding:12px 14px;white-space:pre-wrap;cursor:pointer;-webkit-tap-highlight-color:transparent}
.opt:active{border-color:var(--ac)}
.opt:disabled{cursor:default}
.opt.ok{background:var(--ok);border-color:var(--okb)}
.opt.ko{background:var(--ko);border-color:var(--kob)}
.opt:disabled:not(.ok):not(.ko){opacity:.55}
#fb{min-height:1.6em;margin:14px 2px 0;font-weight:600}
#next{display:none;width:100%;min-height:52px;margin-top:10px;font:inherit;font-weight:600;color:#fff;background:var(--ac);border:0;border-radius:12px;cursor:pointer}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]) #next{color:#10131a}}
:root[data-theme="dark"] #next{color:#10131a}
.info{color:var(--mut);font-size:.85rem;text-align:center;margin:0}
#errmsg{color:var(--kob)}
[hidden]{display:none!important}
header{gap:10px}
h1{flex:1}
.back{font:inherit;font-size:.95rem;color:var(--ac);background:transparent;border:2px solid var(--bd);border-radius:10px;min-height:40px;padding:0 12px;cursor:pointer}
.menu{display:flex;flex-direction:column;gap:14px;margin:6px 0 14px}
.menubtn{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;width:100%;min-height:88px;font:inherit;font-size:1.2rem;font-weight:700;color:var(--tx);background:var(--card);border:2px solid var(--bd);border-radius:16px;cursor:pointer;-webkit-tap-highlight-color:transparent}
.menubtn small{font-size:.85rem;font-weight:400;color:var(--mut)}
.menubtn:active{border-color:var(--ac)}
.menubtn:disabled{opacity:.5;cursor:default}
.opt b,.line b,.cl b{font-weight:700}
.btn{display:block;width:100%;min-height:52px;margin-top:10px;font:inherit;font-weight:600;color:#fff;background:var(--ac);border:0;border-radius:12px;cursor:pointer}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]) .btn{color:#10131a}}
:root[data-theme="dark"] .btn{color:#10131a}
.lines{display:flex;flex-direction:column;gap:10px}
.line{display:flex;align-items:stretch;gap:6px;background:var(--bg);border:2px solid var(--bd);border-radius:12px;padding:6px}
.line .h{display:flex;align-items:center;justify-content:center;min-width:40px;color:var(--mut);font-size:1.4rem;cursor:grab;touch-action:none}
.line .t,.cl .t{flex:1;align-self:center;white-space:pre-wrap;padding:6px 2px}
.line .mv{display:flex;gap:4px;align-items:center}
.line .mv button{width:44px;height:44px;font:inherit;color:var(--ac);background:var(--card);border:2px solid var(--bd);border-radius:10px;cursor:pointer}
.line .mv button:disabled{opacity:.35;cursor:default}
.lines{user-select:none;-webkit-user-select:none}
.line{cursor:grab}
.lines.dragging .line:not(.drag){transition:transform .15s}
.line.drag{position:relative;z-index:5;cursor:grabbing;border-color:var(--ac);box-shadow:0 6px 18px rgba(0,0,0,.28);transition:none}
.line.ok{background:var(--ok);border-color:var(--okb)}
.line.ko{background:var(--ko);border-color:var(--kob)}
.lines.locked .h,.lines.locked .mv{display:none}
#o-fb{min-height:1.6em;margin:14px 2px 0;font-weight:600}
.corr{display:flex;flex-direction:column;gap:8px;margin-top:6px}
.cl{display:flex;gap:10px;align-items:flex-start;border:2px dashed var(--okb);border-radius:12px;padding:8px 10px}
.cl .n{min-width:1.6em;height:1.6em;border-radius:50%;background:var(--okb);color:#fff;font-size:.85rem;font-weight:700;display:flex;align-items:center;justify-content:center;margin-top:4px}
.consigne{font-size:1.05rem;font-weight:600;margin:0 0 10px}
.k{color:#ff79c6}.s{color:#a5e075}.n{color:#f9b572}.c{color:#7f8ea3;font-style:italic}.f{color:#7dcfff}.p{color:#9aa4b8;font-style:italic}.o{color:#c9d6ea}
.counts{display:flex;gap:6px;align-items:center}
.cnt{position:relative;min-width:34px;min-height:34px;padding:0 6px;font:inherit;font-size:1rem;font-weight:700;font-variant-numeric:tabular-nums;background:transparent;border:0;border-radius:8px;cursor:default}
.c-tot{color:var(--tx)}.c-ok{color:var(--okb)}.c-ko{color:var(--kob)}
@media (hover:hover){
 .cnt:hover::after{content:attr(data-tip);position:absolute;top:100%;right:0;z-index:20;margin-top:4px;padding:6px 10px;border-radius:8px;background:var(--code);color:var(--codetx);font-size:.8rem;font-weight:500;white-space:nowrap;box-shadow:0 4px 14px rgba(0,0,0,.3)}
}
@media (hover:none){.cnt{cursor:pointer}}
.cnt{-webkit-tap-highlight-color:transparent}
.cnt:focus{outline:none}
.cnt:focus-visible{outline:2px solid var(--ac)}
dialog{width:min(88vw,360px);border:1px solid var(--bd);border-radius:16px;padding:18px;background:var(--card);color:var(--tx);font:inherit}
dialog::backdrop{background:rgba(0,0,0,.5)}
dialog p{margin:0 0 6px}
</style>
</head>
<body>
<main>
<header><button class="back" id="back" type="button" hidden>← Menu</button><h1 id="title">Python</h1>
<div class="counts" id="counts" hidden>
<button type="button" class="cnt c-tot" id="c-tot" data-tip="Nombre de questions traitées" aria-label="Nombre de questions traitées">0</button>
<button type="button" class="cnt c-ok" id="c-ok" data-tip="Nombre de bonnes réponses" aria-label="Nombre de bonnes réponses">0</button>
<button type="button" class="cnt c-ko" id="c-ko" data-tip="Nombre de mauvaises réponses" aria-label="Nombre de mauvaises réponses">0</button>
</div></header>

<section id="v-menu">
<nav class="menu" aria-label="Menu principal">
<button class="menubtn" type="button" data-go="vocabulaire"><span>Vocabulaire</span><small id="n-vocabulaire"></small></button>
<button class="menubtn" type="button" data-go="ordre"><span>Mettre dans l’ordre</span><small id="n-ordre"></small></button>
<button class="menubtn" type="button" data-go="exercice"><span>Exercice</span><small id="n-exercice"></small></button>
</nav>
</section>

<div id="v-quiz" hidden>
<section class="zone" id="z1" aria-label="Code Python"><p class="lbl" id="lbl1">Code Python</p><p class="consigne" id="consigne" hidden></p><pre id="code"></pre></section>
<section class="zone" id="z2" aria-label="Propositions"><p class="lbl" id="lbl2">Quelle est la bonne traduction ?</p><div class="opts" id="opts"></div>
<div id="fb" aria-live="polite"></div><button id="next" type="button">Question suivante</button></section>
</div>

<div id="v-ordre" hidden>
<section class="zone" aria-label="Code Python"><p class="lbl">Code Python</p><pre id="o-code"></pre></section>
<section class="zone" aria-label="Lignes à remettre dans l’ordre"><p class="lbl">Remettez les lignes dans l’ordre (faites glisser ⠿ ou utilisez ▲ ▼)</p>
<div class="lines" id="lines"></div>
<div id="o-fb" aria-live="polite"></div>
<button class="btn" id="o-valider" type="button">Valider</button>
<div id="o-corr" hidden><p class="lbl" style="margin-top:14px">Correction</p><div class="corr" id="o-corr-list"></div></div>
<button class="btn" id="o-next" type="button" hidden>Question suivante</button></section>
</div>

<section class="zone" id="err" hidden role="alert"><p class="lbl">Problème dans les données</p><div id="errmsg"></div></section>
<p class="info" id="info"></p>
</main>
<dialog id="dlg"><p id="dlgtxt"></p><button class="btn" id="dlgok" type="button">OK</button></dialog>
<!-- Données : modifier ou compléter le bloc XML ci-dessous (voir le mode d’emploi qu’il contient) -->
<script type="application/xml" id="vocabulaire">
<!--
  MODE D’EMPLOI
  - Une <question> = un code Python (<code>), sa bonne traduction (<bonne>) et autant de <fausse> que l’on veut (3 au minimum).
    À chaque question, 3 fausses réponses sont tirées au hasard parmi celles écrites ici.
  - Pour ajouter une question : copier un bloc <question> … </question> n’importe où et changer son contenu.
  - Les <categorie> servent seulement à ranger les questions (elles correspondent aux anciennes lignes vides du CSV).
  - Dans un texte, écrire &lt; pour le signe <  et  &gt; pour le signe >  et  &amp; pour le signe &
    (ou bien encadrer le texte par <![CDATA[ … ]]> pour pouvoir écrire ces signes tels quels).
  - Les retours à la ligne et les espaces à l’intérieur d’un texte sont conservés.
-->
<vocabulaire>
  <categorie>
    <question>
      <code>Un utilisateur</code>
      <bonne>Celui qui exécute le programme</bonne>
      <fausse>Celui qui écrit le programme</fausse>
      <fausse>Celui qui modifie le programme</fausse>
      <fausse>Celui qui code le programme</fausse>
      <fausse>Celui que le programme utilise</fausse>
      <fausse>Celui qui écrit le programmeur</fausse>
      <fausse>Celui qui connait le programme</fausse>
    </question>
    <question>
      <code>Un programmeur</code>
      <bonne>Celui qui écrit le programme</bonne>
      <fausse>Celui qui exécute le programme</fausse>
      <fausse>Celui qui entre des données pendant l'exécution du programme</fausse>
      <fausse>Celui qui est exécuté par le programme</fausse>
      <fausse>Celui qui prolonge le programme</fausse>
      <fausse>Celui qui utilise le programme</fausse>
      <fausse>Celui qui exécute le programmeur</fausse>
    </question>
    <question>
      <code>if … :</code>
      <bonne><i>Est-ce-que</i> …. ?</bonne>
      <fausse><i>Tant que</i> …. ?</fausse>
      <fausse><i>Sinon, est-ce que</i> …. ?</fausse>
      <fausse><i>Sinon</i>.</fausse>
      <fausse>Affiche</fausse>
      <fausse><i>Sinon</i>, <i>tant que</i> …. ?</fausse>
      <fausse><i>Est-ce que</i> …. est faux ?</fausse>
    </question>
    <question>
      <code>while … ?</code>
      <bonne><i>Tant que</i> …. ?</bonne>
      <fausse><i>Est-ce-que</i> …. ?</fausse>
      <fausse><i>Sinon, est-ce que</i> …. ?</fausse>
      <fausse>puis-je ... ?</fausse>
      <fausse>Jusqu'à ... ?</fausse>
      <fausse><i>Sinon</i>, <i>tant que</i> …. ?</fausse>
      <fausse><i>Tant que</i> …. est faux ?</fausse>
    </question>
    <question>
      <code>elif … ?</code>
      <bonne><i>Sinon, est-ce que</i> …. ?</bonne>
      <fausse><i>Est-ce-que</i> …. ?</fausse>
      <fausse><i>Tant que</i> …. ?</fausse>
      <fausse><i>Sinon</i>, pourquoi pas ... ?</fausse>
      <fausse><i>Sinon</i>, <i>tant que</i> …. ?</fausse>
      <fausse>Affiche</fausse>
      <fausse><i>Sinon, est-ce que</i> …. est faux ?</fausse>
    </question>
    <question>
      <code>else :</code>
      <bonne><i>Sinon</i>.</bonne>
      <fausse><i>Sinon, est-ce que</i> …. ?</fausse>
      <fausse><i>Est-ce-que</i> …. ?</fausse>
      <fausse><i>Tant que</i> …. ?</fausse>
      <fausse><i>Sinon</i>, <i>tant que</i> …. ?</fausse>
      <fausse><i>Sinon</i>. ?</fausse>
      <fausse>Et pourquoi ?</fausse>
    </question>
    <question>
      <code>print()</code>
      <bonne>Affiche</bonne>
      <fausse>Saisi</fausse>
      <fausse>Saisi un texte</fausse>
      <fausse>Saisi un nombre</fausse>
      <fausse>Peut-être</fausse>
      <fausse>N'existe pas</fausse>
      <fausse><i>Tant que</i></fausse>
    </question>
    <question>
      <code>age = 15</code>
      <bonne>Met le nombre <b>15</b> dans la variable <b>age</b></bonne>
      <fausse>Met la variable <b>age</b> dans le nombre <b>15</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>age</b> est <u>strictement égal</u> au nombre <b>15</b> ?</fausse>
      <fausse>Met le texte <b>15</b> dans la variable <b>age</b></fausse>
      <fausse>Met le nombre <b>15</b> dans le texte <b>age</b></fausse>
      <fausse>Test si <b>age</b> vaut <b>15</b></fausse>
      <fausse>Met le nombre <b>age</b> dans la variable <b>15</b></fausse>
    </question>
    <question>
      <code>prenom = "Emmanuel"</code>
      <bonne>Met la chaîne de caractères <b>Emmanuel</b>  dans la variable <b>prenom</b></bonne>
      <fausse>Met la variable <b>Emmanuel</b> dans la chaîne de caractères <b>prenom</b></fausse>
      <fausse>Affiche la chaîne de caractères <b>Emmanuel</b></fausse>
      <fausse>Met la chaîne de caractères <b>prenom</b> dans la variable <b>Emmanuel</b></fausse>
      <fausse>Met le nombre <b>Emmanuel</b> dans la variable <b>prenom</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au texte <b>Emmanuel</b> ?</fausse>
      <fausse>Remplace la chaine de caractère <b>prenom</b> par la chaine de caractère <b>Emmanuel</b></fausse>
    </question>
    <question>
      <code>i = 0</code>
      <bonne>Met le nombre <b>0</b> dans la variable <b>i</b></bonne>
      <fausse>Met le nombre <b>i</b> dans la variable <b>0</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>i</b> est <u>strictement égal</u> au nombre <b>0</b> ?</fausse>
      <fausse>Met le nombre <b>1</b> dans la variable <b>i</b></fausse>
      <fausse>Met le nombre <b>0</b> dans le nombre <b>i</b></fausse>
      <fausse>Met la chaîne de caractères <b>0</b> dans la variable <b>i</b></fausse>
      <fausse>Affiche le contenu de la variable <b>i</b> si'l vaut <b>0</b></fausse>
    </question>
    <question>
      <code>lettre = "a"</code>
      <bonne>Met la lettre <b>a</b> dans la variable <b>lettre</b></bonne>
      <fausse>Met la lettre <b>lettre</b> dans la variable <b>a</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>lettre</b> est <u>strictement égal</u> au caractère <b>a</b> ?</fausse>
      <fausse>Met la lettre <b>a</b> dans la variable <b>a</b></fausse>
      <fausse>Met le contenu de la variable <b>a</b> dans la variable <b>lettre</b></fausse>
      <fausse>Affiche le contenu de la variable <b>lettre</b> s'il vaut <b>a</b></fausse>
      <fausse>Met le nombre <b>a</b> dans la variable <b>lettre</b></fausse>
    </question>
    <question>
      <code>f = 20</code>
      <bonne>Met le nombre <b>20</b> dans la variable <b>f</b></bonne>
      <fausse>Met le nombre <b>f</b> dans la variable <b>20</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>f</b> est <u>strictement égal</u> au nombre <b>20</b> ?</fausse>
      <fausse>Met les nombres <b>2</b> et <b>0</b> dans la variable <b>f</b></fausse>
      <fausse>Met le contenu de la variable <b>20</b> dans la variable <b>f</b></fausse>
      <fausse>Met le texte <b>20</b> dans la variable <b>f</b></fausse>
      <fausse>Affiche le contenu de la variable <b>f</b> s'il vaut <b>20</b></fausse>
    </question>
    <question>
      <code>15</code>
      <bonne>La valeur numérique <b>15</b></bonne>
      <fausse>La chaîne de caractères <b>15</b></fausse>
      <fausse>La variable <b>15</b></fausse>
      <fausse>La variable <b>texte 15</b></fausse>
      <fausse>Créé la variable <b>15</b></fausse>
      <fausse>Le texte <b>15</b></fausse>
      <fausse>La variable numérique <b>15</b></fausse>
    </question>
    <question>
      <code>15</code>
      <bonne>Le nombre <b>15</b></bonne>
      <fausse>La chaîne de caractères <b>15</b></fausse>
      <fausse>La variable <b>15</b></fausse>
      <fausse>La variable <b>texte 15</b></fausse>
      <fausse>Créé la variable <b>15</b></fausse>
      <fausse>Le texte <b>15</b></fausse>
      <fausse>La variable numérique <b>15</b></fausse>
    </question>
    <question>
      <code>"15"</code>
      <bonne>La chaîne de caractères <b>15</b></bonne>
      <fausse>Le nombre <b>15</b></fausse>
      <fausse>La valeur numérique <b>15</b></fausse>
      <fausse>La variable <b>15</b></fausse>
      <fausse>Stocke le texte <b>15</b> dans le programme</fausse>
      <fausse>Dit que <b>1</b> et <b>5</b> existe</fausse>
      <fausse>Les nombres <b>1</b> et <b>5</b></fausse>
    </question>
    <question>
      <code>sebastien</code>
      <bonne>La variable <b>sebastien</b></bonne>
      <fausse>Le texte <b>sebastien</b></fausse>
      <fausse>Le nombre <b>sebastien</b></fausse>
      <fausse>La phrase sebastien</fausse>
      <fausse>Crée la chaine de caractères <b>sebastien</b></fausse>
      <fausse>Le nombre contenu dans sebastien</fausse>
      <fausse>La variable numérique <b>sebastien</b></fausse>
    </question>
    <question>
      <code>"sebastien"</code>
      <bonne>Le texte <b>sebastien</b></bonne>
      <fausse>La variable <b>sebastien</b></fausse>
      <fausse>Le nombre <b>sebastien</b></fausse>
      <fausse>La valeur numérique <b>sebastien</b></fausse>
      <fausse>La question sebastien</fausse>
      <fausse>Le nombre contenu dans sebastien</fausse>
      <fausse>La variable numérique <b>sebastien</b></fausse>
    </question>
    <question>
      <code>"s"</code>
      <bonne>Le caractère <b>s</b></bonne>
      <fausse>La variable <b>s</b></fausse>
      <fausse>Le nombre <b>s</b></fausse>
      <fausse>La variable <b>texte</b> s</fausse>
      <fausse>Créé la variable <b>s</b></fausse>
      <fausse>Ne veut rien dire</fausse>
      <fausse>La variable numérique <b>s</b></fausse>
    </question>
    <question>
      <code>s</code>
      <bonne>La variable <b>s</b></bonne>
      <fausse>Le nombre <b>s</b></fausse>
      <fausse>La variable <b>texte</b> s</fausse>
      <fausse>Ne veut rien dire</fausse>
      <fausse>La variable numérique <b>s</b></fausse>
      <fausse>Le texte <b>s</b></fausse>
      <fausse>Le nombre <b>s</b></fausse>
    </question>
  </categorie>
  <categorie>
    <question>
      <code>if prenom == "Jean" :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au texte <b>Jean</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>Jean</b> est <u>strictement égal</u> au texte <b>prenom</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> du texte <b>Jean</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au nombre <b>Jean</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au texte <b>Jean</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au texte <b>Jean</b> ?</fausse>
      <fausse><i>Est-ce que</i> tu peu mettre le texte <b>Jean</b> dans la variable <b>prenom</b></fausse>
    </question>
    <question>
      <code>if prenom != "Jean" :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> du texte <b>Jean</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>Jean</b> est <u>strictement différent</u> du texte <b>prenom</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement égal</u> au texte <b>Jean</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> du contenu de la variable <b>Jean</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> au nombre <b>Jean</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> au texte <b>Jean</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>prenom</b> est <u>strictement différent</u> du texte <b>Jean</b> ?</fausse>
    </question>
    <question>
      <code>if a &gt; b :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au contenu de la variable <b>b</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>b</b> est <u>strictement supérieur</u> au contenu de la variable <b>a</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement inférieur</u> au contenu de la variable <b>b</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au texte <b>b</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au nombre <b>b</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au contenu de la variable <b>b</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au contenu de la variable <b>b</b> ?</fausse>
    </question>
    <question>
      <code>if a &lt; 15 :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement inférieur</u> au nombre <b>15</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement supérieur</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Est-ce que</i> le nombre <b>15</b> est <u>strictement inférieur</u> au contenu de la variable <b>a</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement inférieur</u> au texte <b>15</b> ?</fausse>
      <fausse><i>Est-ce que</i> le texte <b>a</b> est <u>strictement inférieur</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>a</b> est <u>strictement inférieur</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement inférieur</u> au nombre <b>15</b> ?</fausse>
    </question>
    <question>
      <code>if nombre &gt;= reference :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au contenu de la variable <b>reference</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>inferieur ou égal</u> au contenu de la variable <b>reference</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu du nombre <b>nombre</b> est <u>supérieur ou égal</u> au contenu de la variable <b>reference</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>reference</b> est <u>supérieur ou égal</u> au contenu de la variable <b>nombre</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au texte <b>reference</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au contenu de la variable <b>reference</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au contenu de la variable <b>reference</b> ?</fausse>
    </question>
    <question>
      <code>if pointure &lt;= 15 :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>pointure</b> est <u>inférieur ou égal</u> au nombre <b>15</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>pointure</b> est <u>supérieur ou égal</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>pointure</b> est <u>supérieur ou égal</u> au texte <b>15</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de texte <b>pointure</b> est <u>inférieur ou égal</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>pointure</b> est <u>inférieur ou égal</u> au contenu de la variable <b>15</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>pointure</b> est <u>inférieur ou égal</u> au nombre <b>15</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>pointure</b> est <u>inférieur ou égal</u> au nombre <b>15</b> ?</fausse>
    </question>
    <question>
      <code>if lettre == "a" :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>lettre</b> est <u>strictement égal</u> au caractère <b>a</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>lettre</b> est <u>strictement différent</u> du caractère <b>a</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>lettre</b> est <u>strictement égal</u> au nombre <b>a</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>a</b> est <u>strictement égal</u> au caractère <b>lettre</b> ?</fausse>
      <fausse><i>Est-ce que</i> le texte <b>lettre</b> est <u>strictement égal</u> au caractère <b>a</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>lettre</b> est <u>strictement égal</u> au caractère <b>a</b> ?</fausse>
      <fausse><i>Sinon</i> le contenu de la variable <b>lettre</b> est <u>strictement égal</u> au caractère <b>a</b> ?</fausse>
    </question>
    <question>
      <code>if jour == 6 :</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>jour</b> est <u>strictement égal</u> au nombre <b>6</b> ?</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>jour</b> est <u>strictement différent</u> du nombre <b>6</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>jour</b> est <u>strictement égal</u> au contenu de la variable <b>6</b> ?</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>jour</b> est <u>strictement égal</u> au nombre <b>6</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>jour</b> est <u>strictement égal</u> au caractère <b>6</b> ?</fausse>
      <fausse><i>Sinon, est-ce que</i> le contenu de la variable <b>jour</b> est <u>strictement égal</u> au nombre <b>6</b> ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>6</b> est <u>strictement égal</u> au nombre <b>jour</b> ?</fausse>
    </question>
    <question>
      <code>if truc == machin :
     Instruction 1
     Instruction 2
     Instruction 3</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors les instructions 1, 2 et 3 sont exécutées
<i>Si non</i>, alors je ne fais rien</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors les instructions 1 et 2 sont exécutées
<i>Si non</i>, alors l'instruction 1 est exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors seules les instructions 1 et 2 sont exécutées
<i>Si non</i>, alors je ne fais rien</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors les instructions 1, 2 et 3 sont exécutées
<i>Si non</i>, alors j’exécute l’instruction 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors je ne fais rien
<i>Si non</i>, alors les instructions 1, 2 et 3 sont exécutées</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
Si oui, alors l'instruction 1 est exécutée
<i>Si non</i>, alors les instructions 2 et 3 sont exécutées</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>truc</b> est <u>strictement égal</u> au contenu de la variable <b>machin</b> ?
les instructions 1, 2 et 3 sont exécutées
<i>Si non</i>, alors je ne fais rien</fausse>
    </question>
    <question>
      <code>if nombre &gt; 200:
     Instruction 1
     Instruction 2
Instruction 3</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement supérieur</u> au nombre <b>200</b> ?
Si oui, alors les instructions 1 et 2 puis 3 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement inférieur</u> au nombre <b>200</b> ?
Si oui, alors les instructions 1 et 2 puis 3 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <b>200</b> fois <u>supérieur</u> ?
Si oui, alors les instructions 1 et 2 puis 3 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement supérieur</u> de nombre <b>200</b> ?
Si oui, alors les instructions 1 et 2 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement supérieur</u> au nombre <b>200</b> ?
Si oui, alors les instructions 1 et 2 puis 3 sont exécutées.
<i>Si non</i>, alors je ne fais rien</fausse>
      <fausse><i>Est-ce que</i> le texte contenu dans la variable <b>nombre</b> est <u>strictement supérieur</u> au nombre <b>200</b> ?
Si oui, alors seules les instructions 1, 2 puis 3 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>nombre</b> est <u>strictement supérieur</u> au nombre <b>200</b> ?
Si oui, alors les instructions 1 et 2 puis 3 sont exécutées.
<i>Si non</i>, alors l’instruction 3 sera exécutée</fausse>
    </question>
    <question>
      <code>if nombre != 200:
     if a &gt; "a" :
          Instruction 1
     Instruction 2
     Instruction 3
Instruction 4</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement supérieur</u> au caractère <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
<i>Si non</i> à cette deuxième question, alors les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée quel que soit les réponses données</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement égal</u> au nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement supérieur</u> au caractère <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
<i>Si non</i> à cette deuxième question, alors les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée quel que soit les réponses données</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement inferieur</u> au caractère <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
<i>Si non</i> à cette deuxième question, alors les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée quel que soit les réponses données</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement supérieur</u> au caractère <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1 est exécutée,
<i>Si non</i> à cette deuxième question, alors les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée quel que soit les réponses données</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement supérieur</u> au caractère <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
<i>Si non</i> à cette deuxième question, alors Les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée si je réponds non à la première question</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
<i>Si non</i>, alors <i>est-ce que</i> le contenu de la variable <b>a</b> <u>strictement supérieur</u> au caractère <b>a</b> ?
<i>Si non</i> à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
Si oui à cette deuxième question, alors Les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée si je réponds oui à la première question</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>strictement différent</u> du nombre <b>200</b> ?
Si oui, alors <i>est-ce que</i> le caractère <b>a</b> <u>strictement supérieur</u> au contenu de la variable <b>a</b> ?
Si oui à cette deuxième question, alors l’instruction 1, 2 et 3 seront exécutées,
<i>Si non</i> à cette deuxième question, alors Les instructions 2 et 3 seront exécutées.
L’instruction 4 sera exécutée quel que soit les réponses données</fausse>
    </question>
  </categorie>
  <categorie>
    <question>
      <code>if … :
     Instruction 1
else :
     Instruction 2</code>
      <bonne>Structure exécutant une instruction si je réponds oui à la question et une autre instruction si je réponds non.</bonne>
      <fausse>Structure exécutant une instruction si je réponds non à la question et une autre instruction si je réponds oui.</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question et la même instruction si je réponds non.</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question et aucune si je réponds non.</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question puis une autre instruction quelle que soit ma réponse.</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question, puis pose une deuxième question et exécute une autre instruction si je réponds encie oui.</fausse>
      <fausse>Structure exécutant une instruction <i>tant que</i> je réponds oui à la question et une autre instruction si je réponds non.</fausse>
    </question>
    <question>
      <code>if trouver == "oui"  :
     Instruction 1
else :
     Instruction 2</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i> l’instruction 2 sera exécutée</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 2 sera exécutée
<i>Si non</i> l’instruction 1 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement différent</u> du texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i> l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b>?
Si oui l’instruction 1 sera exécutée
L’instruction 2 sera exécutée quoi qu'il arrive</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
L'instruction 1 sera exécutée
Ensuite l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i> je ne fais rien</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>oui</b> est <u>strictement égal</u> au texte <b>trouver</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i> l’instruction 2 sera exécutée</fausse>
    </question>
    <question>
      <code>if ville == "Lausanne" :
     if quartier == "Dock"  :
           Instruction 1
else :
     Instruction 2</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au texte <b>Dock</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, ne rien faire
<i>Si non</i> à la première question, faire instruction 2</bonne> 
      <fausse><i>Est-ce que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au texte <b>Dock</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, faire instruction 2
<i>Si non</i> à la première question, faire instruction 2</fausse>
      <fausse><i>Est-ce que</i> le texte <b>ville</b> est <u>strictement égal</u> au contenu de la variable <b>Lausanne</b>?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au texte <b>Dock</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, ne rien faire
<i>Si non</i> à la première question, faire instruction 2</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
Si oui, alors <i>est-ce que</i> le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au contenu de la variable <b>Dock</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, ne rien faire
<i>Si non</i> à la première question, faire instruction 2</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
<i>Si non</i>, alors <i>est-ce que</i> le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au texte <b>Dock</b>?
<i>Si non</i> à cette deuxième question, alors faire instruction 1
Si oui à cette deuxième question, ne rien faire
Si oui à la première question, faire instruction 2</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
Si oui, alors <i>est-ce que</i> tu peux mettre le texte <b>Dock</b> dans la variable <b>quartier</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, ne rien faire
<i>Si non</i> à la première question, faire instruction 2</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>ville</b> est <u>strictement égal</u> au texte <b>Lausanne</b>?
Si oui, alors <i>Tant que</i> que le contenu de la variable <b>quartier</b> est <u>strictement égal</u> au texte <b>Dock</b>?
Si oui à cette deuxième question, alors faire instruction 1
<i>Si non</i> à cette deuxième question, ne rien faire
<i>Si non</i> à la première question, faire instruction 2</fausse>
    </question>
    <question>
      <code>if nombre &gt;= 100 :
     Instruction 1
else :
     Instruction 2
     if poids &gt; 2000 :
           Instruction 3</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au nombre <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, alors faire instruction 2 puis poser la question : <i>Est-ce que</i> le contenu de la variable <b>poids</b> 
      est <u>strictement supérieur</u> au nombre <b>2000</b> ?
Si oui faire instruction 3</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au texte <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, alors faire instruction 2 puis poser la question : <i>Est-ce que</i> le contenu de la variable <b>poids</b> 
      est <u>strictement supérieur</u> au nombre <b>2000</b> ?
Si oui faire instruction 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au nombre <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, alors <i>est-ce que</i> le contenu de la variable <b>poids</b> est <u>strictement supérieur</u> au nombre <b>2000</b> ?
Si oui faire instruction 2 puis 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au nombre <b>100</b> ?
<i>Si non</i> alors faire instruction 1
Si oui, alors faire instruction 2 puis poser la question : <i>Est-ce que</i> le contenu de la variable <b>poids</b> 
      est <u>strictement supérieur</u> au nombre <b>2000</b> ?
<i>Si non</i> faire instruction 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au nombre <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, faire instructions 2 et 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>supérieur ou égal</u> au nombre <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, alors faire instruction 2 puis poser la question : <i>Est-ce que</i> le contenu du texte <b>poids</b> 
      est <u>strictement supérieur</u> au nombre <b>2000</b> ?
Si oui faire instruction 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>nombre</b> est <u>inférieur ou égal</u> au nombre <b>100</b> ?
Si oui alors faire instruction 1
<i>Si non</i>, alors faire instruction 2 puis poser la question : <i>Est-ce que</i> le contenu de la variable <b>poids</b> 
      est <u>inférieur</u> au nombre <b>2000</b> ?
Si oui faire instruction 3</fausse>
    </question>
  </categorie>
  <categorie>
    <question>
      <code>if ...  :
     …
elif … :
    ...
else :
     …</code>
      <bonne>Structure exécutant une instruction si je réponds oui à la question,
puis, si j’ai répondu non à la première question, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, si j’ai répondu non à la deuxième question, exécute encore une autre instruction</bonne>
      <fausse>Structure exécutant une instruction si je réponds non à la question,
puis, si j’ai répondu oui à la première question, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, si j’ai répondu non à la deuxième question, exécute encore une autre instruction</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question,
puis, si j’ai répondu oui à la première question, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, si j’ai répondu oui à la deuxième question, exécute encore une autre instruction</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question,
puis, quelle que soit la réponse à la première question, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, si j’ai répondu non à la deuxième question, exécute encore une autre instruction</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question,
puis, si j’ai répondu non à la première question, pose une deuxième question et exécute une 
      instruction si je réponds non à cette deuxième question
Puis, si j’ai répondu oui à la deuxième question, exécute encore une autre instruction</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question,
puis, si j’ai répondu non à la première question, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, si j’ai répondu non à la deuxième question, pose une troisième question</fausse>
      <fausse>Structure exécutant une instruction si je réponds oui à la question,
puis, quelle que soit ma réponse, pose une deuxième question et exécute une 
      instruction si je réponds oui à cette deuxième question
Puis, quelle que soit ma réponse, exécute encore une autre instruction</fausse>
    </question>
    <question>
      <code>if trouver == "oui"  :
     Instruction 1
elif trouver == "non" :
     Instruction 2</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui l’instruction 2 sera exécutée</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement différent</u> du texte <b>non</b>?
Si oui l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i> l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
<i>Si non</i> l’instruction 1 sera exécutée
Si oui, <i>est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
<i>Si non</i> l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> tu peux exécuter l’instruction 2 ?</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au contenu de la variable <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui l’instruction 2 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
Si oui, est-ce le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui l’instruction 2 sera exécutée</fausse>
    </question>
    <question>
      <code>if trouver == "oui"  :
     Instruction 1
elif trouver == "non" :
     Instruction 2
else :
    Instruction3</code>
      <bonne><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui, l’instruction 2 sera exécutée
<i>Si non</i>, l’instruction 3 sera exécutée</bonne>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui, l’instruction 2 et 3 seront exécutées</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au contenu de la variable <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui, l’instruction 2 sera exécutée
<i>Si non</i>, je ne fais rien</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
<i>Si non</i> l’instruction 1 sera exécutée
Si oui, <i>est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
<i>Si non</i>, l’instruction 2 sera exécutée
Si oui, l’instruction 3 sera exécutée</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i>, on s'arrête là</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non</i>, <i>tant que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Exécuter l’instruction 2
Puis exécuter l’instruction 3</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>oui</b> ?
Si oui l’instruction 1 sera exécutée
<i>Si non, est-ce que</i> le contenu de la variable <b>trouver</b> est <u>strictement égal</u> au texte <b>non</b>?
Si oui, l’instruction 2 sera exécutée
<i>Si non</i>, l’instruction 1 sera exécutée</fausse>
    </question>
    
  </categorie>
  <categorie>
    <question>
      <code>while comparaison :
    Instruction1
Instruction 2</code>
      <bonne>Structure exécutant l’instruction 1 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
...
<i>Est-ce que</i> comparaison est encore vraie ?
<i>Si non</i> je fais instruction 2</bonne>
      <fausse>Structure exécutant l’instruction 1 et 2 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
...
<i>Est-ce que</i> comparaison est encore vraie ?
<i>Si non</i> fin</fausse>
      <fausse>Structure exécutant l’instruction 2 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
...
<i>Est-ce que</i> comparaison est encore vraie ?
<i>Si non</i> je fais instruction 2</fausse>
      <fausse>Structure exécutant l’instruction 1 si la comparaison est vraie.

<i>Est-ce que</i> comparaison est vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est vraie ?
Si oui je fais instruction 1
...
<i>Est-ce que</i> comparaison est vraie ?
<i>Si non</i> je fais instruction 2</fausse>
      <fausse>Structure exécutant l’instruction 1 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
...
<i>Est-ce que</i> comparaison est encore vraie ?
<i>Si non</i> je fais encore instruction 1</fausse>
      <fausse>Structure exécutant les instructions 1 et 2 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1 et 2
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1 et 2
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1 et 2
...
<i>Est-ce que</i> comparaison est encore vraie ?
<i>Si non</i> je ne fais que l'instruction 2</fausse>
      <fausse>Structure exécutant l’instruction 1 <i>tant que</i> la comparaison est vraie.

<i>Est-ce que</i> comparaison est encore vraie ?
Si oui, je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
<i>Est-ce que</i> comparaison est encore vraie ?
Si oui je fais instruction 1
...
<i>Tant que</i> comparaison est encore vraie ?
je fais instruction 2</fausse>
    </question>
    <question>
      <code>while t != motDePasse :
    Instruction1
Instruction 2</code>
      <bonne><i>Tant que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 1.
L’instruction 2 sera exécutée quand le contenu de la variable <b>t</b> ne sera plus <u>différent</u> du contenu 
    de la variable <b>motDePasse</b>.</bonne>
      <fausse><i>Tant que</i> le contenu de la variable <b>t</b> est <u>égal</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 1.
L’instruction 2 sera exécutant quand le contenu de la variable <b>t</b> ne sera plus <u>différent</u> du contenu 
    de la variable <b>motDePasse</b>.</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 2.
L’instruction 1 sera exécutée quand le contenu de la variable <b>t</b> ne sera plus <u>différent</u> du contenu 
    de la variable <b>motDePasse</b>.</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 1.
L’instruction 1 ne sera jamais exécutée</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 1.
L’instruction 2 sera exécutée quand le contenu de la variable <b>t</b> sera encore <u>différent</u> du contenu 
    de la variable <b>motDePasse</b>.</fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
Si oui, exécuter instruction 1.
<i>Si non</i>, exécuter instruction 2.</fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>t</b> est <u>différent</u> du contenu de la variable <b>motDePasse</b>, 
je fais instruction 1 et 2.
L’instruction 2 sera exécutée quand le contenu de la variable <b>t</b> ne sera plus <u>différent</u> du contenu 
    de la variable <b>motDePasse</b>.</fausse>
    </question>
    <question>
      <code>while i &lt; 10 :
    Instruction 1
    Instruction 2
    if erreur == 5 :
        Instruction 4
    Instruction 5
Instruction 6</code>
      <bonne><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Puis je ferais instruction 5 quelle que soit la réponse.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></bonne>
      <fausse><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus grand que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Puis je ferais instruction 5 quelle que soit la réponse.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement différent</u> du nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Puis je ferais instruction 5 quelle que soit la réponse.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4 et 5.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Si la réponse est non, je fais instruction 5.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></fausse>
      <fausse><i>Est-ce que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je fais instruction 1 et instruction 2, et je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Puis je ferais instruction 5 quelle que soit la réponse.

L’instruction 6 sera exécutée si le contenu de la variable <b>i</b> n'est pas <u>strictement inférieur</u> au nombre <b>10</b></fausse>
      <fausse><i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement plus petit que</u> le nombre <b>10</b>, 
je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> au nombre <b>5</b>
Si la réponse est oui, je fais instruction 4.
Puis je ferais instruction 5 quelle que soit la réponse.

L’instruction 6 sera exécutée quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b></fausse>
    </question>
  </categorie>
  <categorie>
    <question>
      <code>print(schtroumpf)</code>
      <bonne>Afficher le contenu de la variable <b>schtroumpf</b></bonne>
      <fausse>Afficher chaîne de caractère <b>schtroumpf</b></fausse>
      <fausse>Saisir le contenu de la variable <b>schtroumpf</b></fausse>
      <fausse>Afficher le nombre <b>schtroumpf</b></fausse>
      <fausse>Retenir en mémoire la variable <b>schtroumpf</b></fausse>
      <fausse>Mettre la chaîne de caractère <b>schtroumpf</b> dans la mémoire</fausse>
      <fausse>Saisir la chaîne de caractère <b>schtroumpf</b></fausse>
    </question>
    <question>
      <code>print("schtroumpf")</code>
      <bonne>Afficher la chaîne de caractère <b>schtroumpf</b></bonne>
      <fausse>Afficher le contenu de la variable <b>schtroumpf</b></fausse>
      <fausse>Saisir le contenu de la variable <b>schtroumpf</b></fausse>
      <fausse>Afficher le nombre <b>schtroumpf</b></fausse>
      <fausse>Retenir en mémoire la variable <b>schtroumpf</b></fausse>
      <fausse>Mettre la chaîne de caractère <b>schtroumpf</b> dans la mémoire</fausse>
      <fausse>Saisir la chaîne de caractère <b>schtroumpf</b></fausse>
    </question>
    <question>
      <code>input()</code>
      <bonne>Saisir un texte</bonne>
      <fausse>Saisir un nombre</fausse>
      <fausse>Afficher un texte</fausse>
      <fausse>Afficher un nombre</fausse>
      <fausse>Saisir une variable</fausse>
      <fausse>Afficher la phrase entre guillemet</fausse>
      <fausse>Mettre un texte dans une variable</fausse>
    </question>
    <question>
      <code>int(input())</code>
      <bonne>Saisir un nombre</bonne>
      <fausse>Saisir un texte</fausse>
      <fausse>Afficher un nombre</fausse>
      <fausse>Afficher un texte</fausse>
      <fausse>Saisir une variable</fausse>
      <fausse>Afficher la phrase entre guillemet</fausse>
      <fausse>Mettre un nombre dans une variable</fausse>
    </question>
    <question>
      <code>input("Voici un texte")</code>
      <bonne>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir un texte</bonne>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir un nombre</fausse>
      <fausse>Saisir un texte, puis afficher la phrase entre guillemet <b>Voici un texte</b></fausse>
      <fausse>Afficher la variable <b>Voici un texte</b>, puis saisir un texte</fausse>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis afficher un texte</fausse>
      <fausse>Saisir un texte</fausse>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir une variable</fausse>
    </question>
    <question>
      <code>int(input("Voici un texte"))</code>
      <bonne>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir un nombre</bonne>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir un texte</fausse>
      <fausse>Saisir un nombre, puis afficher la phrase entre guillemet <b>Voici un texte</b></fausse>
      <fausse>Afficher la variable <b>Voici un texte</b>, puis saisir un nombre</fausse>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis afficher un nombre</fausse>
      <fausse>Saisir un nombre</fausse>
      <fausse>Afficher la phrase entre guillemet <b>Voici un texte</b>, puis saisir une variable</fausse>
    </question>
    <question>
      <code>prenom = input()</code>
      <bonne>Met le texte saisi par l’utilisateur dans la variable <b>prenom</b></bonne>
      <fausse>Met le nombre saisi par l’utilisateur dans la variable <b>prenom</b></fausse>
      <fausse>Met le texte saisi par le programmeur dans la variable <b>prenom</b></fausse>
      <fausse>Affiche le texte saisi par l’utilisateur dans la variable <b>prenom</b></fausse>
      <fausse>Met le texte saisi par l’utilisateur dans la variable <b>texte</b></fausse>
      <fausse>Met la variable <b>prenom</b> dans le texte saisi par l’utilisateur</fausse>
      <fausse>Test si texte saisi par l’utilisateur est déjà dans la variable <b>prenom</b></fausse>
    </question>
    <question>
      <code>age = int(input())</code>
      <bonne>Met le nombre saisi par l’utilisateur dans la variable <b>age</b></bonne>
      <fausse>Met le texte saisi par l’utilisateur dans la variable <b>age</b></fausse>
      <fausse>Met le nombre saisi par le programmeur dans la variable <b>age</b></fausse>
      <fausse>Affiche le nombre saisi par l’utilisateur dans la variable <b>age</b></fausse>
      <fausse>Met le texte saisi par le programmeur dans la variable <b>age</b></fausse>
      <fausse>Vérifie que la saisie soit <u>égal</u> au contenu de la varialbe <b>age</b></fausse>
      <fausse>Demande à l'utilisateur de vérifier que la saisie est <u>égal</u> au contenu de la varialbe <b>age</b></fausse>
      
    </question>
    <question>
      <code>age = int(input(15))</code>
      <bonne>Affiche <b>15</b> puis met le nombre saisi par l’utilisateur dans la variable <b>age</b></bonne>
      <fausse>Affiche <b>15</b> puis met le nombre <b>15</b> dans la variable <b>age</b> et demande à l'utilisateur de valider</fausse>
      <fausse>Affiche <b>15</b> puis met le nombre saisi par le programmeur dans la variable <b>age</b></fausse>
      <fausse>Affiche le nombre saisi par l’utilisateur dans la variable <b>age</b></fausse>
      <fausse>Affiche <b>15</b> puis met le texte saisi par l’utilisateur dans la variable <b>age</b></fausse>
      <fausse>Vérifie que le nombre <b>15</b> soit <u>égal</u> au contenu de la varialbe <b>age</b></fausse>
      <fausse>Demande à l'utilisateur de vérifier que le nombre <b>15</b> est <u>égal</u> au contenu de la varialbe <b>age</b></fausse>
    </question>
  </categorie>
</vocabulaire>

<!--
  MISE EN FORME (dans <bonne>, <fausse> et <ligne>) : <b>gras</b> (nombres, noms de variables, textes), <u>souligné</u>, <i>italique</i>.
-->
<!--
  PAGE « METTRE DANS L’ORDRE » : <replacer>
  - Une <question> = un <code> et ses <ligne>, écrites DANS LE BON ORDRE. La page les mélange pour l’élève.
  - On peut mettre autant de <ligne> et de <question> que l’on veut.
-->
<replacer>
  <question>
    <code>
      if age == 15 :
        Instruction 1
      else:
        Instruction 2
    </code>
    <ligne>
      <i>Est-ce que</i> le contenu de la variable <b>age</b> est <u>strictement égal</u> au nombre <b>15</b> ?
    </ligne>
    <ligne>
      Si oui, exécuter Instruction 1
    </ligne>
    <ligne>
      <i>si non</i>, exécuter Instruction 2
    </ligne>
  </question>
  <question>
    <code>
      while age == 15 :
        Instruction 1
      Instruction 2
    </code>
    <ligne>
      <i>Tant que</i> le contenu de la variable <b>age</b> est <u>strictement égal</u> au nombre <b>15</b> ?
    </ligne>
    <ligne>
      j'exécute l'Instruction 1
    </ligne>
    <ligne>
      Je ferais l'Instruction 2, quand le contenu de la variable <b>age</b> ne sera plus <u>strictement égal</u> au nombre <b>15</b>
    </ligne>
  </question>
  <question>
    <code>
      while i &lt; 10 :
        Instruction 1
        Instruction 2
        if erreur == 5 :
          Instruction 4
        Instruction 5
      Instruction 6
    </code>
    <ligne>
      <i>Tant que</i> le contenu de la variable <b>i</b> est <u>strictement inférieur</u> au nombre <b>10</b> ?
    </ligne>
    <ligne>
      j'exécute l'instruction 1
    </ligne>
    <ligne>
      j'exécute l'instruction 2
    </ligne>
    <ligne>
      je pose la question <i>est-ce que</i> le contenu de la variable <b>erreur</b> est <u>strictement égal</u> eu nombre <b>5</b> ?
    </ligne>
    <ligne>
      Si oui, j'exécute les instructions 4 et 5
    </ligne>
    <ligne>
      <i>Si non</i>, j'exécute l'instruction 5
    </ligne>
    <ligne>
      Je ferais l'instruction 6, quand le contenu de la variable <b>i</b> ne sera plus <u>strictement inférieur</u> au nombre <b>10</b>
    </ligne>
  </question>
</replacer>

<!--
  PAGE « EXERCICE » : <exercice>
  - Une <question> = une <consigne> (affichée au-dessus du code), un <code> (le programme, facultatif), une <bonne> réponse et au moins 3 <fausse>.
  - 3 fausses réponses sont tirées au hasard parmi celles écrites.
-->
<exercice>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      print(nombre)
    </code>
    <bonne>
      17
    </bonne>
    <fausse>
      nombre
    </fausse>
    <fausse>
      16
    </fausse>
    <fausse>
      rien
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      print(nombre)
      nombre = 18
      print(nombre)
    </code>
    <bonne>
      17
      18
    </bonne>
    <fausse>
      18
    </fausse>
    <fausse>
      nombre
    </fausse>
    <fausse>
      17
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      nombre = 18
      print(nombre)
    </code>
    <bonne>
      18
    </bonne>
    <fausse>
      17
      18
    </fausse>
    <fausse>
      nombre
    </fausse>
    <fausse>
      17
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      nombre = 18 - 1
      print(nombre)
    </code>
    <bonne>
      17
    </bonne>
    <fausse>
      18
    </fausse>
    <fausse>
      nombre
    </fausse>
    <fausse>
      16
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      nombre = nombre + 1
      print(nombre)
    </code>
    <bonne>
      18
    </bonne>
    <fausse>
      17
      18
    </fausse>
    <fausse>
      nombre
    </fausse>
    <fausse>
      17
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      nombre = nombre + nombre
      print(nombre)
    </code>
    <bonne>
      34
    </bonne>
    <fausse>
      17
    </fausse>
    <fausse>
      nombre + nombre
    </fausse>
    <fausse>
      289
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre = 17
      nombre = nombre * 2 - nombre
      print(nombre)
    </code>
    <bonne>
      17
    </bonne>
    <fausse>
      34
    </fausse>
    <fausse>
      nombre * 2 - nombre
    </fausse>
    <fausse>
      nombre
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      nombre1 = 15
      nombre2 = 17
      nombre3 = nombre1 + nombre2
      print(nombre1)
      print(nombre2)
      print(nombre3)
    </code>
    <bonne>
      15
      17
      32
    </bonne>
    <fausse>
      15
    </fausse>
    <fausse>
      17
    </fausse>
    <fausse>
      32
    </fausse>
    <fausse>
      nombre1
      nombre2
      nombre3
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      monAge = 15
      tonAge = 40
      ageCommun = monAge + tonAge/2
      ageCommun = ageCommun * 2
      print(ageCommun)
    </code>
    <bonne>
      70
    </bonne>
    <fausse>
      55
    </fausse>
    <fausse>
      ageCommun
    </fausse>
    <fausse>
      erreur
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      taillePied1 = 42
      taillePied2 = 43
      tailleAbsolu = taillePied2 – taillePied1
      tailleAbsolu = tailleAbsolu * -1
    </code>
    <bonne>
      rien
    </bonne>
    <fausse>
      0
    </fausse>
    <fausse>
      -2
    </fausse>
    <fausse>
      42
      43
    </fausse>
  </question>
  <question>
    <consigne>
      Pourquoi le programme suivant est-il faux ?
    </consigne>
    <code>
      ageCommun = monAge + tonAge/2
      ageCommun = ageCommun * 2
      print(ageCommun)
    </code>
    <bonne>
      À la ligne une, on demande de faire le calcul "monAge + tonAge/2". Mais aucune de ces variablent n'existent.
    </bonne>
    <fausse>
      le nom d'une variable ne peut pas avoir de majuscule
    </fausse>
    <fausse>
      Dans le calcul suivant : "age x 2 − age", il manque les parenthèses.
    </fausse>
    <fausse>
      Dnas le calcul suivant "monAge + tonAge/2", on ne peut pas savoir ce qu'il faire, car il manque les parenthèses.
    </fausse>
  </question>
  <question>
    <consigne>
      Pourquoi le programme suivant est-il faux ?
    </consigne>
    <code>
      age = 17
      age = age x 2 − age
      print(age)
    </code>
    <bonne>
      Pour multiplier, le caractère * doit être utilisé et non le caractère x
    </bonne>
    <fausse>
      "age = age x 2 − age" est à mettre dans l'autre sens : "age x 2 − age = age"
    </fausse>
    <fausse>
      Dans le calcul suivant : "age x 2 − age", il manque les parenthèses.
    </fausse>
    <fausse>
      Tout va bien, il n'y a pas de faute.
    </fausse>
  </question>
  <question>
    <consigne>
      Pourquoi le programme suivant est-il faux ?
    </consigne>
    <code>
      print(monAgeDouble)
      monAge = 16
      monAgeDouble = monAge / 2
    </code>
    <bonne>
      À la première ligne, je veux afficher le contenu de la variable monAgeDouble. La variable n'existe pas encore, elle sera créée 2 lignes plus tard.
    </bonne>
    <fausse>
      Le signe de la division n'ets pas le slach (barre oblique), mais cela la : ÷
    </fausse>
    <fausse>
      Le nom des variables n'a pas le droit de contenir des majuscules. 
    </fausse>
    <fausse>
      Tout va bien, il n'y a pas de faute.
    </fausse>
  </question>
  <question>
    <consigne>
      Dans quelle condition ce programme affichera un a ?
    </consigne>
    <code>
      monPoid = 70
      if monPoids > 70 :
        print("a")
      if monPoids &lt; 10 :
        print("a")
      elif monPoids &lt; 50 :
        print("b")
      elif monPoids &lt; 70 :
        print("c")
      else:
        print("d")
    </code>
    <bonne>
      Si la valeur contenue dans la variable monPoids
        est strictement supérieur à 70
        OU
        qu’elle est strictement inférieur à 10
    </bonne>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est strictement supérieur à 70
        ET
        qu’elle est strictement inférieur à 10
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est strictement supérieur à 70
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est strictement inférieur à 70
        OU
        qu’elle est strictement supérieur à 10
    </fausse>
  </question>
  <question>
    <consigne>
      Dans quelle condition ce programme affichera un b ?
    </consigne>
    <code>
      monPoid = 70
      if monPoids > 70 :
        print("a")
      if monPoids &lt; 10 :
        print("a")
      elif monPoids &lt; 50 :
        print("b")
      elif monPoids &lt; 70 :
        print("c")
      else:
        print("d")
    </code>
    <bonne>
      Si la valeur contenue dans la variable monPoids
        est supérieur ou égal à 10
        ET
        qu’elle est strictement inférieure à 50.
    </bonne>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est supérieur à 10
        ET
        qu’elle est strictement inférieure à 50.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est supérieur ou égal à 10
        OU
        qu’elle est strictement inférieure à 50.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est strictement inférieure à 50.
    </fausse>
  </question>
  <question>
    <consigne>
      Dans quelle condition ce programme affichera un c ?
    </consigne>
    <code>
      monPoid = 70
      if monPoids > 70 :
        print("a")
      if monPoids &lt; 10 :
        print("a")
      elif monPoids &lt; 50 :
        print("b")
      elif monPoids &lt; 70 :
        print("c")
      else:
        print("d")
    </code>
    <bonne>
      Si la valeur contenue dans la variable monPoids
        est supérieur ou égal à 10
        ET
        qu’elle est supérieur ou égal à 50
        ET
        qu’elle est strictement inférieure à 70.
    </bonne>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est supérieur à 10
        ET
        qu’elle est supérieur à 50
        ET
        qu’elle est strictement inférieure à 70.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est supérieur ou égal à 10
        OU
        qu’elle est supérieur ou égal à 50
        OU
        qu’elle est strictement inférieure à 70.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable monPoids
        est strictement inférieure à 70.
    </fausse>
  </question>
  <question>
    <consigne>
      Dans quelle condition ce programme affichera un a ?
    </consigne>
    <code>
      maPointure = 38
      if maPointure > 45 :
        if maPointure &lt; 50 :
          print("a")
        elif maPointure &lt; 55 :
          print("b")
        else :
          print("c")
      elif maPointure &lt; 20 :
        print("d")
      else :
        print("e")
        if maPointure &lt; 30 :
          print("f")
        else:
          print("g")
    </code>
    <bonne>
      Si la valeur contenue dans la variable maPointure
        est strictement supérieur à 45
        ET
        qu'elle est strictement inférieur à 50.
    </bonne>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement inférieur à 45
        ET
        qu'elle est strictement supérieur à 50.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement supérieur à 45
        OU
        qu'elle est strictement inférieur à 50.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement inférieur à 50.
    </fausse>
  </question>
  <question>
    <consigne>
      Dans quelle condition ce programme affichera un b ?
    </consigne>
    <code>
      maPointure = 38
      if maPointure > 45 :
        if maPointure &lt; 50 :
          print("a")
        elif maPointure &lt; 55 :
          print("b")
        else :
          print("c")
      elif maPointure &lt; 20 :
        print("d")
      else :
        print("e")
        if maPointure &lt; 30 :
          print("f")
        else:
          print("g")
    </code>
    <bonne>
      Si la valeur contenue dans la variable maPointure
        est strictement supérieur à 45
        ET
        qu'elle est supérieur ou égal à 50
        ET
        qu'elle est strictement inférieur à 55.
    </bonne>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement supérieur à 45
        ET
        qu'elle est supérieur à 50
        ET
        qu'elle est strictement inférieur à 55.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement supérieur à 45
        OU
        qu'elle est supérieur ou égal à 50
        OU
        qu'elle est strictement inférieur à 55.
    </fausse>
    <fausse>
      Si la valeur contenue dans la variable maPointure
        est strictement inférieur à 55.
    </fausse>
  </question>
  <question>
    <consigne>
      Que vaut nombre à la fin du programme suivant ?
    </consigne>
    <code>
      nombre = 5
      if nombre &lt; 5 :
        nombre = 2 + 10
    </code>
    <bonne>
      5
    </bonne>
    <fausse>
      12
    </fausse>
    <fausse>
      20
    </fausse>
    <fausse>
      5 et 12
    </fausse>
  </question>
  <question>
    <consigne>
      Que vaut nombre à la fin du programme suivant ?
    </consigne>
    <code>
      nombre = 1
      if nombre >= 0 :
        nombre = nombre + 2
      else :
        nombre = nombre * nombre + 1
    </code>
    <bonne>
      3
    </bonne>
    <fausse>
      1
    </fausse>
    <fausse>
      10
    </fausse>
    <fausse>
      0
    </fausse>
  </question>
  <question>
    <consigne>
      Que vaut nombre à la fin du programme suivant ?
    </consigne>
    <code>
      nombre = -6
      if nombre &lt; 100 :
        if nombre &lt; 0 :
          nombre = nombre * -1
        else:
          nombre = nombre
      else :
        nombre = nombre / 2
    </code>
    <bonne>
      6
    </bonne>
    <fausse>
      -3
    </fausse>
    <fausse>
      -6
    </fausse>
    <fausse>
      3
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      a = 4
      b = 0
      while b &lt; a :
        b = b + 1
        print(b)
    </code>
    <bonne>
      1
      2
      3
      4
    </bonne>
    <fausse>
      0
      1
      2
      3
    </fausse>
    <fausse>
      3
    </fausse>
    <fausse>
      4
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      a = 4
      b = 0
      while b &lt; a :
        print(b)
        b = b + 1
      print("fin")
    </code>
    <bonne>
      0
      1
      2
      3
      fin
    </bonne>
    <fausse>
      3
      fin
    </fausse>
    <fausse>
      0
      1
      2
      3
      4
      fin
    </fausse>
    <fausse>
      1
      2
      3
      4
      fin
    </fausse>
  </question>
  <question>
    <consigne>
      Qu'affiche le programme suivant ?
    </consigne>
    <code>
      a = 4
      b = 0
      while b &lt; a :
        if b == 1:
          b = 3
        print(b)
        b = b + 1
      print(a)
    </code>
    <bonne>
      0
      3
      4
    </bonne>
    <fausse>
      0
      1
      2
      3
      4
    </fausse>
    <fausse>
      0
      4
      3
      4
      4
      4
    </fausse>
    <fausse>
      Toujours la même chose, car c'est une boucle infinie
    </fausse>
  </question>
  <question>
    <consigne>
      Que vaut nombre à la fin du programme ?
    </consigne>
    <code>
      nombre = 5
      if nombre &gt; 0 :
        while nombre &lt; 10 :
          nombre = nombre + 1
        if nombre != 10:
          nombre = 9
      else:
        nombre = 0
    </code>
    <bonne>
      10
    </bonne>
    <fausse>
      9
    </fausse>
    <fausse>
      0
    </fausse>
    <fausse>
      5
    </fausse>
  </question>
  <question>
    <consigne>
      Corrigez le programme pour ne plus faire de boucle infinie.
    </consigne>
    <code>
      a = 5
      b = 90
      while a &lt;= 7 :
        if a &lt; 0 :
          b = b * b
        else:
          b = b - 1
    </code>
    <bonne>
      a = 5
      b = 90
      while a &lt;= 7 :
        if a &lt; 0 :
          a = a * a
        else:
          a = a - 1
    </bonne>
    <fausse>
      a = 5
      b = 90
      while a &lt;= 7 :
        if a &lt; 0 :
          b = b / b
        else:
          b = b - 1
    </fausse>
    <fausse>
      a = 90
      b = 5
      while a &lt;= 7 :
        if a &lt; 0 :
          b = b * b
        else:
          b = b - 1
    </fausse>
    <fausse>
      a = 5
      b = 90
      while a &lt;= 7 :
        if a &lt; 0 :
          a = a / a
        else:
          a = a - 1
    </fausse>
  </question>
</exercice>

</script>
<script>
// ===== Réglage =====
const NB_FAUSSES=3;   // nombre de fausses réponses tirées au hasard à chaque question (Vocabulaire et Exercice)

const $=id=>document.getElementById(id);
const shuffle=a=>{a=a.slice();for(let i=a.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[a[i],a[j]]=[a[j],a[i]]}return a};
const norm=s=>s.replace(/\u00a0/g,' ').replace(/\s+/g,' ').trim();
const esc=s=>s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');

// ===== Coloration syntaxique (Python) =====
const RE_PY=/(#[^\n]*)|("(?:[^"\\\n]|\\.)*"|'(?:[^'\\\n]|\\.)*')|(\bInstructions?[ \u00a0]*\d+\b)|(\b\d+(?:\.\d+)?\b)|(\b(?:if|elif|else|while|for|in|def|return|and|or|not|True|False|None|import|from|as|break|continue|pass)\b)|(\b(?:print|input|int|str|float|len|range)\b)|(==|!=|<=|>=|[<>=+\-*\/%])/g;
function colorer(s){
  let o='',last=0,m;RE_PY.lastIndex=0;
  while((m=RE_PY.exec(s))){
    o+=esc(s.slice(last,m.index));
    const cls=m[1]?'c':m[2]?'s':m[3]?'p':m[4]?'n':m[5]?'k':m[6]?'f':'o';
    o+='<span class="'+cls+'">'+esc(m[0])+'</span>';last=m.index+m[0].length;
  }
  return o+esc(s.slice(last));
}

// ===== Lecture du bloc XML (relu intégralement à chaque ouverture / rechargement) =====
// retire les lignes vides de début/fin et l’indentation commune (le XML peut être indenté librement)
function dedent(s){
  const L=s.replace(/\r/g,'').split('\n');
  while(L.length&&!L[0].trim())L.shift();
  while(L.length&&!L[L.length-1].trim())L.pop();
  const ind=L.filter(l=>l.trim()).map(l=>l.match(/^[ \t]*/)[0].length);
  const m=ind.length?Math.min(...ind):0;
  return L.map(l=>l.slice(Math.min(m,l.length))).join('\n').trim();
}
// texte + mise en forme : seules les balises <b> <i> <u> sont conservées (le reste est affiché comme texte)
function nodeHtml(n){
  let o='';
  for(const c of n.childNodes){
    if(c.nodeType===3||c.nodeType===4)o+=esc(c.nodeValue);
    else if(c.nodeType===1){const t=c.tagName.toLowerCase(),i=nodeHtml(c);o+=['b','i','u'].includes(t)?'<'+t+'>'+i+'</'+t+'>':i}
  }
  return o;
}
const item=el=>({t:dedent(el.textContent),h:dedent(nodeHtml(el))});
const first=(q,tag)=>q.getElementsByTagName(tag)[0];
const questions=(doc,section)=>{const s=doc.getElementsByTagName(section)[0];return s?[...s.getElementsByTagName('question')]:[]};

function lireXML(){
  const doc=new DOMParser().parseFromString('<donnees>'+$('vocabulaire').textContent+'</donnees>','application/xml');
  const err=doc.getElementsByTagName('parsererror')[0];
  if(err)return {erreur:err.textContent.replace(/\s+/g,' ').trim().slice(0,300)};
  const ignorees={};
  // questions à 4 propositions : vocabulaire et exercice
  const choix=section=>{
    let ign=0;const qs=[];
    for(const q of questions(doc,section)){
      const c=first(q,'code'),b=first(q,'bonne'),k=first(q,'consigne');
      const code=c?dedent(c.textContent):'',consigne=k?dedent(k.textContent):'',good=b?item(b):null;
      const bad=[];const vus=new Set();
      for(const f of q.getElementsByTagName('fausse')){const it=item(f);if(it.t&&!vus.has(norm(it.t))){vus.add(norm(it.t));bad.push(it)}}
      if(!(code||consigne)||!good||!good.t||!bad.length){ign++;continue}
      qs.push({code,consigne,good,bad});
    }
    // plusieurs questions de même code : la bonne réponse de l’une n’est jamais proposée comme fausse réponse de l’autre
    const ok={};qs.forEach(q=>{(ok[norm(q.code)]??=new Set()).add(norm(q.good.t))});
    const valides=qs.filter(q=>{q.bad=q.bad.filter(b=>!ok[norm(q.code)].has(norm(b.t)));if(q.bad.length)return true;ign++;return false});
    ignorees[section]=ign;return valides;
  };
  // questions « mettre dans l’ordre »
  const ordre=[];let ign=0;
  for(const q of questions(doc,'replacer')){
    const c=first(q,'code');
    const code=c?dedent(c.textContent):'';
    const lignes=[...q.getElementsByTagName('ligne')].map(item).filter(l=>l.t);
    if(!code||lignes.length<2){ign++;continue}
    ordre.push({code,lignes});
  }
  ignorees.replacer=ign;
  return {vocabulaire:choix('vocabulaire'),ordre,exercice:choix('exercice'),ignorees};
}

// ===== Navigation (menu + 3 pages) =====
const VUES={menu:'Python',vocabulaire:'Vocabulaire',ordre:'Mettre dans l’ordre',exercice:'Exercice'};
let D=null;
function montrer(v){
  $('v-menu').hidden=v!=='menu';
  $('v-quiz').hidden=!(v==='vocabulaire'||v==='exercice');
  $('v-ordre').hidden=v!=='ordre';
  $('back').hidden=v==='menu';
  $('counts').hidden=true;
  $('title').textContent=VUES[v];
  $('info').hidden=v!=='menu';
  if(!D||D.erreur)return;
  if(v==='vocabulaire'||v==='exercice')demarrerQuiz(v);
  if(v==='ordre')demarrerOrdre();
  window.scrollTo(0,0);
}
function compteurs(total,bonnes){$('counts').hidden=false;$('c-tot').textContent=total;$('c-ok').textContent=bonnes;$('c-ko').textContent=total-bonnes}
function route(){const n=location.hash.slice(1);montrer(VUES[n]&&n!=='menu'&&D&&!D.erreur&&(n==='ordre'?D.ordre:D[n]).length?n:'menu')}
addEventListener('hashchange',route);
document.querySelectorAll('[data-go]').forEach(b=>b.onclick=()=>{location.hash=b.dataset.go});
$('back').onclick=()=>{location.hash='menu'};

// ===== Pages Vocabulaire et Exercice : 1 code, 4 propositions =====
let Q={};
function demarrerQuiz(mode){
  Q={mode,data:D[mode],deck:[],good:0,total:0,answered:false};
  $('lbl1').hidden=mode==='exercice';
  $('lbl2').textContent=mode==='exercice'?'Quelle est la bonne réponse ?':'Quelle est la bonne traduction ?';
  compteurs(0,0);
  suivante();
}
function suivante(){
  if(!Q.deck.length)Q.deck=shuffle(Q.data.map((_,i)=>i));   // chaque question est posée une fois avant qu’une question revienne
  const q=Q.data[Q.deck.pop()];Q.answered=false;
  $('consigne').hidden=!q.consigne;$('consigne').textContent=q.consigne||'';
  $('code').hidden=!q.code;$('code').innerHTML=colorer(q.code);
  const opts=shuffle([{h:q.good.h,ok:true},...shuffle(q.bad).slice(0,NB_FAUSSES).map(b=>({h:b.h,ok:false}))]);
  const box=$('opts');box.innerHTML='';
  opts.forEach(o=>{const b=document.createElement('button');b.type='button';b.className='opt';b.innerHTML=o.h;b.onclick=()=>repondre(b,o.ok,opts);box.appendChild(b)});
  $('fb').textContent='';$('fb').style.color='';$('next').style.display='none';
  window.scrollTo(0,0);
}
function repondre(btn,ok,opts){
  if(Q.answered)return;Q.answered=true;Q.total++;if(ok)Q.good++;
  [...$('opts').children].forEach((b,k)=>{b.disabled=true;if(opts[k].ok)b.classList.add('ok')});
  if(!ok)btn.classList.add('ko');
  $('fb').textContent=ok?'Bravo, c’est la bonne réponse !':'Raté. La bonne réponse est en vert.';
  $('fb').style.color=ok?'var(--okb)':'var(--kob)';
  compteurs(Q.total,Q.good);
  $('next').style.display='block';
  $('next').scrollIntoView({block:'nearest',behavior:'smooth'});
}
$('next').onclick=suivante;

// ===== Page « Mettre dans l’ordre » =====
let O={};
function demarrerOrdre(){O={data:D.ordre,deck:[],good:0,total:0,cur:[],sol:[],valide:false};compteurs(0,0);suivanteOrdre()}
function suivanteOrdre(){
  if(!O.deck.length)O.deck=shuffle(O.data.map((_,i)=>i));
  const q=O.data[O.deck.pop()];O.valide=false;O.sol=q.lignes;
  let m=shuffle(q.lignes);
  for(let k=0;k<20&&m.every((l,i)=>norm(l.t)===norm(q.lignes[i].t))&&new Set(q.lignes.map(l=>norm(l.t))).size>1;k++)m=shuffle(q.lignes);
  O.cur=m;
  $('o-code').innerHTML=colorer(q.code);
  const box=$('lines');box.innerHTML='';box.classList.remove('locked');
  m.forEach((l,i)=>box.appendChild(creerLigne(l,i,box)));
  majBoutons();
  $('o-fb').textContent='';$('o-corr').hidden=true;$('o-corr-list').innerHTML='';
  $('o-valider').hidden=false;$('o-next').hidden=true;
  window.scrollTo(0,0);
}
function majBoutons(){
  const L=[...$('lines').children];
  L.forEach((d,i)=>{d.querySelector('.up').disabled=i===0;d.querySelector('.dn').disabled=i===L.length-1});
}
function creerLigne(l,i,box){
  const d=document.createElement('div');d.className='line';d.dataset.i=i;
  d.innerHTML='<span class="h" aria-hidden="true">⠿</span><span class="t">'+l.h+'</span><span class="mv"><button type="button" class="up" aria-label="Monter la ligne">▲</button><button type="button" class="dn" aria-label="Descendre la ligne">▼</button></span>';
  d.querySelector('.up').onclick=()=>{const p=d.previousElementSibling;if(p){box.insertBefore(d,p);majBoutons();d.querySelector('.up').focus({preventScroll:true});d.scrollIntoView({block:'nearest'})}};
  d.querySelector('.dn').onclick=()=>{const n=d.nextElementSibling;if(n){box.insertBefore(n,d);majBoutons();d.querySelector('.dn').focus({preventScroll:true});d.scrollIntoView({block:'nearest'})}};
  d.querySelector('.h').addEventListener('pointerdown',e=>{if(e.button===0)glisser(e,d,box)});
  d.querySelector('.t').addEventListener('pointerdown',e=>{if(e.pointerType==='mouse'&&e.button===0)glisser(e,d,box)});
  return d;
}
// Glisser-déposer : la ligne suit le doigt/la souris, les autres s’écartent ; l’ordre n’est modifié qu’au relâchement.
// On peut ainsi déplacer une ligne de plusieurs places d’un seul geste.
function glisser(e,d,box){
  if(O.valide)return;
  e.preventDefault();
  const items=[...box.children],n=items.length,from=items.indexOf(d);
  const R=items.map(x=>x.getBoundingClientRect());
  const gap=n>1?R[1].top-R[0].bottom:0,hd=R[from].height+gap;
  const y0=e.clientY,s0=window.scrollY;let y=y0,to=from;
  d.classList.add('drag');box.classList.add('dragging');
  try{d.setPointerCapture(e.pointerId)}catch(_){}
  const maj=()=>{
    const dy=(y-y0)+(window.scrollY-s0);
    d.style.transform='translateY('+dy+'px)';
    const c=R[from].top+R[from].height/2+dy;
    to=0;items.forEach((x,i)=>{if(i!==from&&R[i].top+R[i].height/2<c)to++});
    items.forEach((x,i)=>{
      if(i===from)return;
      const s=(to<from&&i>=to&&i<from)?hd:(to>from&&i>from&&i<=to)?-hd:0;
      x.style.transform=s?'translateY('+s+'px)':'';
    });
  };
  const bouge=ev=>{y=ev.clientY;maj()};
  const defile=setInterval(()=>{if(y<70)window.scrollBy(0,-10);else if(y>innerHeight-70)window.scrollBy(0,10);else return;maj()},16);
  const fin=()=>{
    clearInterval(defile);
    removeEventListener('pointermove',bouge);removeEventListener('pointerup',fin);removeEventListener('pointercancel',fin);removeEventListener('blur',fin);
    box.classList.remove('dragging');d.classList.remove('drag');
    items.forEach(x=>{x.style.transform=''});
    box.insertBefore(d,items.filter(x=>x!==d)[to]||null);
    majBoutons();
    try{d.releasePointerCapture(e.pointerId)}catch(_){}
  };
  addEventListener('pointermove',bouge);addEventListener('pointerup',fin);addEventListener('pointercancel',fin);addEventListener('blur',fin);
}
$('o-valider').onclick=()=>{
  if(O.valide)return;O.valide=true;
  const box=$('lines'),L=[...box.children];let bonnes=0;
  L.forEach((d,k)=>{const ok=norm(O.cur[+d.dataset.i].t)===norm(O.sol[k].t);d.classList.add(ok?'ok':'ko');if(ok)bonnes++});
  box.classList.add('locked');
  const tout=bonnes===L.length;O.total++;if(tout)O.good++;
  $('o-fb').textContent=tout?'Bravo, tout est dans le bon ordre !':bonnes+' ligne'+(bonnes>1?'s':'')+' bien placée'+(bonnes>1?'s':'')+' sur '+L.length+'. La correction est ci-dessous.';
  $('o-fb').style.color=tout?'var(--okb)':'var(--kob)';
  $('o-corr-list').innerHTML=O.sol.map((l,k)=>'<div class="cl"><span class="n">'+(k+1)+'</span><span class="t">'+l.h+'</span></div>').join('');
  $('o-corr').hidden=false;
  compteurs(O.total,O.good);
  $('o-valider').hidden=true;$('o-next').hidden=false;
  $('o-fb').scrollIntoView({block:'nearest',behavior:'smooth'});
};
$('o-next').onclick=suivanteOrdre;

// ===== Compteurs : infobulle (souris) ou boîte de dialogue (écran tactile) =====
const AIDE={'c-tot':['Questions traitées','Nombre de questions auxquelles vous avez répondu.'],'c-ok':['Bonnes réponses','Nombre de questions réussies.'],'c-ko':['Mauvaises réponses','Nombre de questions ratées.']};
document.querySelectorAll('.cnt').forEach(b=>b.onclick=()=>{
  if(!matchMedia('(hover: none)').matches)return;
  const [t,d]=AIDE[b.id];
  $('dlgtxt').innerHTML='<strong>'+t+' : '+b.textContent+'</strong><br>'+d;
  if($('dlg').showModal)$('dlg').showModal();else alert(t+' : '+b.textContent+'\n'+d);
});
$('dlgok').onclick=()=>$('dlg').close();

// ===== Démarrage =====
(function(){
  try{D=lireXML()}catch(e){D={erreur:String(e)}}
  if(D.erreur){
    $('err').hidden=false;
    $('errmsg').textContent='Le bloc XML n’est pas valide : '+D.erreur+' — Astuce : un signe < ou & dans un texte doit s’écrire &lt; ou &amp; (ou être placé dans un CDATA).';
    document.querySelectorAll('[data-go]').forEach(b=>b.disabled=true);
  }else{
    const n={vocabulaire:D.vocabulaire.length,ordre:D.ordre.length,exercice:D.exercice.length};
    const lib=k=>n[k]?n[k]+' question'+(n[k]>1?'s':''):'aucune question';
    for(const k in n){$('n-'+k).textContent=lib(k);document.querySelector('[data-go="'+k+'"]').disabled=!n[k]}
    const ign=Object.values(D.ignorees).reduce((a,b)=>a+b,0);
    $('info').textContent=ign?ign+' question(s) ignorée(s) (réponses ou lignes manquantes)':'';
  }
  route();
})();
</script>
</body>
</html>
