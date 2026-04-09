# Detailed Examples / أمثلة تفصيلية 📚

This document provides detailed examples of how to use **Easy CSS** to build common UI components.

يوفر هذا المستند أمثلة مفصلة حول كيفية استخدام **Easy CSS** لبناء مكونات واجهة المستخدم الشائعة.

---

## 1. Profile Card / بطاقة شخصية 👤

A simple card component with an image, title, description, and a button.

مكون بطاقة بسيط يحتوي على صورة، عنوان، وصف، وزر.

```html
<div
  class="bg-white shadow-lg rounded-12 overflow-hidden border border-gray-200 max-w-300"
>
  <!-- Image -->
  <div class="bg-gray-100 h-150 flex items-center justify-center">
    <span class="text-gray-400 text-48">🖼️</span>
  </div>

  <!-- Content -->
  <div class="p-6">
    <h3 class="text-20 font-bold text-dark mb-2">John Doe</h3>
    <p class="text-14 text-secondary mb-4">
      Full Stack Developer who loves building beautiful UIs with Easy CSS.
    </p>

    <!-- Action -->
    <button
      class="bg-primary text-white w-full py-2 rounded-8 font-500 hover-opacity cursor-pointer"
    >
      Follow Profile
    </button>
  </div>
</div>
```

---

## 2. Navigation Bar / شريط التنقل 🧭

A responsive navbar with a logo and links.

شريط تنقل مستجيب يحتوي على شعار وروابط.

```html
<nav
  class="bg-dark text-white px-6 py-4 flex justify-between items-center sticky-top"
>
  <!-- Logo -->
  <div class="text-24 font-bold text-primary cursor-pointer">
    Easy<span class="text-white">CSS</span>
  </div>

  <!-- Desktop Links -->
  <div class="flex gap-6 sm__hidden">
    <a href="#" class="text-white no-underline hover-red">Home</a>
    <a href="#" class="text-white no-underline hover-red">Components</a>
    <a href="#" class="text-white no-underline hover-red">Documentation</a>
  </div>

  <!-- Mobile Menu Icon -->
  <div class="hidden sm__block cursor-pointer">☰</div>
</nav>
```

---

## 3. Responsive Grid Layout / تخطيط شبكي مستجيب 📐

A 3-column grid that collapses to 1 column on small screens.

شبكة من 3 أعمدة تتقلص إلى عمود واحد في الشاشات الصغيرة.

```html
<div class="grid grid-cols-3 sm__grid-cols-1 gap-6 p-6">
  <!-- Feature 1 -->
  <div class="bg-light p-6 rounded-8 border-l-4 border-primary">
    <h4 class="text-18 font-bold mb-2">Fast Performance</h4>
    <p class="text-14">Optimized SCSS for the best loading speed.</p>
  </div>

  <!-- Feature 2 -->
  <div class="bg-light p-6 rounded-8 border-l-4 border-success">
    <h4 class="text-18 font-bold mb-2">Responsive</h4>
    <p class="text-14">Works perfectly on all screen sizes.</p>
  </div>

  <!-- Feature 3 -->
  <div class="bg-light p-6 rounded-8 border-l-4 border-warning">
    <h4 class="text-18 font-bold mb-2">Easy to Use</h4>
    <p class="text-14">Simple class names that make sense.</p>
  </div>
</div>
```

---

## 4. Responsive Modifiers Explained / شرح المعدلات المستجيبة 📱

Easy CSS uses a **Max-Width** approach for responsiveness. This means classes with a breakpoint prefix will apply when the screen is **smaller** than that breakpoint.

تستخدم Easy CSS نهج **Max-Width** للاستجابة. هذا يعني أن الكلاسات التي تحتوي على بادئة نقطة توقف سيتم تطبيقها عندما تكون الشاشة **أصغر** من نقطة التوقف تلك.

- `sm__`: Applies on screens < 640px.
- `md__`: Applies on screens < 768px.
- `lg__`: Applies on screens < 1024px.

**Example**:
`<div class="flex sm__flex-col">`

- On large screens: `display: flex` (horizontal).
- On screens < 640px: `flex-direction: column` (vertical).

---

## 5. Utility Combinations / دمج الكلاسات 🛠️

You can combine multiple utilities to create complex designs:

يمكنك دمج عدة كلاسات مساعدة لإنشاء تصميمات معقدة:

```html
<!-- A centered, rounded, shadowed box with a hover effect -->
<div
  class="mx-auto my-10 p-8 bg-white rounded-24 shadow-xl max-w-500 text-center hover-opacity cursor-pointer"
>
  <h2 class="text-28 font-900 text-primary mb-4">Ready to Start?</h2>
  <p class="text-gray-600">
    Join thousands of developers using Easy CSS today.
  </p>
</div>
```
