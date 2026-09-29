# توثيق Easy CSS

Easy CSS مكتبة كلاسات مساعدة مبنية بـ SCSS لتنسيق واجهات الويب. تجمع أدوات للمسافات، والتخطيط، والأبعاد، والنصوص، والألوان، والحدود، والمؤثرات البسيطة. وهي مناسبة لمشاريع Nuxt وغيرها من المشاريع التي تستخدم CSS أو SCSS.

> أسماء الكلاسات والقيم الواردة هنا مأخوذة من ملفات SCSS الحالية. كل كلاس يضيف خاصية CSS مع `!important`؛ لذلك قد يتغلب على قواعد التطبيق العادية.

## المحتويات

- [التثبيت والاستخدام مع Nuxt](#التثبيت-والاستخدام-مع-nuxt)
- [تخصيص رموز التصميم](#تخصيص-رموز-التصميم)
- [طريقة تسمية الكلاسات](#طريقة-تسمية-الكلاسات)
- [المسافات](#المسافات)
- [Flexbox](#flexbox)
- [Grid](#grid)
- [العرض والارتفاع](#العرض-والارتفاع)
- [النصوص والألوان](#النصوص-والألوان)
- [الحدود](#الحدود)
- [الأدوات المساعدة](#الأدوات-المساعدة)
- [الكلاسات المتجاوبة](#الكلاسات-المتجاوبة)
- [البناء وبنية المشروع](#البناء-وبنية-المشروع)

## التثبيت والاستخدام مع Nuxt

ثبّت الحزمة في مشروع Nuxt:

```bash
npm install easy-css
npm install -D sass
```

أضف مدخل SCSS في `nuxt.config.ts`:

```ts
export default defineNuxtConfig({
  css: ['easy-css/src/index.scss'],
})
```

بعد ذلك استخدم الكلاسات داخل صفحات ومكونات Vue:

```vue
<template>
  <main class="max-w-900 mx-auto p-20">
    <section class="grid grid-cols-3 gap-16 sm__grid-cols-1">
      <article class="border border-gray-200 rounded-12 bg-white p-16 shadow-sm">
        <h2 class="text-24 font-bold text-primary">بطاقة</h2>
        <p class="mt-10 text-16 text-gray-600">محتوى البطاقة</p>
      </article>
    </section>
  </main>
</template>
```

يحتوي ملف `src/index.scss` على جميع أجزاء المكتبة؛ أضفه مرة واحدة إلى CSS العام للمشروع.

### استخدام ملف CSS المبني

إذا لم تكن بحاجة إلى تعديل قيم SCSS، يمكنك استخدام ملف CSS الجاهز بدلًا من ترجمة المصدر:

```ts
export default defineNuxtConfig({
  css: ['easy-css/dist/easy-css.css'],
})
```

عند اختيار ملف CSS الجاهز لا تستورد مدخل SCSS معه كي لا تُحمّل القواعد مرتين.

## تخصيص رموز التصميم

تقبل الخرائط في `src/variables.scss` التخصيص بواسطة Sass `@use ... with (...)`. أنشئ ملفًا محليًا، مثل `assets/scss/easy-css.scss`، وعرّف القيم قبل استيراد المدخل الشامل:

```scss
@use 'easy-css/src/variables' with (
  $colors: (
    'transparent': transparent,
    'current': currentColor,
    'white': #fff,
    'black': #000,
    'primary': #6750a4
  )
);

@use 'easy-css/src/index';
```

أضف ملف التهيئة المحلي إلى Nuxt بدل الاستيراد المباشر:

```ts
export default defineNuxtConfig({
  css: ['~/assets/scss/easy-css.scss'],
})
```

الخريطة التي تمررها تستبدل الخريطة الافتراضية كاملة. لذلك سيولّد تخصيص `$colors` أعلاه كلاسات الألوان للمفاتيح الخمسة فقط؛ أضف إلى الخريطة كل الألوان التي تريد الاحتفاظ بكلاساتها. وينطبق مبدأ الاستبدال على خرائط الرموز الأخرى أيضًا.

الخرائط القابلة للتهيئة هي:

- `$breakpoints`: أسماء وقيم نقاط التوقف.
- `$spacing`: قيم المسافات، وتُستخدم أيضًا في الفجوات وإزاحات الموضع.
- `$sizes`: قيم العرض والارتفاع.
- `$colors`: ألوان النص والخلفية والحدود ومتغيرات CSS.
- `$font-sizes` و`$font-weights`: أحجام الخطوط وأوزانها.
- `$border-radius`: أنصاف أقطار الزوايا.
- `$shadows`: قيم الظلال.
- `$z-index`: طبقات الترتيب.
- `$opacity`: قيم الشفافية.

## طريقة تسمية الكلاسات

تستخدم الكلاسات نمطًا وصفيًا يتبعه رقم أو اتجاه أو قيمة. مثلًا `p-20` تعني حشوة داخلية بقيمة 20px، و`grid-cols-3` تعني ثلاثة أعمدة متساوية. الوحدات والقيم الدقيقة تأتي من خرائط الرموز الموضحة أدناه.

## المسافات

يوفر `spacing.scss` كلاسات `margin` و`padding` للجهات الأربع أو جهة محددة أو محور كامل:

| النمط | الخاصية |
|---|---|
| `m-{n}`, `p-{n}` | الجهات الأربع |
| `mt-{n}`, `pt-{n}` | الأعلى |
| `mb-{n}`, `pb-{n}` | الأسفل |
| `ml-{n}`, `pl-{n}` | اليسار |
| `mr-{n}`, `pr-{n}` | اليمين |
| `mx-{n}`, `px-{n}` | اليمين واليسار |
| `my-{n}`, `py-{n}` | الأعلى والأسفل |

القيم الافتراضية لـ `{n}` هي: `0`, `5`, `10`, `12`, `15`, `16`, `20`, `24`, `25`, `30`, `35`, `40`, `45`, `50`, `55`, `60`, `65`, `70`, `75`, `80`, `85`, `90`, `95`, `100`, `110`, `120`, `130`, `140`, `150`, و`auto`. قيمة `auto` صالحة لهوامش `m-*` فقط؛ الحشوات والفجوات وإزاحات الموضع التي تُولد من `$spacing` تتبع القيمة نفسها، لكن استخدام `auto` معها ليس مناسبًا لكل خاصية CSS.

للهوامش التلقائية توجد كذلك `m-auto`, `mx-auto`, `my-auto`, `mt-auto`, `mb-auto`, `ml-auto`, `mr-auto`.

```html
<div class="mx-auto max-w-600 p-20">
  <p class="mb-10">مسافة أسفل الفقرة</p>
</div>
```

## Flexbox

### الحاوية والاتجاه والالتفاف

- العرض: `flex`, `inline-flex`.
- الاتجاه: `flex-row`, `flex-col`, `flex-row-reverse`, `flex-col-reverse`.
- الالتفاف: `flex-wrap`, `flex-nowrap`, `flex-wrap-reverse`.

### المحاذاة

- `justify-start`, `justify-end`, `justify-center`, `justify-between`, `justify-around`, `justify-evenly` لضبط `justify-content`.
- `items-start`, `items-end`, `items-center`, `items-baseline`, `items-stretch` لضبط `align-items`.
- `content-start`, `content-end`, `content-center`, `content-between`, `content-around`, `content-stretch` لضبط `align-content`.

### العناصر والفجوات

- `flex-1`, `flex-2`, `flex-3`, `flex-auto`, `flex-none` لضبط قيمة `flex`.
- `flex-shrink-0`, `flex-shrink-1` لضبط `flex-shrink`.
- `gap-{n}` للفجوة؛ يستخدم القيم نفسها في `$spacing`.

```html
<div class="flex items-center justify-between gap-10">
  <span>العنوان</span>
  <button class="flex-shrink-0">فتح</button>
</div>
```

## Grid

- `grid` ينشئ حاوية Grid.
- `grid-cols-1` إلى `grid-cols-6` و`grid-cols-12` تنشئ أعمدة متساوية؛ يتوفر أيضًا `grid-cols-none`.
- `grid-cols-auto-100`, `grid-cols-auto-150`, `grid-cols-auto-200`, `grid-cols-auto-250`, `grid-cols-auto-300` تنشئ أعمدة تلقائية باستخدام `auto-fit` وحد أدنى بالبيكسل.
- `grid-rows-1` إلى `grid-rows-4` تنشئ صفوفًا متساوية.
- `col-span-1` إلى `col-span-12` تحدد امتداد العنصر على الأعمدة؛ `col-span-full` يمتد على كامل الشبكة.
- `row-span-1` إلى `row-span-4` تحدد امتداد العنصر على الصفوف.
- `gap-{n}` يضبط الفجوة باستخدام قيم `$spacing`.
- `justify-items-start/end/center/stretch` لضبط العناصر أفقيًا داخل خلايا الشبكة.
- `align-items-start/end/center/stretch` لضبط العناصر عموديًا.

```html
<section class="grid grid-cols-3 gap-20">
  <article class="col-span-2">المحتوى الرئيسي</article>
  <aside>الشريط الجانبي</aside>
</section>
```

## العرض والارتفاع

تُستخدم مفاتيح `$sizes` مع البادئات التالية:

- `w-{n}` و`h-{n}`: العرض والارتفاع.
- `min-w-{n}` و`max-w-{n}`: الحد الأدنى والأقصى للعرض.
- `min-h-{n}` و`max-h-{n}`: الحد الأدنى والأقصى للارتفاع.
- `size-{n}`: يضبط العرض والارتفاع بالقيمة نفسها.

القيم الافتراضية: `0`, `25`, `30`, `35`, `40`, `45`, `50`, `70`, `100`, `120`, `150`, `200`, `250`, `300`, `400`, `500`, `600`, `700`, `800`, `900`, `1000` (كلها px)، إضافة إلى `auto`, `full` (100%), `screen` (`var(--app-viewport-height, 100svh)`), و`fit` (`fit-content`).

```html
<img class="size-50 rounded-full" src="avatar.png" alt="الصورة الشخصية">
<div class="w-full max-w-600">حاوية بعرض لا يتجاوز 600px</div>
```

## النصوص والألوان

### تنسيق النص

- `text-{n}` لأحجام الخطوط: `10`, `12`, `13`, `14`, `15`, `16`, `18`, `20`, `22`, `24`, `26`, `28`, `30`, `32`, `34`, `36`, `38`, `40`, `42`, `44`, `48`, `52`, `56`, `64`, `72`, `80` px.
- `font-{weight}` للأوزان `100` إلى `900` بمئاتها، إضافة إلى `font-normal` و`font-bold`.
- المحاذاة: `text-left`, `text-center`, `text-right`, `text-start`, `text-end`.
- حالة الأحرف: `uppercase`, `lowercase`, `capitalize`, `normal-case`.
- الزخرفة: `underline`, `no-underline`, `line-through`.
- الالتفاف والقص: `text-wrap`, `text-nowrap`, `truncate`.
- `line-clamp-1` إلى `line-clamp-4` لإخفاء النص بعد عدد الأسطر المحدد.

### ألوان النص والخلفية

ألوان `$colors` الافتراضية: `transparent`, `current`, `white`, `black`, `primary`, `secondary`, `success`, `danger`, `warning`, `info`, `dark`, `light`, `gray`, و`gray-100` إلى `gray-900`.

- `text-{color}` يضبط لون النص.
- `bg-{color}` يضبط لون الخلفية.
- `bg-white` و`bg-transparent` متاحان أيضًا ككلاسين ثابتين.

```html
<h1 class="text-32 font-bold text-primary text-center">عنوان الصفحة</h1>
<p class="text-gray-600 line-clamp-2">وصف طويل يمكن قصه بعد سطرين.</p>
```

## الحدود

- `rounded-{n}` يضبط نصف قطر الزوايا. القيم: `0`, `2`, `4`, `6`, `8`, `10`, `12`, `16`, `20`, `24`, `30`, `50` (50%)، و`full` (9999px).
- `rounded-t`, `rounded-r`, `rounded-b`, `rounded-l` تجعل زوايا الجهة المحددة ترث نصف قطر العنصر الأب.
- `border`, `border-2`, `border-3`, `border-0` تضبط سماكة أو إزالة الحد. اللون الافتراضي للحدود هو `#e5e7eb`.
- `border-t/r/b/l` تنشئ حدًا بسمك 1px للجهة المحددة؛ وتتوافر نظائر `border-t/r/b/l-2` و`border-t/r/b/l-0`.
- `border-{color}` يغيّر لون الحد؛ و`border-t/r/b/l-{color}` يغيّر لون جهة محددة. هذه الكلاسات تغيّر اللون فقط؛ استخدم معها كلاسًا ينشئ الحد مثل `border`.
- الأنماط: `border-solid`, `border-dashed`, `border-dotted`, `border-none`.

```html
<div class="border border-gray-200 rounded-12 p-16">بطاقة بحد خفيف</div>
```

## الأدوات المساعدة

### العرض والتموضع

- العرض: `block`, `inline-block`, `inline`, `hidden`.
- التموضع: `static`, `relative`, `absolute`, `fixed`, `sticky`.
- الإزاحات `top-{n}`, `right-{n}`, `bottom-{n}`, `left-{n}` تستخدم قيم `$spacing`. تتوفر أيضًا `top/right/bottom/left-auto` و`top/right/bottom/left-full`.
- `inset-0`, `inset-x-0`, `inset-y-0` تضبط الإزاحة على جهات متعددة.
- `sticky-top`, `sticky-bottom` يضبطان التموضع اللاصق والحافة والخلفية البيضاء و`z-index: 10`.

### الطبقات والمظهر

- `z-{key}` يستخدم مفاتيح `$z-index`: `0`, `10`, `20`, `30`, `40`, `50`, `dropdown`, `overlay-backdrop`, `overlay-panel`, `auto`.
- `opacity-{n}` يستخدم `0`, `25`, `50`, `75`, `100`.
- `shadow-{key}` يستخدم `none`, `sm`, `md`, `lg`, `xl`, `xxl`.
- `visible`, `invisible` لضبط الظهور.
- `bg-overlay-scrim` لخلفية سوداء بشفافية 35%؛ `backdrop-blur-sm` و`backdrop-blur-md` لتمويه الخلفية.
- `active-primary` يبرز النص بخاصية `--primary-color` ويضيف حدًا سفليًا.

### التفاعل والفيض والتحويل

- الفيض: `overflow-auto`, `overflow-hidden`, `overflow-visible`, `overflow-scroll`, `overflow-x-auto`, `overflow-y-auto`, `overflow-x-hidden`, `overflow-y-hidden`.
- المؤشر: `cursor-pointer`, `cursor-default`, `cursor-wait`, `cursor-move`, `cursor-not-allowed`.
- تفاعل المؤشر: `pointer-events-none`, `pointer-events-auto`.
- تحديد النص: `select-none`, `select-text`, `select-all`, `select-auto`.
- `super` لمحاذاة النص عموديًا كعلامة مرتفعة وتصغير خطه.
- الانتقالات: `transition-opacity-500` و`transition-colors`.
- التحويم: `hover-opacity`, `hover-cursor-pointer`, `hover-red`, `hover-outline`.
- `disabled` يخفض الشفافية ويعطل أحداث المؤشر.
- الدوران: `rotate-0`, `rotate-45`, `rotate-90`, `rotate-180`, `rotate-270`.
- التكبير والتصغير: `scale-90`, `scale-95`, `scale-100`, `scale-105`, `scale-110`.

## الكلاسات المتجاوبة

أضف بادئة نقطة التوقف ثم شرطتين سفليتين ثم اسم الكلاس، مثل `md__flex-col`. نقاط التوقف الافتراضية هي:

| البادئة | الحد الأقصى للعرض |
|---|---:|
| `sm__` | 640px |
| `md__` | 768px |
| `lg__` | 1024px |
| `xl__` | 1280px |
| `xxl__` | 1536px |

كل قاعدة متجاوبة داخل `@media (max-width: ...)`، لذلك تعمل عند عرض الشاشة المساوي للحد أو الأقل. نقاط التوقف نطاقات متداخلة؛ إذا وضعت على العنصر كلاسين متجاوبين يغيران الخاصية نفسها، فقد تنطبق القاعدتان معًا وتفوز القاعدة الأحدث في ترتيب CSS.

ليست كل الكلاسات لها نسخة متجاوبة. المتاح بحسب المصدر:

- المسافات: جميع قيم المسافات العادية، إضافة إلى `m-auto`, `mx-auto`, `ml-auto`, `mr-auto`؛ لا توجد نسخ متجاوبة لـ `my-auto`, `mt-auto`، أو `mb-auto`.
- Flexbox: مجموعة جزئية تشمل العرض والاتجاه والالتفاف والمحاذاة و`flex-1` والفجوات.
- Grid: العرض، أعمدة 1–4، امتدادات أعمدة محددة (`2`, `3`, `full`) والفجوات.
- الأبعاد: `w-*`, `h-*`, `min-w-*`, `max-w-*`, `size-*`؛ لا توجد نسخ متجاوبة لـ `min-h-*` أو`max-h-*`.
- النصوص: أحجام الخطوط والأوزان ومحاذاة left/center/right.
- الحدود: أنصاف الأقطار، `border` و`border-2` و`border-0`، حدود الجهات بسمك 1، وألوان `border-{color}`.
- المساعدات: `hidden`, `block`, `flex`, `grid`, `relative`, `absolute`, `sticky-top`.

```html
<div class="grid grid-cols-3 gap-16 sm__grid-cols-1">
  <!-- يصبح التخطيط عمودًا واحدًا عند العرض 640px أو أقل -->
</div>
```

## متغيرات CSS

يصدر `utilities.scss` على `:root` متغيرًا لكل لون في `$colors` بصيغة `--color-{name}`، كما يصدر `--primary-color: var(--color-primary)`. يمكن استخدام هذه المتغيرات في CSS الخاص بالتطبيق. بعض القيم الافتراضية للألوان الرمادية تعتمد على متغيرات يوفرها التطبيق: `--theme-text-secondary`, `--theme-border`, `--theme-surface`, `--theme-page-bg`.

## البناء وبنية المشروع

لتجميع SCSS بعد تثبيت اعتماديات التطوير:

```bash
npm install
npm run build
```

ينشئ الأمر `dist/easy-css.css` من `src/index.scss` بتنسيق مضغوط. وللبناء التلقائي عند تعديل المصدر:

```bash
npm run watch
```

| الملف | المسؤولية |
|---|---|
| `src/index.scss` | يجمع جميع أجزاء المكتبة |
| `src/variables.scss` | خرائط القيم الافتراضية القابلة للتهيئة |
| `src/spacing.scss` | الهوامش والحشوات |
| `src/flex.scss` | كلاسات Flexbox |
| `src/grid.scss` | كلاسات Grid |
| `src/width-height.scss` | العرض والارتفاع |
| `src/typography.scss` | النصوص |
| `src/border.scss` | الحدود وأنصاف الأقطار |
| `src/utilities.scss` | الألوان والموضع والمظهر والتفاعل وغيرها |
| `dist/easy-css.css` | ملف CSS الجاهز للاستخدام |

عند تحديث الكلاسات أو قيم الرموز، حدّث هذا الدليل وREADME بما يطابق المصدر، ثم أعد بناء ملف CSS.

## الترخيص

MIT
