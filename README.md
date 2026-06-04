

base = Path("/mnt/data/mirelas_premium_website")
base.mkdir(exist_ok=True)

assets = {
    "hero-flyer.jpeg": "/mnt/data/A5C02F8D-503C-4EE1-9F02-345F94BA15F1.jpeg",
    "preise-flyer.jpeg": "/mnt/data/174A0149-8FEE-46A5-8FFE-3726E7E6D643.jpeg",
    "cocktailshot.jpeg": "/mnt/data/9AC7852C-8750-48BF-B435-3306703295D2.jpeg",
    "haarverlaengerung.jpeg": "/mnt/data/AC1F0420-BB38-4857-BFBA-54DCA67A9395.jpeg",
    "kontakt-qr.jpeg": "/mnt/data/B58E66C9-4592-40DF-A8A3-2BF7EF06DCD2.jpeg",
}
for name, src in assets.items():
    p = Path(src)
    if p.exists():
        shutil.copy(p, base / name)

html = r"""<!doctype html>
<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Mirela's Hairstyle | Damenfriseur Offenburg</title>
<meta name="description" content="Mirela's Hairstyle in Offenburg: Damenfriseur, Balayage, Strähnen, Styling, Cocktailshot, Haarverlängerung, Brautstyling und Make-up.">
<style>
:root{
  --gold:#b58428; --gold2:#edcf82; --dark:#120c07; --cream:#fffaf1; --soft:#fbf0dc; --line:#e8d4aa;
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;background:var(--cream);color:var(--dark);font-family:Georgia,'Times New Roman',serif;line-height:1.55}
a{text-decoration:none;color:inherit}
.topbar{position:sticky;top:0;z-index:50;background:rgba(255,250,241,.96);border-bottom:1px solid var(--line);backdrop-filter:blur(10px)}
.nav{max-width:1220px;margin:auto;display:flex;align-items:center;justify-content:space-between;gap:18px;padding:12px 18px}
.logo{font-size:25px;color:var(--gold);font-weight:bold;letter-spacing:.5px}
.menu{display:flex;gap:18px;align-items:center;flex-wrap:wrap;font-size:14px;text-transform:uppercase}
.menu a:hover{color:var(--gold)}
.btn{display:inline-block;background:linear-gradient(135deg,var(--gold),var(--gold2));color:white;padding:12px 22px;border-radius:999px;font-weight:bold;box-shadow:0 10px 22px #b5842840}
.btn.white{background:white;color:var(--gold);border:1px solid var(--gold);box-shadow:none}
.hero{
  min-height:88vh;display:flex;align-items:center;padding:70px 18px;
  background:linear-gradient(90deg,rgba(255,250,241,.98) 0%,rgba(255,250,241,.78) 45%,rgba(255,250,241,.22) 100%),url('hero-flyer.jpeg') center/cover no-repeat;
}
.hero-inner{max-width:1220px;margin:auto;width:100%;display:grid;grid-template-columns:1fr .72fr;gap:32px;align-items:center}
.badge{display:inline-block;color:var(--gold);border:1px solid var(--gold);padding:8px 14px;border-radius:999px;background:#fff9;font-weight:bold}
h1{font-size:clamp(48px,8vw,96px);line-height:.92;color:var(--gold);font-weight:normal;margin:18px 0 10px}
.hero h2{font-size:clamp(23px,3vw,38px);font-weight:normal;margin:0 0 18px}
.hero p{font-size:18px;max-width:620px}
.panel{background:#fffdf8e8;border:1px solid var(--line);border-radius:28px;padding:26px;box-shadow:0 22px 55px #00000017}
.panel h3{color:var(--gold);font-size:28px;margin:0 0 12px}
.quick{max-width:1220px;margin:-45px auto 0;padding:0 18px;position:relative;z-index:3}
.quick-grid{background:#fff;border:1px solid var(--line);border-radius:22px;padding:18px;display:grid;grid-template-columns:repeat(5,1fr);gap:12px;box-shadow:0 18px 40px #0001}
.quick-grid div{text-align:center;color:#6e4b13;font-weight:bold}
section{max-width:1220px;margin:auto;padding:65px 18px}
.title{text-align:center;margin-bottom:34px}
.title h2{font-size:clamp(32px,5vw,52px);color:var(--gold);font-weight:normal;margin:0}
.title p{max-width:760px;margin:10px auto 0}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:20px}
.card{background:white;border:1px solid var(--line);border-radius:24px;overflow:hidden;box-shadow:0 12px 30px #0000000e}
.card img{width:100%;height:205px;object-fit:cover;display:block}
.card div{padding:22px}
.card h3{color:var(--gold);font-size:25px;margin:0 0 10px}
.card ul{padding-left:18px}
.price-box{border:1px solid var(--line);border-radius:24px;background:white;overflow:hidden;box-shadow:0 14px 35px #0000000d}
table{width:100%;border-collapse:collapse}
th,td{border-bottom:1px solid #ead9b9;padding:14px 16px;text-align:left}
th{background:#fbf1dc;color:var(--gold);font-size:19px}
.dark{max-width:none;background:radial-gradient(circle at 30% 20%,#4b310d,#120c07 55%);color:white}
.dark .wrap{max-width:1220px;margin:auto;padding:60px 18px;display:grid;grid-template-columns:1fr 1fr;gap:32px;align-items:center}
.dark h2{font-size:48px;color:var(--gold2);font-weight:normal;margin:0 0 12px}
.dark img,.feature-img{width:100%;border-radius:25px;border:1px solid #72501a;box-shadow:0 16px 40px #0004}
.gallery{display:grid;grid-template-columns:repeat(auto-fit,minmax(255px,1fr));gap:18px}
.gallery a img{width:100%;height:380px;object-fit:cover;border-radius:22px;border:1px solid var(--line);box-shadow:0 14px 34px #0001}
.social{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:18px;text-align:center}
.social a{background:white;border:1px solid var(--line);border-radius:22px;padding:24px;box-shadow:0 12px 28px #0000000d;font-weight:bold}
.contact{max-width:none;background:#100b06;color:white}
.contact .wrap{max-width:1220px;margin:auto;padding:56px 18px;display:grid;grid-template-columns:1.2fr 1fr 1fr;gap:25px}
.contact h3{color:var(--gold2);font-size:25px;margin-top:0}
.footer{text-align:center;background:#070503;color:#e7c36a;padding:18px}
.float-wa{position:fixed;right:18px;bottom:18px;z-index:80;background:#25d366;color:white;border-radius:999px;padding:14px 18px;font-weight:bold;box-shadow:0 10px 28px #0004}
iframe{width:100%;height:330px;border:0;border-radius:24px;border:1px solid var(--line)}
@media(max-width:850px){
  .menu{display:none}.hero-inner,.dark .wrap,.contact .wrap{grid-template-columns:1fr}
  .quick-grid{grid-template-columns:1fr 1fr}.hero{min-height:auto}.panel{padding:20px}
}
</style>
</head>
<body>

<a class="float-wa" href="https://wa.me/4917661072119?text=Hallo%20Mirela%2C%20ich%20m%C3%B6chte%20einen%20Termin%20vereinbaren." target="_blank">WhatsApp</a>

<div class="topbar">
  <div class="nav">
    <a class="logo" href="#home">Mirela's Hairstyle</a>
    <div class="menu">
      <a href="#leistungen">Leistungen</a>
      <a href="#preise">Preise</a>
      <a href="#cocktailshot">Cocktailshot</a>
      <a href="#extensions">Extensions</a>
      <a href="#galerie">Galerie</a>
      <a href="#links">Links</a>
      <a href="#kontakt">Kontakt</a>
    </div>
    <a class="btn" href="tel:+4917661072119">Termin buchen</a>
  </div>
</div>

<header id="home" class="hero">
  <div class="hero-inner">
    <div>
      <span class="badge">Nur Damenfriseur · Offenburg</span>
      <h1>Mirela's Hairstyle</h1>
      <h2>Ihr Friseur für Schönheit mit Leidenschaft</h2>
      <p>Damenhaarschnitt, Styling, Farbe, Strähnen, Balayage, Cocktailshot, Brautstyling und Haarverlängerung – elegant, professionell und mit Liebe zum Detail.</p>
      <p>
        <a class="btn" href="tel:+4917661072119">01766 1072119 anrufen</a>
        <a class="btn white" href="#preise">Preise ansehen</a>
      </p>
    </div>
    <div class="panel">
      <h3>Termin vereinbaren</h3>
      <p><strong>Telefon:</strong><br><a href="tel:+4917661072119">01766 1072119</a></p>
      <p><strong>Adresse:</strong><br><a target="_blank" href="https://www.google.com/maps/search/?api=1&query=Marlenstra%C3%9Fe%207%2C%2077656%20Offenburg">Marlenstraße 7, 77656 Offenburg</a></p>
      <p><strong>Öffnungszeiten:</strong><br>Di – Fr: 09:00 – 18:00 Uhr<br>Sa: 08:00 – 14:00 Uhr</p>
      <a class="btn" target="_blank" href="https://wa.me/4917661072119?text=Hallo%20Mirela%2C%20ich%20m%C3%B6chte%20einen%20Termin%20vereinbaren.">Nachricht senden</a>
    </div>
  </div>
</header>

<div class="quick">
  <div class="quick-grid">
    <div>✨ Mehr Glanz</div>
    <div>🤍 Geschmeidigkeit</div>
    <div>🛡️ Schutz & Pflege</div>
    <div>⭐ Salonqualität</div>
    <div>💛 Persönliche Beratung</div>
  </div>
</div>

<section id="leistungen">
  <div class="title">
    <h2>Meine Leistungen</h2>
    <p>Schön strukturierte Angebote für deine Kundinnen – vom Schnitt bis zur Haarverlängerung.</p>
  </div>
  <div class="grid">
    <div class="card"><img src="hero-flyer.jpeg"><div><h3>Schnitt & Styling</h3><p>Waschen, Schneiden, Föhnen und professionelles Styling.</p></div></div>
    <div class="card"><img src="preise-flyer.jpeg"><div><h3>Farbe & Balayage</h3><p>Ansatzfarbe, Strähnen, Balayage, Toner und Veredelung.</p></div></div>
    <div class="card"><img src="haarverlaengerung.jpeg"><div><h3>Haarverlängerung</h3><p>Tape, Bonding, Micro Bonding und Mikrorings.</p></div></div>
    <div class="card"><img src="cocktailshot.jpeg"><div><h3>Pflege & Cocktailshot</h3><p>Luxuriöse Intensivpflege für geschädigtes Haar.</p></div></div>
  </div>
</section>

<section id="preise">
  <div class="title">
    <h2>Preisliste</h2>
    <p>Alle Preise sind ab-Preise. Der genaue Preis richtet sich nach Haarlänge, Haarmenge und Aufwand.</p>
  </div>
  <div class="price-box">
    <table>
      <tr><th>Leistung</th><th>Preis</th></tr>
      <tr><td>Waschen & Schneiden kurz / mittel / lang</td><td>ab 35 € / 45 € / 55 €</td></tr>
      <tr><td>Waschen, Schneiden & Stylen kurz / mittel / lang</td><td>ab 55 € / 65 € / 85 €</td></tr>
      <tr><td>Stylen kurz / mittel / lang</td><td>ab 35 € / 50 € / 65 €</td></tr>
      <tr><td>Ansatzfarbe inkl. Waschen, Pflege & Föhnen</td><td>ab 50 €</td></tr>
      <tr><td>Ansatzsträhnen 50 % inkl. Toner, Pflege & Föhnen</td><td>ab 130 – 150 €</td></tr>
      <tr><td>Closing</td><td>ab 50 €</td></tr>
      <tr><td>Komplette Kopfsträhnen kurz / mittel / lang</td><td>ab 150 € / 170 € / 200 €</td></tr>
      <tr><td>Balayage kurz / mittel / lang</td><td>ab 150 € / 180 € / 230 €</td></tr>
      <tr><td>Hochsteckfrisur / Brautfrisur / Braut Make-up</td><td>ab 70 € / 150 € / 150 €</td></tr>
      <tr><td>Augenbrauen formen & zupfen / Gesicht zupfen</td><td>ab 12 € / 30 €</td></tr>
    </table>
  </div>
</section>

<div id="cocktailshot" class="dark">
  <div class="wrap">
    <div>
      <h2>Cocktailshot Spezial</h2>
      <p>Ein luxuriöses Pflege-Ritual für glänzendes, kräftiges und geschmeidiges Haar.</p>
      <ul>
        <li>Express Repairing Ritual – ab 49 €</li>
        <li>Intensive Repairing Ritual – ab 80 €</li>
        <li>Luxury Repairing Ritual – ab 120 €</li>
      </ul>
      <a class="btn" href="tel:+4917661072119">Termin vereinbaren</a>
    </div>
    <img src="cocktailshot.jpeg" alt="Cocktailshot für die Haare">
  </div>
</div>

<section id="extensions">
  <div class="title">
    <h2>Haarverlängerung</h2>
    <p>Mehr Länge, mehr Volumen, mehr du – mit individueller Beratung.</p>
  </div>
  <div class="grid">
    <div class="card"><div><h3>Haarlängen</h3><p>45 cm ab 3,00 €<br>50 cm ab 3,50 €<br>60 cm ab 4,00 €<br>70 cm ab 4,50 €</p></div></div>
    <div class="card"><div><h3>Methoden</h3><p>Tape-In ab 4,50 € pro Tape<br>Bonding ab 2,00 € pro Strähne<br>Micro Bonding ab 1,50 € pro Strähne<br>Mikrorings ab 2,00 € pro Strähne</p></div></div>
    <div class="card"><div><h3>Qualität</h3><p>Natürliches Ergebnis, schonende Einarbeitung und Beratung zur passenden Farbe und Methode.</p></div></div>
  </div>
</section>

<section id="galerie">
  <div class="title">
    <h2>Galerie</h2>
    <p>Klicke auf ein Bild, um es groß zu öffnen.</p>
  </div>
  <div class="gallery">
    <a href="hero-flyer.jpeg" target="_blank"><img src="hero-flyer.jpeg"></a>
    <a href="preise-flyer.jpeg" target="_blank"><img src="preise-flyer.jpeg"></a>
    <a href="cocktailshot.jpeg" target="_blank"><img src="cocktailshot.jpeg"></a>
    <a href="haarverlaengerung.jpeg" target="_blank"><img src="haarverlaengerung.jpeg"></a>
    <a href="kontakt-qr.jpeg" target="_blank"><img src="kontakt-qr.jpeg"></a>
  </div>
</section>

<section id="links">
  <div class="title">
    <h2>Folge mir & bewerte mich</h2>
    <p>Direkt anklickbar für Instagram, TikTok, WhatsApp und Google Maps.</p>
  </div>
  <div class="social">
    <a target="_blank" href="https://www.instagram.com/mirelas_hairstyle_extensions">Instagram öffnen</a>
    <a target="_blank" href="https://www.tiktok.com/@mirelas_hairstyle">TikTok öffnen</a>
    <a target="_blank" href="https://wa.me/4917661072119?text=Hallo%20Mirela%2C%20ich%20m%C3%B6chte%20einen%20Termin%20vereinbaren.">WhatsApp schreiben</a>
    <a target="_blank" href="https://www.google.com/maps/search/?api=1&query=Marlenstra%C3%9Fe%207%2C%2077656%20Offenburg">Route öffnen</a>
  </div>
</section>

<section>
  <div class="title">
    <h2>Standort</h2>
    <p>Marlenstraße 7, 77656 Offenburg</p>
  </div>
  <iframe loading="lazy" src="https://www.google.com/maps?q=Marlenstra%C3%9Fe%207%2C%2077656%20Offenburg&output=embed"></iframe>
</section>

<section id="kontakt" class="contact">
  <div class="wrap">
    <div>
      <h3>Mirela's Hairstyle</h3>
      <p>Schönheit ist unsere Leidenschaft.</p>
      <a class="btn" href="tel:+4917661072119">Jetzt anrufen</a>
    </div>
    <div>
      <h3>Kontakt</h3>
      <p>Telefon: <a href="tel:+4917661072119">01766 1072119</a><br>
      Adresse: <a target="_blank" href="https://www.google.com/maps/search/?api=1&query=Marlenstra%C3%9Fe%207%2C%2077656%20Offenburg">Marlenstraße 7, 77656 Offenburg</a></p>
    </div>
    <div>
      <h3>Öffnungszeiten</h3>
      <p>Di – Fr: 09:00 – 18:00 Uhr<br>Sa: 08:00 – 14:00 Uhr<br>Termine nach Vereinbarung</p>
    </div>
  </div>
</section>

<div class="footer">© Mirela's Hairstyle · Damenfriseur Offenburg</div>

</body>
</html>
"""

(base/"index.html").write_text(html, encoding="utf-8")

zip_path = Path("/mnt/data/mirelas_premium_website.zip")
if zip_path.exists():
    zip_path.unlink()
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for f in base.iterdir():
        z.write(f, arcname=f.name)

print(zip_path)
print(base/"index.html")
