# Easy CSS 🚀

**Easy CSS** is a lightweight, SCSS-based utility-first CSS library designed for rapid UI development with a focus on simplicity and responsiveness.

**Easy CSS** هي مكتبة CSS مساعدة خفيفة الوزن تعتمد على SCSS، مصممة لتطوير واجهات المستخدم بسرعة مع التركيز على البساطة والاستجابة (Responsiveness).

---

## 🌟 Features / المميزات

- 🚀 **Lightweight & Fast**: Only include what you need.
- 📱 **Fully Responsive**: Easy-to-use responsive modifiers.
- 🎨 **Customizable**: Built with SCSS variables for easy branding.
- 🛠️ **Utility-First**: Similar to Tailwind but simpler and SCSS-based.
- 🇸🇦 **Arabic Support**: Arabic comments and documentation support.

---

## 🛠️ Installation / التثبيت

To use Easy CSS in your project, simply import the main SCSS file:

لاستخدام Easy CSS في مشروعك، ببساطة قم باستيراد ملف SCSS الرئيسي:

```scss
@import "path/to/easy-css/src/index.scss";
```

---

## 📖 Usage / طريقة الاستخدام

### 1. Spacing (Margin & Padding) / المسافات

Use `m-{size}` for margin and `p-{size}` for padding.

استخدم `m-{size}` للهوامش الخارجية و `p-{size}` للهوامش الداخلية.

- **Directions**: `t` (top), `b` (bottom), `l` (left), `r` (right), `x` (horizontal), `y` (vertical).
- **Example**: `.m-4`, `.pt-2`, `.mx-auto`, `.py-6`.

### 2. Flexbox / المرن

Easily create flexible layouts.

إنشاء تخطيطات مرنة بسهولة.

- **Classes**: `.flex`, `.flex-col`, `.justify-center`, `.items-center`, `.gap-4`.
- **Example**:

```html
<div class="flex justify-between items-center gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

### 3. Grid / الشبكة

Powerful grid system.

نظام شبكة قوي.

- **Classes**: `.grid`, `.grid-cols-3`, `.gap-4`, `.col-span-2`.
- **Example**:

```html
<div class="grid grid-cols-3 gap-4">
  <div class="col-span-2">Main Content</div>
  <div>Sidebar</div>
</div>
```

### 4. Typography / النصوص

Control text size, weight, and alignment.

التحكم في حجم النص، وزنه، ومحاذاته.

- **Classes**: `.text-16`, `.font-bold`, `.text-center`, `.uppercase`.
- **Example**: `<h1 class="text-32 font-bold text-primary">Hello World</h1>`

### 5. Borders / الحدود

Customize borders and border radius.

تخصيص الحدود ونصف قطر الحواف.

- **Classes**: `.border`, `.border-2`, `.rounded-8`, `.border-primary`.
- **Example**: `<div class="border border-gray-200 rounded-8 p-4">Content</div>`

### 6. Utilities / مساعدات متنوعة

Additional helper classes for common tasks.

كلاسات مساعدة إضافية للمهام الشائعة.

- **Classes**: `.shadow-md`, `.opacity-50`, `.cursor-pointer`, `.bg-light`.
- **Example**: `<button class="bg-primary text-white p-2 rounded-4 cursor-pointer shadow-sm">Click Me</button>`

---

## 📱 Responsiveness / الاستجابة

Easy CSS uses a simple prefix system for responsive design: `{breakpoint}__class`.

تستخدم Easy CSS نظام بادئة بسيط للتصميم المستجيب: `{breakpoint}__class`.

- **Breakpoints**: `sm`, `md`, `lg`, `xl`, `xxl`.
- **Example**: `.md__flex-row`, `.sm__text-14`, `.lg__p-10`.

> [!IMPORTANT]
> Note the double underscore `__` between the breakpoint and the class name.
> تنبيه: لاحظ استخدام الشرطة السفلية المزدوجة `__` بين نقطة التوقف واسم الكلاس.

---

## 🎨 Customization / التخصيص

You can customize the design tokens by modifying `src/variables.scss`.

يمكنك تخصيص رموز التصميم من خلال تعديل ملف `src/variables.scss`.

---

## 🏗️ Build / البناء

To compile the SCSS files into a single CSS file, you can use the `sass` compiler.

لتحويل ملفات SCSS إلى ملف CSS واحد، يمكنك استخدام مترجم `sass`.

### Using Sass CLI / استخدام Sass CLI

```bash
# Install sass if you haven't already
# npm install -g sass

# Compile the library
sass src/index.scss dist/easy-css.css --style compressed
```

### Using NPM Scripts / استخدام NPM Scripts

If you have a `package.json` file, you can add the following script:

إذا كان لديك ملف `package.json` يمكنك إضافة السكريبت التالي:

```json
"scripts": {
  "build": "sass src/index.scss dist/easy-css.css --style compressed",
  "watch": "sass src/index.scss dist/easy-css.css --watch"
}
```

---

## 📄 License / الترخيص

MIT License.
