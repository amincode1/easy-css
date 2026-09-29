# Easy CSS

مكتبة كلاسات CSS مساعدة مبنية بـ SCSS، تتضمن أدوات للمسافات والتخطيط والأبعاد والنصوص والألوان والحدود، مع كلاسات متجاوبة.

للدليل التفصيلي وقائمة الكلاسات والقيم المدعومة، راجع [DOCUMENTATION.md](./DOCUMENTATION.md).

## التثبيت

```bash
npm install easy-css
```

## الاستخدام في Nuxt

أضف مدخل SCSS إلى `css` في `nuxt.config.ts`:

```ts
export default defineNuxtConfig({
  css: ['easy-css/src/index.scss'],
})
```

يتطلب ذلك أن يدعم مشروع Nuxt ترجمة SCSS؛ ثبّت `sass` في التطبيق إذا لم يكن موجودًا:

```bash
npm install -D sass
```

ثم استخدم الكلاسات في القوالب:

```html
<section class="grid grid-cols-3 gap-16 sm__grid-cols-1">
  <article class="p-20 rounded-12 bg-primary text-white">محتوى</article>
</section>
```

البادئة المتجاوبة `sm__` و`md__` وغيرها تطبق قواعدها حتى عرض نقطة التوقف المحددة (max-width). نقاط التوقف الافتراضية: `sm` 640px، `md` 768px، `lg` 1024px، `xl` 1280px، `xxl` 1536px.

## تخصيص قيم SCSS

أنشئ ملفًا محليًا مثل `assets/scss/easy-css.scss`، وهيّئ المتغيرات قبل استيراد المدخل الشامل:

```scss
@use 'easy-css/src/variables' with (
  $colors: (
    'transparent': transparent,
    'current': currentColor,
    'white': #fff,
    'black': #000,
    'primary': #6750a4,
    'secondary': #64748b,
    'success': #00b342,
    'danger': #df1c1c,
    'warning': #ad6d00,
    'info': #0ea5e9,
    'dark': #1e293b,
    'light': #f8fafc,
    'gray': #9ca3af,
    'gray-100': #f3f4f6,
    'gray-200': #e5e7eb,
    'gray-300': #d1d5db,
    'gray-400': #9ca3af,
    'gray-500': #6b7280,
    'gray-600': #4b5563,
    'gray-700': #374151,
    'gray-800': #1f2937,
    'gray-900': #111827
  )
);

@use 'easy-css/src/index';
```

بعدها أضف الملف المخصص إلى `css` بدلًا من استيراد المكتبة مباشرة:

```ts
export default defineNuxtConfig({
  css: ['~/assets/scss/easy-css.scss'],
})
```

المتغيرات التي يمكن تهيئتها تشمل نقاط التوقف والمسافات والأحجام والألوان وأحجام وأوزان الخطوط وأنصاف الأقطار والظلال وطبقات z-index والشفافية. عند تخصيص خريطة مثل `$colors` يجب تمرير الخريطة كاملة.

## استخدام CSS الجاهز

إذا لم ترغب بترجمة SCSS أو تخصيص القيم، استورد CSS المبني:

```ts
export default defineNuxtConfig({
  css: ['easy-css/dist/easy-css.css'],
})
```

## البناء من المصدر

```bash
npm install
npm run build
```

ينتج البناء `dist/easy-css.css`. ملفات SCSS المصدرية مضمنة في الحزمة المنشورة لدعم التخصيص.

## أمثلة الكلاسات

- المسافات: `m-10`, `p-20`, `mx-auto`, `sm__p-10`
- Flexbox: `flex`, `flex-col`, `items-center`, `justify-between`, `gap-10`
- Grid: `grid`, `grid-cols-3`, `col-span-2`, `sm__grid-cols-1`
- الأبعاد: `w-full`, `h-screen`, `max-w-600`, `size-50`
- النصوص والألوان: `text-16`, `font-bold`, `text-primary`, `text-center`
- الحدود: `border`, `border-gray-200`, `rounded-12`
- المساعدات: `hidden`, `relative`, `z-dropdown`, `shadow-md`, `cursor-pointer`

## الترخيص

MIT
