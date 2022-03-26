# Çeviri Hakkında

*Bu repo (web versiyonunu şuradan görüntüleyebilirsiniz: tolgarecep.github.io/interpretable-ml-book) Christoph Molnar'ın "Interpretable Machine Learning" kitabının Türkçe çevirisini içerir. Orijinal metne buradan ulaşabilirsiniz:* 

*Çeviride Türkçe halleri kullanılmayan/çok az kullanılan kelimeler İngilizce bırakılmıştır. Bölüm 2 - Özet'te belirtildiği üzere bu kitap sıfırdan makine öğrenmesi öğretmeyi amaçlamaz.* 

*Bu dosyanın kalanı README.md dosyasının Türkçe çevirisidir. Changelog henüz çevirilmedi.*

# Yorumlanabilir Makine Öğrenmesi

Makine öğrenmesi modellerinin aldıkları kararlar ve onların davranışlarının açıklanması.

![Build Status](https://github.com/christophM/interpretable-ml-book/actions/workflows/Book.yaml/badge.svg)

## Özet
Kitabın güncel halini burada bulabilirsiniz: https://christophm.github.io/interpretable-ml-book/

Bu kitap açıklanabilir makine öğrenmesi hakkında. Makine öğrenmesi günlük hayatımızdaki birçok ürünün ve prosedürün içine yerleşmiş olsa da makineler tarafından alınan kararlar kendiliğinden herhangi bir izah içermiyor. Modelin yaptıklarının izahı, modele ve modelin aldığı karara olan güveni arttırır. Algoritmanın programcısı olarak bu öğrenmiş (optimize edilmiş) modele güvenip güvenemeyeceğinizi bilmelisiniz. Genelleştirilebilir feature'lar öğrenebilmiş mi? Ya da training verisinde modelin yakaladığı garip yapaylıklar var mı? Bu kitap, kara-kutuları olabildiğince transparan yapmak ve kara-kutuların aldığı kararları açıklamak için geliştirilen metodları gözden geçiriyor. İlk bölümde sade ve yorumlanabilir modeller üreten algoritmalar onları nasıl yorumlayacağınıza dair açıklamalarla beraber sunuluyor. Sonraki bölümler karmaşık modelleri ve onların kararlarını analiz etmeye odaklanıyor. İdeal bir gelecekte makineler aldıkları kararları açıkalayabilecek ve daha insani bir algoritmik geleceğe geçiş yapacak. Bu kitap makine öğrenmesiyle çalışanlara, veri bilimcilere, istatistikçilere ve makine öğrenmesi algoritmalarını ve zeki algoritmaları kullanmaya karar vermiş menfaat sahibi kimselere tavsiye edilir. 

Bu kitap master branch'den (çeviri turkish branch'inden) otomatik olarak kuruldu ve Github Actions ile gh-pages'a push edildi.

## Destek
[Nasıl destek olabilirim?](CONTRIBUTING.md)

## Kitabın render'lanması
Repo'yu clone'layın:
```{shell}
git clone git@github.com:christophM/interpretable-ml-book.git
```
Tüm gerekliliklerin kurulu olduğundan emin olun. Bu kitap R paketi yapısında olduğundan gereklilikler kolayca kurulabilir; sadece R ve devtools kütüphanesi gerekli. Kitap repo'sunun klasöründe bir R oturumu başlatın ve şunu yazın:
```{r}
devtools::install_deps()
```
Kitabı render'lamak için, bir R oturumu başlatıp şunu yazın:
```{r}
setwd("manuscript")
# first, generate the references
source("../scripts/references.R")
bookdown::render_book('.', 'bookdown::gitbook')
```
Render'ladıktan sonra kitabın HTML dosyaları "\_book" dosyasında olur. Daha sonra `index.html`'e çift tıklayabilir ya da R'de şunu yapabilirsiniz: 
```{r}
browseURL('_book/index.html')
```
## lulu.com ile çıktı alma
- Export from Leanpub in 7.44" x 9.68" 	18.9cm x 24.6cm
- Kapak için: 7.565 x 9.925", 19.226 x 25.224cm, [tavsiye edilen boyutlar](https://connect.lulu.com/en/discussion/33279/recommended-book-cover-image-dimensions)
- Ön kapaktaki font: Francois One

