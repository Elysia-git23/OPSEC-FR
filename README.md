# OPSEC-FR


<style>
*{box-sizing:border-box;margin:0;padding:0}
.card{background:var(--color-background-primary);border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:1rem 1.25rem;margin-bottom:12px}
.badge{font-size:11px;padding:2px 8px;border-radius:10px;font-weight:500;display:inline-block}
.bp{background:#EEEDFE;color:#3C3489}.bt{background:#E1F5EE;color:#085041}.ba{background:#FAEEDA;color:#633806}.br{background:#FCEBEB;color:#791F1F}.bg{background:#EAF3DE;color:#27500A}
.title{font-size:15px;font-weight:500;color:var(--color-text-primary);margin-bottom:6px;display:flex;align-items:center;gap:8px}
.body{font-size:13px;color:var(--color-text-secondary);line-height:1.7}
.nav{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:1.5rem}
.nb{padding:6px 14px;font-size:13px;border-radius:20px;border:0.5px solid var(--color-border-secondary);background:var(--color-background-primary);color:var(--color-text-secondary);cursor:pointer;transition:all .15s}
.nb.active{background:#EEEDFE;color:#3C3489;border-color:#AFA9EC;font-weight:500}
.nb:hover:not(.active){background:var(--color-background-secondary)}
.sec{display:none}.sec.active{display:block}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:10px;margin-top:10px}
.item{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:10px 12px}
.iname{font-size:13px;font-weight:500;color:var(--color-text-primary)}
.idesc{font-size:12px;color:var(--color-text-secondary);margin-top:3px}
.step{display:flex;gap:12px;align-items:flex-start;margin-bottom:14px}
.snum{width:28px;height:28px;border-radius:50%;background:#EEEDFE;color:#3C3489;font-size:13px;font-weight:500;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.stitle{font-size:14px;font-weight:500;color:var(--color-text-primary)}
.sdesc{font-size:13px;color:var(--color-text-secondary);margin-top:3px;line-height:1.6}
code{font-family:var(--font-mono);background:var(--color-background-secondary);padding:1px 6px;border-radius:4px;font-size:12px;color:var(--color-text-primary)}
.hdr{font-size:18px;font-weight:500;color:var(--color-text-primary);margin-bottom:4px}
.sub{font-size:13px;color:var(--color-text-secondary);margin-bottom:1.5rem}
.prog{height:4px;background:var(--color-background-secondary);border-radius:2px;margin-bottom:1.5rem}
.pfill{height:100%;background:#7F77DD;border-radius:2px;transition:width .3s}
.level{display:flex;align-items:center;gap:10px;padding:10px 12px;border-radius:var(--border-radius-md);margin-bottom:8px;border:0.5px solid var(--color-border-tertiary)}
.dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}
.ltext{font-size:13px;color:var(--color-text-primary)}
.lsub{font-size:12px;color:var(--color-text-secondary)}
</style>

<h2 class="sr-only">Guide complet OPSEC — Sécurité opérationnelle</h2>

<div style="padding:1rem 0">
<div class="prog"><div class="pfill" id="pf" style="width:20%"></div></div>

<nav class="nav">
  <button class="nb active" onclick="show('def',0)"><i class="ti ti-info-circle" aria-hidden="true"></i> Définition</button>
  <button class="nb" onclick="show('process',1)"><i class="ti ti-route" aria-hidden="true"></i> Processus</button>
  <button class="nb" onclick="show('menaces',2)"><i class="ti ti-alert-triangle" aria-hidden="true"></i> Menaces</button>
  <button class="nb" onclick="show('pratiques',3)"><i class="ti ti-shield-lock" aria-hidden="true"></i> Pratiques</button>
  <button class="nb" onclick="show('outils',4)"><i class="ti ti-tool" aria-hidden="true"></i> Outils</button>
</nav>

<!-- DÉFINITION -->
<div class="sec active" id="sec-def">
  <p class="hdr">OPSEC — Operational Security</p>
  <p class="sub">Protéger ses informations sensibles contre les adversaires</p>

  <div class="card">
    <div class="title"><i class="ti ti-book" style="color:#7F77DD" aria-hidden="true"></i> C'est quoi l'OPSEC ? <span class="badge bp">Fondamental</span></div>
    <div class="body">L'OPSEC (Sécurité Opérationnelle) est un processus qui identifie les informations critiques, analyse les menaces, et met en place des contre-mesures pour protéger ces informations contre des adversaires. Né dans l'armée américaine, il est aujourd'hui essentiel en cybersécurité.</div>
  </div>

  <div class="card" style="background:#EEEDFE;border-color:#AFA9EC">
    <div class="title" style="color:#3C3489"><i class="ti ti-quote" aria-hidden="true"></i> La règle d'or</div>
    <div class="body" style="color:#534AB7;font-style:italic">"Si l'ennemi connaît vos plans, vos plans ne valent rien."<br><span style="font-style:normal;font-size:12px;color:#7F77DD">— Principe fondateur de l'OPSEC militaire</span></div>
  </div>

  <div class="grid">
    <div class="item">
      <div class="iname"><i class="ti ti-military" style="color:#7F77DD" aria-hidden="true"></i> Origine militaire</div>
      <div class="idesc">Créé pendant la guerre du Vietnam (opération Purple Dragon, 1967)</div>
    </div>
    <div class="item">
      <div class="iname"><i class="ti ti-shield" style="color:#1D9E75" aria-hidden="true"></i> Usage cyber</div>
      <div class="idesc">Protéger identité, méthodes, cibles lors d'investigations ou pentests</div>
    </div>
    <div class="item">
      <div class="iname"><i class="ti ti-eye-off" style="color:#BA7517" aria-hidden="true"></i> Usage OSINT</div>
      <div class="idesc">Rester anonyme pendant une investigation sans révéler qu'on enquête</div>
    </div>
    <div class="item">
      <div class="iname"><i class="ti ti-user-shield" style="color:#D4537E" aria-hidden="true"></i> Usage perso</div>
      <div class="idesc">Protéger sa vie privée en ligne au quotidien</div>
    </div>
  </div>

  <div class="card" style="margin-top:12px">
    <div class="title"><i class="ti ti-vs" style="color:#7F77DD" aria-hidden="true"></i> OPSEC vs Cybersécurité classique</div>
    <div class="body">
      <div style="display:flex;gap:8px;margin-top:6px;flex-wrap:wrap">
        <div style="flex:1;min-width:140px;background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:10px">
          <div style="font-weight:500;font-size:13px;color:var(--color-text-primary);margin-bottom:6px">Cybersécurité</div>
          <div class="idesc">Protège les systèmes et données contre les attaques techniques</div>
        </div>
        <div style="flex:1;min-width:140px;background:#EEEDFE;border-radius:var(--border-radius-md);padding:10px;border:0.5px solid #AFA9EC">
          <div style="font-weight:500;font-size:13px;color:#3C3489;margin-bottom:6px">OPSEC</div>
          <div style="font-size:12px;color:#534AB7">Protège les informations comportementales et opérationnelles contre l'analyse humaine</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- PROCESSUS -->
<div class="sec" id="sec-process">
  <p class="hdr">Le processus OPSEC en 5 étapes</p>
  <p class="sub">La méthodologie officielle utilisée par les professionnels</p>

  <div class="step">
    <div class="snum">1</div>
    <div>
      <div class="stitle">Identifier les informations critiques</div>
      <div class="sdesc">Quelles infos, si elles tombaient entre mauvaises mains, causeraient un dommage ? Exemples : ton identité réelle, ta cible, ta méthode, ton timing, tes outils utilisés.</div>
    </div>
  </div>
  <div class="step">
    <div class="snum">2</div>
    <div>
      <div class="stitle">Analyser les menaces</div>
      <div class="sdesc">Qui veut ces informations ? Un script kiddie, un groupe de hackers, une entreprise, un gouvernement ? Chaque adversaire a des capacités différentes.</div>
    </div>
  </div>
  <div class="step">
    <div class="snum">3</div>
    <div>
      <div class="stitle">Analyser les vulnérabilités</div>
      <div class="sdesc">Comment l'adversaire pourrait-il obtenir ces infos ? Réseaux sociaux, logs de connexion, métadonnées, habitudes en ligne, cercle social...</div>
    </div>
  </div>
  <div class="step">
    <div class="snum">4</div>
    <div>
      <div class="stitle">Évaluer les risques</div>
      <div class="sdesc">Probabilité × Impact = Risque. Prioriser les vulnérabilités les plus critiques à corriger en premier.</div>
    </div>
  </div>
  <div class="step">
    <div class="snum">5</div>
    <div>
      <div class="stitle">Appliquer des contre-mesures</div>
      <div class="sdesc">Mettre en place les protections : VPN, pseudonymes, chiffrement, compartimentation, fausses pistes, changement d'habitudes...</div>
    </div>
  </div>

  <div class="card" style="background:#E1F5EE;border-color:#5DCAA5">
    <div class="title" style="color:#085041"><i class="ti ti-repeat" aria-hidden="true"></i> C'est un cycle continu</div>
    <div class="body" style="color:#0F6E56">L'OPSEC n'est pas une action unique — c'est une mentalité permanente. Les menaces évoluent, les habitudes changent, les contre-mesures deviennent obsolètes. Il faut réévaluer régulièrement.</div>
  </div>
</div>

<!-- MENACES -->
<div class="sec" id="sec-menaces">
  <p class="hdr">Les menaces OPSEC principales</p>
  <p class="sub">Ce qui peut trahir ton identité ou tes actions</p>

  <div class="card">
    <div class="title"><i class="ti ti-device-analytics" style="color:#E24B4A" aria-hidden="true"></i> Fuites de métadonnées <span class="badge br">Critique</span></div>
    <div class="body">Les fichiers que tu envoies contiennent des infos cachées : coordonnées GPS dans les photos, nom d'auteur dans les documents Word, logiciel utilisé, date de création. Invisibles mais révélateurs.</div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-wifi" style="color:#BA7517" aria-hidden="true"></i> Empreinte réseau <span class="badge ba">Élevé</span></div>
    <div class="body">Ton adresse IP réelle, les sites que tu visites, les heures de connexion, les requêtes DNS — tout est loggué par ton FAI et les sites web. Sans protection, tu es traçable.</div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-social" style="color:#7F77DD" aria-hidden="true"></i> Réseaux sociaux <span class="badge ba">Élevé</span></div>
    <div class="body">Un like à 3h du matin, une photo avec un reflet dans les lunettes, un commentaire qui révèle ta localisation, un ancien pseudo lié à ton vrai nom — les réseaux sociaux sont la plus grande fuite OPSEC.</div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-brain" style="color:#1D9E75" aria-hidden="true"></i> Habitudes comportementales <span class="badge bt">Moyen</span></div>
    <div class="body">Tu te connectes toujours entre 20h et 23h ? Tu utilises toujours le même style d'écriture ? Tu fais toujours les mêmes fautes ? Ces patterns permettent de t'identifier même sans ton vrai nom.</div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-users" style="color:#D4537E" aria-hidden="true"></i> Cercle social (HUMINT) <span class="badge bt">Moyen</span></div>
    <div class="body">Un adversaire peut obtenir des infos sur toi via tes amis, collègues ou famille — qui ne savent pas qu'ils partagent des infos sensibles. C'est le vecteur le plus sous-estimé.</div>
  </div>
</div>

<!-- PRATIQUES -->
<div class="sec" id="sec-pratiques">
  <p class="hdr">Bonnes pratiques OPSEC</p>
  <p class="sub">Ce qu'un professionnel applique au quotidien</p>

  <div style="margin-bottom:16px">
    <div class="level">
      <div class="dot" style="background:#639922"></div>
      <div><div class="ltext">Niveau 1 — Bases essentielles</div><div class="lsub">Pour tout le monde</div></div>
    </div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Pseudonymes séparés</div><div class="idesc">Un pseudo différent par plateforme, jamais lié à ton vrai nom</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Emails jetables</div><div class="idesc">ProtonMail, Tutanota ou SimpleLogin pour les inscriptions sensibles</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Nettoyer les métadonnées</div><div class="idesc">ExifTool avant de partager photos et documents</div></div>
  </div>

  <div style="margin-bottom:16px">
    <div class="level">
      <div class="dot" style="background:#BA7517"></div>
      <div><div class="ltext">Niveau 2 — Protection réseau</div><div class="lsub">Pour investigations OSINT</div></div>
    </div>
    <div class="item" style="margin-bottom:6px"><div class="iname">VPN de confiance</div><div class="idesc">Mullvad ou ProtonVPN — sans logs, payé en crypto</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Machine virtuelle dédiée</div><div class="idesc">VM Kali séparée pour chaque mission — snapshot avant / après</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">DNS chiffré</div><div class="idesc">DNS over HTTPS pour éviter les fuites de requêtes</div></div>
  </div>

  <div>
    <div class="level">
      <div class="dot" style="background:#A32D2D"></div>
      <div><div class="ltext">Niveau 3 — Anonymat avancé</div><div class="lsub">Pour opérations sensibles</div></div>
    </div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Tails OS</div><div class="idesc">OS live sur clé USB, laisse zéro trace sur la machine</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Réseau Tor</div><div class="idesc">Anonymise le trafic via 3 relais chiffrés</div></div>
    <div class="item" style="margin-bottom:6px"><div class="iname">Compartimentation totale</div><div class="idesc">Séparer strictement identités réelle et opérationnelle — jamais de mélange</div></div>
  </div>
</div>

<!-- OUTILS -->
<div class="sec" id="sec-outils">
  <p class="hdr">Arsenal d'outils OPSEC</p>
  <p class="sub">Les outils utilisés par les professionnels</p>

  <div class="card">
    <div class="title"><i class="ti ti-device-desktop" style="color:#7F77DD" aria-hidden="true"></i> Systèmes d'exploitation sécurisés</div>
    <div class="grid">
      <div class="item"><div class="iname">Tails OS</div><div class="idesc">Live USB, amnésique, aucune trace laissée</div></div>
      <div class="item"><div class="iname">Whonix</div><div class="idesc">OS dans VM, tout le trafic passe par Tor</div></div>
      <div class="item"><div class="iname">Qubes OS</div><div class="idesc">Compartimentation par VMs isolées</div></div>
    </div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-network" style="color:#1D9E75" aria-hidden="true"></i> Anonymisation réseau</div>
    <div class="grid">
      <div class="item"><div class="iname">Tor Browser</div><div class="idesc">Navigation anonyme via réseau Tor</div></div>
      <div class="item"><div class="iname">Mullvad VPN</div><div class="idesc">Sans logs, accepte cash et crypto</div></div>
      <div class="item"><div class="iname">ProtonVPN</div><div class="idesc">Open source, basé en Suisse</div></div>
    </div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-lock" style="color:#BA7517" aria-hidden="true"></i> Chiffrement et communications</div>
    <div class="grid">
      <div class="item"><div class="iname">Signal</div><div class="idesc">Messagerie chiffrée de bout en bout</div></div>
      <div class="item"><div class="iname">ProtonMail</div><div class="idesc">Email chiffré, serveurs en Suisse</div></div>
      <div class="item"><div class="iname">VeraCrypt</div><div class="idesc">Chiffrement de disques et fichiers</div></div>
    </div>
  </div>

  <div class="card">
    <div class="title"><i class="ti ti-photo-off" style="color:#D4537E" aria-hidden="true"></i> Nettoyage de traces</div>
    <div class="grid">
      <div class="item"><div class="iname">ExifTool</div><div class="idesc">Supprime métadonnées photos/docs</div><code>exiftool -all= photo.jpg</code></div>
      <div class="item"><div class="iname">MAT2</div><div class="idesc">Nettoyage automatique de métadonnées</div></div>
      <div class="item"><div class="iname">BleachBit</div><div class="idesc">Efface traces système et navigateur</div></div>
    </div>
  </div>
</div>

</div>

<script>
const secs=['def','process','menaces','pratiques','outils'];
function show(name,idx){
  secs.forEach(s=>{document.getElementById('sec-'+s).classList.remove('active')});
  document.getElementById('sec-'+name).classList.add('active');
  document.querySelectorAll('.nb').forEach((b,i)=>b.classList.toggle('active',i===idx));
  document.getElementById('pf').style.width=Math.round((idx+1)/5*100)+'%';
}
</script>
