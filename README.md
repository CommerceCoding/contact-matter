# Contact Matter

## Wichtig

Diese Erweiterung wurde auf Basis der modified eCommerce Shopsoftware (Version 1.06 rev 4356) entwickelt. Alle Dateien dieser Erweiterung ergänzen vorhandene Dateien des Shopsystems.  Die Dateien sollten nicht einfach über bestehende kopiert werden, sondern sollen als Anhaltspunkt für die richtigen Stellen der Einfügen dienen. Ein Backup des Shops vorher ist empfehlenswert. Es wird keine Haftung übernommen.

## Sprachdateien

### lang/english/lang_english.conf

An den Block *[contact_us]* folgendes anfügen:

```
# Contact Matter - Commerce Coding - BEGIN
text_contact_matter = 'Contact Matter:'
# Contact Matter - Commerce Coding - END
```

### lang/english/contact_us.php

An die Datei alle gewünschten Gründe, z.B. folgendes, anfügen:

```php
// Contact Matter - Commerce Coding - BEGIN
define('PRODUCT_REQUEST', 'Product Request');
define('SHIPPING_STATUS', 'Shipping Status');
// Contact Matter - Commerce Coding - END
```

### lang/german/lang_german.conf

An den Block *[contact_us]* folgendes anfügen:

```
# Contact Matter - Commerce Coding - BEGIN
text_contact_matter = 'Art der Anfrage:'
# Contact Matter - Commerce Coding - END
```

### lang/german/contact_us.php

An die Datei alle gewünschten Gründe, z.B. folgendes, anfügen:

```php
// Contact Matter - Commerce Coding - BEGIN
define('PRODUCT_REQUEST', 'Produktnachfrage');
define('SHIPPING_STATUS', 'Lieferstatus');
// Contact Matter - Commerce Coding - END
```

## Formularvorbereitung und -verarbeitung

### includes/contact_us.php

In der oberen Hälfte der Datei an der gewünschten Stelle folgendes einfügen ein, um die Eingabe des Formulars zu verarbeiten:

```php
$_POST['contact_matter']
```

Dies kann beispielsweise im Funktionsaufruf von *xtc_php_mail* geschehen, um die Betreffzeile entsprechend zu erweitern.

Kurz vor Ende der Datei folgendes einfügen, um das Drop-Down-Menü für die Ausgabe vorzubereiten:

```php
// Contact Matter - Commerce Coding - BEGIN
require_once DIR_WS_LANGUAGES . $_SESSION['language'] . '/contact_us.php';
$reasonArray = array();
$reasonArray[] = array('id' => PRODUCT_REQUEST, 'text' => PRODUCT_REQUEST);
$reasonArray[] = array('id' => SHIPPING_STATUS, 'text' => SHIPPING_STATUS);
$smarty->assign('INPUT_CONTACT_MATTER', xtc_draw_pull_down_menu('contact_matter', $reasonArray));
// Contact Matter - Commerce Coding - END
```

## Kontaktformular

### templates/xtc5/module/contact_us.html

Die Datei *contact_us.html* beinhaltet das Template für das Kontaktformular. In dieser Datei des verwendeten Templates an gewünschter Stelle folgendes einfügen:

```html
<!-- Contact Matter - Commerce Coding - BEGIN -->
<tr>
  <td>{#text_contact_matter#}*</td>
  <td width="59%">{$INPUT_CONTACT_MATTER}</td>
</tr>
<!-- Contact Matter - Commerce Coding - END -->
```

## Credits
Copyright: © 2013, Commerce Coding, http://www.commerce-coding.de  
Lizenz: http://opensource.org/licenses/GPL-2.0  GNU General Public License, version 2 (GPL-2.0)