## Yazım
Hem leanpub hem de bookdown'da geçerli bazı bilgiler:
- Başlıklar # ile, altbaşlıklar ## ile başlar ve benzer şekilde ilerler.
- Başlıklara {#tag-of-the-title} ile tag eklenebilir.
- Bölümler `[text of the link](#tag-of-the-title)` ile refere edilebilir.
- Figürler `[text of the link](#fig:tag-of-r-chunk-that-produced-figure)` ile refere edilebilir.
- Matematiksel ifadeler `$` (inline) ya da `$$` (extra line) ile başlayıp bitirilir. leanpub ve regexpr için otomatik olarak değiştirilir. Dönüştürme script'i yalnızca formülde boş alan yoksa çalışır.
- Formüller ve yazı arasında boş satır bırakın (if formula not inline). Formüller (with $$ ... $$) birçok satırda değil sadece tek bir satırda olmalı (due to parser).
- Referanslar `[^ref-tag]` şeklinde yazılmalı ve ilgili dosyanın sonunda `[^ref]: Details of the reference ...` ile beraber olmalı. Boşluğun koyulduğundan emin olun. Referanslar 10-reference.Rmd içinde references.R ile birliktedir. `[^ref-tag]: ` ifadesini text içinde kullanmadığınızdan emin olun, sadece en aşağıda referanslar için kullanın. 

Ekstra satırları düzeltmek için:
HTML kitabını kurun, manuscript/\_book/libs/gitbook*/css/style.css'a giderek, line-height:1.7'ı line-height:2.5 olarak değiştirin, Chrome'da HTML'i açarak "custom margin" seçeneği ile pdf olarak çıktı alın.

## Changelog
All notable changes to the book will be documented here.

### v2.0 (IN PROGRESS) [html version]
- Added "Preface by the Author" chapter
- Started section on neural network interpretation
- Added chapter on feature visualization
- Added SHAP chapter
- Added Anchors chapter
- Fixed error in logistic regression chapter: Logistic regression was predicting class "Healthy", but interpretation in the text was for class "Cancer". Now regression weights have the correct sign.
- Renamed Feature Importance chapter to "Permutation Feature Importance"
- Added chapter about functional decomposition
- Rearranged interpretation methods by local, global and deep learning (before: model-agnostic, example-based, deep learning)
- Errata:
	- Chapter 4.3 GLM, GAM and more: Logistic regression uses logit, not logistic function as link function.
	- Chapter Linear models: Formula for adjusted R-squared was corrected (twice)
        - Chapter Decision Rules: Newly introduced mix up between Healthy and Cancer in OneR chapter was fixed.
        - Chapter RuleFit: The importance of the linear term in the total importance formulate was indexed with an $l$ instead of $j$.
- Updated images

### v1.1 (2019-03-23) [Print version, ebook version]
- Fixes wrong index in Cooks Distance summation (i -> j)
- fixed boxplot formula (1.5 instead of 1.58)
- Change to colorblind-friendly color palettes (viridis)
- Make sure plots work in black and white as well
- Extends counterfactual chapter with MOC (by Susanne Dandl)

### v1.0 (2019-02-21)
- Extensive proofreading and polishing

### v0.7 (2018-11-21)
- Renamed Definitions chapter to Terminology
- Added mathematical notation to Terminology (former Definitions) chapter
- Added LASSO example
- Restructured lm chapter and added pros/cons
- Renamed "Criteria of Interpretability Methods" to "Taxonomy of Interpretability Methods"
- Added advantages and disadvantages of logistic regression
- Added list of references at the end of book
- Added images to the short stories
- Added drawback of shapley value: feature have to be independent
- Added tree decomposition and feature importance to tree chapter
- Improved explanation of individual prediction in lm
- Added "What's Wrong With my Dog" example to Adversarial Examples
- Added links to data files and pre-processing R scripts

### v0.6 (2018-11-02)
- Added chapter on accumulated local effects plots
- Added some advantages and disadvantages to pdps
- Added chapter on extending linear models
- Fixed missing square in the Friedman H-statistic
- Added discussion about training vs. test data in feature importance chapter
- Improved the definitions, also added some graphics
- Added an example with a categorical feature to PDP

### v0.5 (2018-08-14)
- Added chapter on influential instances
- Added chapter on Decision Rules
- Added chapter on adversarial machine examples
- Added chapter on prototypes and criticisms
- Added chapter on counterfactual explanations
- Added section on LIME images (by Verena Haunschmid)
- Added section on when we don't need interpretability
- Renamed chapter: Human-style Explanations -> Human-friendly Explanations

### v0.4 (2018-05-23)
- Added chapter on global surrogate models
- Added improved Shapley pictograms
- Added acknowledgements chapter
- Added feature interaction chapter
- Improved example in partial dependence plot chapter
- The weights in LIME text chapter where shown with the wrong words. This has been fixed.
- Improved introduction text
- Added chapter about the future of interpretability
- Added Criteria for Intepretability Methods

### v0.3 (2018-04-24)
- Reworked the Feature Importance Chapter
- Added third short story
- Removed xkcd comic
- Merged introduction and about the book chapters
- Addeds pros & cons to pdp and ice chapters
- Started using the iml package for plots in ice and pdp
- Restructured the book files for Leanpub
- Added a cover
- Added some CSS for nicer formatting

### v0.2 (2018-02-13)
- Added chapter about Shapley value explanations
- Added short story chapters
- Added donation links in Preface
- Reworked RuleFit with examples and theory.
- Interpretability chapter extended
- Add chapter on human-style explanations
- Making it easier to collaborate: Travis checks if book can be rendered for pull requests

### v0.1 (2017-12-03)
- First release of the Interpretable Machine Learning book
