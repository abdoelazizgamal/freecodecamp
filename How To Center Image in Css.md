

JUNE 14, 2020/[#CSS](https://www.freecodecamp.org/news/tag/css/)

# كيفية توسيط صورة عموديًا و أفقيًا بواسطة CSS  
![Cem Eygi](https://www.freecodecamp.org/news/content/images/size/w100/2019/08/Ekran-Resmi-2019-08-01-12.13.08.png)

[Cem Eygi](https://www.freecodecamp.org/news/author/cemeygi/)

![How to Center an Image Vertically and Horizontally with CSS](https://cdn-media-2.freecodecamp.org/w1280/5f9c9a4c740569d1a4ca24c2.jpg)

يعاني العديد من المطورين في التعامل مع الصور كالعمل علي جعل التصميم متجاوب مع جميع الشاشات   [responsiveness](https://www.freecodecamp.org/news/css-responsive-image-tutorial/) . و محاذاة العنصر (alignment)  والتي تعد أمرا صعبًا خاصةً عند توسيط الصورة في منتصف العنصر أو الصفحة .

لذلك في هذا المنشور ، سأعرض بعضًا من أكثر الطرق شيوعًا لتوسيط الصورة عموديًا وأفقيًا باستخدام خصائص CSS المختلفة .

لقد فرغت من كتابة منشور سابق متعلق بخصائص css التالية  [Position](https://www.freecodecamp.org/news/how-to-use-the-position-property-in-css-to-align-elements-d8f49c403a26/)  و  [Display](https://www.youtube.com/watch?v=hgoFi0fCv3w)
 إذا لم تكن على دراية بتلك الخصائص وتبدو غريبة بالنسبة إليك فإنني أوصي بمراجعة هذه المنشورات قبل قراءة هذه المقالة
 
هنا نسخة فيديو إذا كنت تريد التحقق منها:

### توسيط الصورة أفقيًا
لنبدأ بتوسيط الصورة أفقيًا باستخدام 3 خصائص CSS مختلفة
### Text-Align

الطريقة الأولي لتوسيط عنصر أفقيًا هي بإستخدام خاصية `text-align` مع الأخذ بالإعتبار أن هذه الخاصية لا تعمل إلا في حالة وجود الصورة داخل عنصر خاصية الdisplay  الخاصة به تكون قيمتها الإفتراضية  block كعنصر ال `<div>`:


```html
<style>
  div {
    text-align: center;
  }
</style>

<div>
  <img src="your-image.jpg">
</div>
```

### Margin: Auto

طريقة أخري لتوسيط الصورة أفقيًا وهي بإستخدام خاصية الهامش `margin` و إعطائها القيمة `auto` وهذه القيمة تُطبق علي الهامش الأيمن  والأيسر   (`margin: auto` => for left-margin and right-margin )

استخدام   `margin: auto` ليس كافيًا  لتوسيط الصورة أفقيًا  ، هناك خاصيتان  إضافيتان يجب  إستخدامهم 

المشكلة تكمن أن  `margin: auto`  ليس لها تأثير علي العناصر التي تكون inline level  وبالتالي ليس لها تأثير علي الصورة وذلك لأن خاصية ال `display `  الخاصة بيها  قيمتها الإفتراضية `inline-block`  مما يعني أن الصورة ( inline element )   لذلك نحتاج  إلي تحويلها  إلي عنصر `block` .
```css
img {
  margin: auto;
  display: block;
}
```

ثانيًا ، نحتاج لوضع عرض مُحدد للصورة وهنا تكمن الحيلة ، عند وضع عرض مُحدد يتم طرحُه من المساحة الكاملة 100% 
وتوزع المساحة المتبقية يمينا ويسارًا بالتساوي ،  ف تعمل خاصية ال  `margin:auto` بمحاذاة الصورة تلقائيًا ،  هذا لن يعمل في حالة إعطائك الصورة العرض كاملاً  100% لأنه لن تكون هناك مساحة كافية لتوزيعها .
```css
img {
  width: 60%;
  margin: auto;
  display: block;
}
```

### Display: Flex

الطريقة الثالثة لتوسيط عنصر أفقيا بإستخدام خاصية `display: flex`، كما إستخدمنا خاصية ال `text-align` للعنصر الأب أو للعنصر الذي يحتوي علي  العنصر الذي نريد توسيطه 'container'  ، فإننا نستخدم خاصية ال `display:flex` للعنصر الأب أيضا ( container )

ولكن ضع في الإعتبار أن إستخدام خاصية ال ` display : flex `  فقط لن يكون كافيًا ، يجب اعطاء العنصر الأب أو الذي يحتوي علي العنصر المُراد توسيطه  خاصية إضافية وهي `justify-content : center ` 
```css
div {
  display: flex;
  justify-content: center;
}

img {
  width: 60%;
}
```

خاصية ال `justify-content` لا تعمل إلا  في وجود خاصية ال  `display : flex` وهي تعمل علي توسيط العنصر أفقيًا .

أخيرًا ، يجب أن يكون عرض الصورة أصغر من عرض الأب وإلا فإنها تأخذ 100٪ من المساحة ومن ثم لا يمكننا توسيطها أفقيًا

**ملحوظة هامة** الخاصية `display : flex ` غير مدعومة في الإصدارات القديمة من المتصفحات 
  [ لمعرفة المزيد من التفاصيل](https://caniuse.com/#search=display%20flex)
	
## توسيط الصورة عموديًا

### Display: Flex

بالنسبة للمحاذاة الرأسية ، يعد استخدام`display: flex` مفيدًا حقًا مرة أخرى 

ضع في اعتبارك أن يبلغ  ارتفاع العنصر الأب أو العنصر الذي يحتوي علي الصورة  800px ، ولكن ارتفاع الصورة يبلغ 500px  فقط
```css
div {
  display: flex;
  justify-content: center;
  height: 800px;
}

img {
  width: 60%;
  height: 500px;
}
```

في هذه الحالة إضافة سطر واحد من الكود  `align-items:center `  للعنصر الأب أو الذي يحتوي علي الصورة تعمل علي توسيط الصورة رأسيًا .

```css
div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 800px;
}
```

خاصية ` align-items : center`   لا تقوم بتوسيط موضع العنصر أفقيًا إلا عند استخدامها مع خاصية ` display : flex `
### Position: Absolute & Transform Properties

طريقة أخري للمحاذاة الرأسية عن طريق استخدام خاصية ال` position ` و خاصية ال `transform ` معًا ، هذه الطريقة تحتاج إلي تركيز لذا سنتبع بضع خطوات بسيطة
### الخطوة الأولي : Define Position Absolute
أول خطوة هي تغيير خاصية ال ` position`  للصورة  من القيمة الإفتراضية للعناصر وهي  ` static`  للقيمة  `absolute` الوضع المٌطلق والتي تجعل العنصر مكانه ليس محجوزًا في ال work flow ، أيضًا يجب اعطاء العنصر الأب الذي يحتوي علي الصورة  قيمة للخاصية ` position ` وهي  ` relative` 

```css
div {
  height: 800px;
  position: relative;
  background: red;
}

img {
  width: 80%;
  position: absolute;
}
```

### الخطوة الثانية : Define Top & Left Properties

الخطوة الثانية : نقوم بتحديد خاصية ` top ` و خاصية ` left `  للصورة ووضع قيمة كل منهم ب  50% ، ماذا تعني هذه الخطوة ؟  
تعني تحريك الصورة بجعل بدايتها من الأعلي واليسار تبدأ عند 50% من العنصر الأب أو الحاوية لها لذلك أعطينا للأب قيمة ` relative ` للخاصية  ` position ` حتي تكون النسبة محسوبة 50%  من العنصر الأب ، ولكن حتي مع فعل ذلك لن تكون الصورة متوسطة أفقيا ورأسيا وذلك لأن  بداية الصورة هي من تقع عند نقطة منتصف الأب
```css
img {
  width: 80%;
  position: absolute;
  top: 50%;
  left: 50%;
}
```

### الخطوة الثالثة : Define Transform Property
في الخطوة الثانية لاحظنا أن الصورة لم تكن في المنتصف تماما وخرج جزءٌ منها عن العنصر الأب وذلك لأنها تم توسيطها ولكن بداية الصورة من الأعلي والأيسر  هي من تقع عند منتصف الأب ،  إذًا نحتاج إلي جعل نقطة منتصف الصورة هي من تقع عند نقطة منتصف الأب حتي يتم التوسيط أفقيًا ورأسيًا ، ولكن كيف يتم ذلك ؟ بتحريك الصورة أفقيا بمقدار يساوي نصف عرضها ولكن ف الاتجاه المعاكس وعموديًا بمقدار يساوي نصف طولها ولكن في الإتجاه المعاكس ، وكيف يتم ذلك إذا لم يكن لديك علم بطول الصورة أو عرضها بإستخدام خاصية  ` transform  : translate (-50% , -50% ) `
وهذه  الخاصية تقوم بتحريك الصورة علي المحور " س " و " ص" بمقدار  يساوي نصف عرضها ونصف طولها والاتجاه المعاكس هنا هو تحريكها في اتجاهي اليمين والأعلي لذا تم التعبير عن الاتجاهين بالإشارة السالبة :

```css
img {
  width: 80%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

هناك طرق أخرى لتوسيط العناصر أفقيًا ورأسيًا ، لكنني أوضحت أكثرها شيوعًا. آمل أن يساعدك هذا المنشور في فهم كيفية محاذاة صورك في وسط الصفحة أو العنصر 
**If you want to learn more about Web Development, feel free to visit my  [Youtube Channel](https://www.youtube.com/channel/UC1EgYPCvKCXFn8HlpoJwY3Q?view_as=subscriber)  for more.**

شكرا لقرائتك!

----------

![Cem Eygi](https://www.freecodecamp.org/news/content/images/size/w100/2019/08/Ekran-Resmi-2019-08-01-12.13.08.png)

[Cem Eygi](https://www.freecodecamp.org/news/author/cemeygi/)

Front-end Developer // Follow Me on Youtube: https://bit.ly/3dBiTUT

----------

If you read this far, tweet to the author to show them you care.  Tweet a thanks

Learn to code for free. freeCodeCamp's open source curriculum has helped more than 40,000 people get jobs as developers.  [Get started](https://www.freecodecamp.org/learn/)

freeCodeCamp is a donor-supported tax-exempt 501(c)(3) nonprofit organization (United States Federal Tax Identification Number: 82-0779546)

Our mission: to help people learn to code for free. We accomplish this by creating thousands of videos, articles, and interactive coding lessons - all freely available to the public. We also have thousands of freeCodeCamp study groups around the world.

Donations to freeCodeCamp go toward our education initiatives and help pay for servers, services, and staff.

You can  [make a tax-deductible donation here](https://www.freecodecamp.org/donate/).

Trending Guides

[What is JavaScript?](https://www.freecodecamp.org/news/what-is-javascript-javascript-code-explained-in-plain-english/)[Linux List Processes](https://www.freecodecamp.org/news/linux-list-processes-how-to-check-running-processes/)[Web Page Text Editor](https://www.freecodecamp.org/news/web-page-text-editor-how-to-open-html-code-in-mac-textedit/)[What is Open Source?](https://www.freecodecamp.org/news/what-is-open-source-software-explained-in-plain-english/)[Sim Swapping Attacks](https://www.freecodecamp.org/news/protect-yourself-against-sim-swapping-attacks/)[RNG Meaning in Gaming](https://www.freecodecamp.org/news/rng-meaning-what-does-rng-stand-for-in-gaming/)[Model View Controller](https://www.freecodecamp.org/news/the-model-view-controller-pattern-mvc-architecture-and-frameworks-explained/)[Front End Development](https://www.freecodecamp.org/news/front-end-developer-what-is-front-end-development-explained-in-plain-english/)[Full Stack Developer?](https://www.freecodecamp.org/news/what-is-a-full-stack-developer-back-end-front-end-full-stack-engineer/)[JavaScript Switch Case](https://www.freecodecamp.org/news/javascript-switch-case-js-switch-statement-example/)

[Bash Sleep](https://www.freecodecamp.org/news/bash-sleep-how-to-make-a-shell-script-wait-n-seconds-example-command/)[Bash Array](https://www.freecodecamp.org/news/bash-array-how-to-declare-an-array-of-strings-in-a-bash-script/)[What is a CV?](https://www.freecodecamp.org/news/what-is-a-cv-and-how-is-it-different-from-a-resume/)[Coding Programs](https://www.freecodecamp.org/news/coding-programs-101-ways-to-learn-to-code-for-free/)[How to Exit Vim](https://www.freecodecamp.org/news/how-to-exit-vim/)[HTML Line Break](https://www.freecodecamp.org/news/html-line-break-how-to-break-a-line-with-the-html-br-tag/)[C# String to Int](https://www.freecodecamp.org/news/how-to-convert-a-string-to-an-int-in-c-tutorial-with-example-code/)[Logical fallacies](https://www.freecodecamp.org/news/logical-fallacies-definition-fallacy-examples/)[JavaScript Online](https://www.freecodecamp.org/news/javascript-online-html-css-js-code-editor-list-browser-ide-tools/)[SQL Case Statement](https://www.freecodecamp.org/news/sql-case-statement-tutorial-with-when-then-clause-example-queries/)

[JavaScript toLowerCase](https://www.freecodecamp.org/news/javascript-tolowercase-how-to-convert-a-string-to-lowercase-and-uppercase-in-js/)[Angular NgClass Example](https://www.freecodecamp.org/news/angular-ngclass-example/)[SQL Aggregate Functions](https://www.freecodecamp.org/news/sql-aggregate-functions-with-example-data-queries-for-beginners/)[What is Web Development?](https://www.freecodecamp.org/news/what-is-web-development-how-to-become-a-web-developer-career-path/)[Best Way to Learn Python](https://www.freecodecamp.org/news/the-best-way-to-learn-python-python-programming-tutorial-for-beginners/)

[Word Count in Google Docs](https://www.freecodecamp.org/news/word-count-in-google-docs-tutorial-counting-words-and-characters-in-a-google-doc-or-word-file/)[Node Environment Variables](https://www.freecodecamp.org/news/how-to-use-node-environment-variables-with-a-dotenv-file-for-node-js-and-npm/)[Event Viewer in Windows 10](https://www.freecodecamp.org/news/event-viewer-how-to-access-the-windows-10-activity-log/)[Combine 1st/Last Name Excel](https://www.freecodecamp.org/news/combine-first-last-names-excel/)[JavaScript if-else & if-then](https://www.freecodecamp.org/news/javascript-if-else-and-if-then-js-conditional-statements/)

	[About](https://www.freecodecamp.org/news/about/)[Alumni Network](https://www.linkedin.com/school/free-code-camp/people/)[Open Source](https://github.com/freeCodeCamp/)[Shop](https://www.freecodecamp.org/shop/)[Support](https://www.freecodecamp.org/news/support/)[Sponsors](https://www.freecodecamp.org/news/sponsors/)[Academic Honesty](https://www.freecodecamp.org/news/academic-honesty-policy/)[Code of Conduct](https://www.freecodecamp.org/news/code-of-conduct/)[Privacy Policy](https://www.freecodecamp.org/news/privacy-policy/)[Terms of Service](https://www.freecodecamp.org/news/terms-of-service/)[Copyright Policy](https://www.freecodecamp.org/news/copyright-policy/)