# Hello, world!

ٹیوٹوریل کا یہ حصہ  Javascript کی بنیاد ہے۔ Javascript زبان کا سبق ہے یہ۔

لیکن ہمیں اپنی سکرپٹس چلانے کیلیے کسی انوائرنمنٹ کی ضرورت ہے۔ چونکہ یہ کتاب آن لائن ہے تو براؤزر ہی ایک اچھا انتخاب ہے۔ ہم براؤزر کے متعلق کمانڈز (جیسے کہ `alert` ہے) کو کم سے کم استعمال کریں گے تاکہ اگر آپ کسی دوسرے انوائرنمنٹ جیسے (Node JS ہے) پر کام کرنا چاہیں تو آپ کو بہت زیادہ مشکل نہ ہو۔ ہم [اگلے حصے](/ui) میں Javascript کو براؤزر میں استعمال کرنے پر غور کریں گے۔

تو پہلے دیکھتے ہیں کہ ایک سکرپٹ کو ایک ویب پیج کے ساتھ کیسے جوڑا جاتا ہے۔ server-side انوائرنمنٹ (جیسے Node ہے) پر سکرپٹ چلانے کیلیے ایک کمانڈ جیسے `"node my.js"` ہے کو چلایا جائے گا۔

## The "script" tag

جاواسکرپٹ (Javascript) پروگرامز کو HTML ڈاکیومنٹ میں کہیں بھی `<script>` tag شاھل کیا جا سکتا ہے۔

مثال کے طور پر:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>سکرپٹ سے پہلے۔۔۔</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>سکرپٹ کے بعد۔۔۔</p>

</body>

</html>
```

```online
آپ مثال کو چلانے کیلیے ڈبے کے سب سے اوپر دائیں کونے میں "Play" کے بٹن کو دبا سکتے ہیں۔
```

`<script>` tag میں موجود Javascript کوڈ براؤزر کے tag کو پروسیس کرنے پر خود بخود چل جاتا ہے۔

## Modern markup

`<script>` tag کے کچھ attributes ہیں جو آج کل مشکل ہی استعمال کیجیے جاتے ہیں لیکن پرانے کوڈ میں ابھی بھی موجود ہیں:

`type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>

: پرانے HTML standard, HTML4 میں سکرپٹ tag کے اوپر `type` attribute کا ہونا لازمی تھا۔ عام طور پر یہ `type="text/javascript"` ہوتا تھا۔ اب یہ لازم نہیں ہے۔ جدید HTML standard نے اسکا مطلب بھی بدل دیا ہے۔ اب یہ Javascript موڈیولز کیلیے استعمال ہو سکتا ہے۔ لیکن وہ ایک اعلی درجے کا موضوع ہے۔ ہم اس کے بارے ٹیوٹوریل کے موڈیولز کے حصے میں بات کریں گے۔

`language` attribute: <code>&lt;script <u>language</u>=...&gt;</code>
: یہ attribute سکرپٹ کی زبان دکھانے کیلیے استعمال ہوتا تھا۔ اب یہ attribute کسی کام کا نہیں کیونکہ Javascript ڈیفالٹ زبان ہے۔ اسے استعمال کرنے کی کوئی ضرورت نہیں۔

