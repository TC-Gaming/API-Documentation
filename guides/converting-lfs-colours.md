# Converting LFS Colours

Live for Speed text that includes colours is encoded. This guide will help you to extract the colours from the text.

Our code examples are available in JavaScript and PHP _(change language in the top right)._

{% method %}
## Reference Implementations

The list of LFS colour codes is as follows:

| Colour | Code |
| :--- | :--- |
| Black | `^0` |
| Red | `^1` |
| Light Green | `^2` |
| Yellow | `^3` |
| Blue | `^4` |
| Purple | `^5` |
| Light Blue | `^6` |
| White | `^7` |
| Dark Green (Default) | `^8` |
| Original text colour and codepage | `^9` |

All of the examples in this guide require the following CSS to properly display the colours:

### CSS

```css
.lfs_col0 {color : #000000;}
.lfs_col1 {color : #ff0000;}
.lfs_col2 {color : #00ff00;}
.lfs_col3 {color : #ffff00;}
.lfs_col4 {color : #0000ff;}
.lfs_col5 {color : #ff00ff;}
.lfs_col6 {color : #00ffff;}
.lfs_col7 {color : #ffffff;}
.lfs_col8 {color : #8a8a8a;}
```

{% sample lang="js" %}

### JavaScript

{% sample lang="php" %}

### PHP

```php
function LFSColours($raw) {
  if ($raw === null) return "";
  $parts = preg_split('/(?=\^\d)/', $raw);
  $res = "";
  foreach ($parts as $part) {
    if (preg_match('/(\^\d)(.*)/', $part, $m) === 1) {
      $res .= "<span class='lfs_col" . $m[1][1] . "'>" . htmlspecialchars($m[2]) . "</span>";
    }
    else $res .= "<span class='lfs_col8'>" . htmlspecialchars($part) . "</span>";
  }
  return $res;
}```

{% endmethod %}