سکرپٹس کے پہلے اور بعد میں کمنٹس۔
: پرانی کتابوں اور گائیڈز میں آپ کو `<script>` tags میں اس طرح کمنٹ ملتے ہوں گے:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```
    یہ طریقہ جدید Javascript میں استعمال نہیں کیا جاتا۔ یہ کمنٹس Javascript کوڈ کو پرابے براؤزرز جنہیں یہ معلوم نہیں کہ `<script>` tag کو کس طرح پروسیس کرنا ہے سے چھپا دیتے ہیں۔ چونکہ پچھلے 15 سالوں میں جو براؤزرز ریلیز کیے جا رہے ہیں ان میں یہ مسؑلہ نہیں اس کمنٹ سے آپ کے ایک بہت پرانے کوڈ کی شناخت کرنے میں مدد ملے گی۔


## External scripts

اگر ہمارے پاس بہت زیادہ جاواسکرپٹ کوڈ ہو تو ہم اسے علیحدہ فائل میں شامل کر سکتے ہیں۔

سکرپٹ فائلز کو HTML کے ساتھ `src` attribute سے جوڑا جاتا ہے۔

```html
<script src="/path/to/script.js"></script>
```

یہاں `/path/to/script.js` سکرپٹ کا سائٹ کے روٹ سے ایبسولیوٹ پاتھ ہے۔ ہم موجودہ پیج سے ریلیٹِو پاتھ بھی مہیا کر سکتے ہیں۔ مثال کے طور پر،  `src="script.js"`، اسی طرح `src="./script.js"` کا مطلب بھی یہ ہی ہے کہ موجودہ فولڈر میں موجود `"script.js"` نام کی فائل۔

ہم ایک مکمل URL بھی دے سکتے ہیں۔ مثال کے طور پر:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

کئی سکرپٹس شامل کرنے کیلیے ایک سے زیادہ tags استعمال کیے جاتے ہیں:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
اصول کے مطابق، صرف سادہ ترین سکرپٹس ہی HTML میں لکھی جاتی ہے۔ زیادہ پیچیدہ سکرپٹس کو علیحدہ فائلز میں رکھا جاتا ہے۔

علیحدہ فائل کا فائدہ یہ ہے کہ براؤزر اسے ڈاؤن لوڈ کرنے کے بعد اپنے [cache](https://en.wikipedia.org/wiki/Web_cache) میں محفوظ کر لے گا۔

دوسرے پیجز جو اسی سکرپٹ کو حوالہ استعمال کریں گے وہ اسے ڈاؤن لوڈ کرنے کی جگہ کیش سے اٹھائیں گے۔ اس طرح فائل صرف ایک دفعہ ہی ڈاؤن لوڈ ہوتی ہے اور اسی فائل کا استعمال بار بار ہوتا ہے۔

اس سے ٹریفک کم ہوتی ہے اور پیج تیز ہو جاتا ہے۔
```

````warn header="If `src` is set, the script content is ignored."
ایک اکیلا `<script>` tag اپنے اندر کوڈ اور `src` attribute دونوں نہیں رکھ سکتا۔

یہ کوڈ کام نہیں کرے گا:

```html
<script *!*src*/!*="file.js">
  alert(1); // کنٹینٹ اگنور کر دیا جاتا ہے، کیونکہ سورس موجود ہے۔
</script>
```

ہمیں بیرونی `<script src"...">` یا اندرونی `<script>` سکرپٹ میں سے کوئی ایک لازمی چننا ہوتی ہے۔

مندرجہ بالا مثال کو دو سکرپٹس میں تقسیم کر کے استعمال کیا جا سکتا ہے:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Summary
- ہم `<script>` tag استعمال کرکے Javascript کوڈ کو پیج میں شامل کر سکتے ہیں۔
- `type` اور `language` attributes لازم نہیں۔
- بیرونی سکرپٹ کو `<script src="path/to/script.js"></script>` کی مدد سے شامل کیا جا سکتا ہے۔

براؤزر سکرپٹس کے بارے اور ان کی ویب پیج کے ساتھ interaction کے بارے بہت کچھ سیکھنے کو ہے۔ لیکن ذہن نشین رکھیے کہ ٹیوٹوریل کا یہ حصہ Javascript زبان کیلیے مخصوص ہے۔

There is much more to learn about browser scripts and their interaction with the webpage. But let's keep in mind that this part of the tutorial is devoted to the JavaScript language, so we shouldn't distract ourselves with browser-specific implementations of it. We'll be using the browser as a way to run JavaScript, which is very convenient for online reading, but only one of many.
