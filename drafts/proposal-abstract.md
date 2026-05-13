# Thesis Preview
## Simulation-Based Inference for Cosmic String Microphysics in NANOGrav Pulsar Timing Array Data

---

### Background

Pulsar timing arrays (PTAs) exploit the extreme rotational stability of millisecond pulsars
as a galaxy-scale gravitational wave detector. By monitoring the arrival times of pulses from
an array of such pulsars over years to decades, any coherent perturbation to spacetime — such
as a stochastic gravitational wave background (SGWB) — manifests as a characteristic pattern
of correlated timing residuals across pulsar pairs, described by the Hellings-Downs angular
correlation (Hellings & Downs, 1983).

In June 2023, NANOGrav reported strong evidence for such a background in their 15-year dataset
(Agazie et al., 2023), a result confirmed independently by the EPTA, PPTA, and CPTA
collaborations. The origin of this signal remains an open question. The leading astrophysical
explanation is an incoherent superposition of gravitational waves from inspiralling supermassive
black hole binaries (SMBHBs). However, several cosmological sources remain viable candidates,
among them a network of cosmic strings — one-dimensional topological defects that may have
formed during symmetry-breaking phase transitions in the early universe.

Cosmic string networks, if they exist, are characterised by a small number of microphysical
parameters: the string tension $G\mu$, the reconnection probability $p$, and the assumed loop
distribution model. These parameters directly shape the spectral energy density
$\Omega_{\mathrm{gw}}(f)$ of the emitted gravitational wave background, making PTA data a
potentially powerful probe of early-universe physics at energy scales inaccessible to collider
experiments.

---

### What This Thesis Attempts

The goal of this thesis is to build a simulation-based inference (SBI) pipeline capable of
constraining the microphysical parameters of a cosmic string network from the NANOGrav
15-year dataset, and to assess whether this approach offers practical advantages over the
existing MCMC-based analyses conducted with ENTERPRISE and PTArcade.

The pipeline consists of three components. The first is a forward simulator — referred to here
as PTAforge — that numerically solves the Velocity-dependent One-Scale (VOS) model ODEs in
an FLRW background, computes the resulting SGWB spectrum using the BOS or LRS loop
distribution models, and injects the signal into realistic mock PTA noise derived from the
NANOGrav free-spectrum posterior. The second component is a compression network, a 1D
convolutional neural network trained to reduce the high-dimensional frequency-domain PTA data
to a low-dimensional summary statistic. The third is a neural ratio estimator, implemented via
the swyft library, performing Truncated Marginal Neural Ratio Estimation (TMNRE) to recover
marginal posteriors over $(G\mu, p, \text{loop model})$.

A secondary objective, treated as an ambitious extension rather than a core commitment, is to
use TMNRE's implicit marginalisation capability to perform source separation: jointly modelling
the cosmic string signal and the SMBHB background, with the latter treated as a nuisance, to
assess whether existing MCMC analyses may carry a systematic bias from an incorrectly fixed
SMBHB model.

---

### Why This Is Worth Doing

The NANOGrav 15-year new-physics search (Afzal et al., 2023) already places constraints on
cosmic string parameters using MCMC. The present work is not motivated by the belief that
those results are wrong, but by two practical limitations of the MCMC approach.

First, scaling MCMC to jointly sample over cosmic string parameters and a realistic SMBHB
nuisance model is expensive. The SMBHB background introduces several additional parameters,
and the posterior landscape can be multimodal. SBI, and TMNRE in particular, is designed to
handle this by learning the posterior directly from simulations without requiring an explicit
likelihood evaluation, making it substantially cheaper at inference time once the network is
trained.

Second, MCMC-based analyses typically either fix the SMBHB model or marginalise over it with
a parametric template. If the true SMBHB spectrum does not match the assumed template, the
resulting cosmic string constraints may be biased. TMNRE can, in principle, marginalise over
the SMBHB contribution implicitly. Whether this actually works in the PTA band, and how well,
is one of the questions this thesis intends to test.

**On the choice of cosmic strings specifically.** Among the cosmological sources consistent
with the NANOGrav signal, cosmic strings occupy a somewhat privileged position from an
inference standpoint. Their gravitational wave spectrum is governed by a small, physically
meaningful parameter space — $(G\mu, p, \text{loop model})$ — that is well-defined,
theoretically motivated, and directly connected to early-universe symmetry breaking. This
makes them tractable for a targeted SBI pipeline: the forward model is computationally
demanding but well-posed, and the parameters have clear physical interpretations. By contrast,
other cosmological candidates such as first-order phase transitions involve broader and less
constrained model spaces, and the SMBHB background, while astrophysically motivated, does
not carry the same direct window onto fundamental physics. Cosmic strings also sit at an
interesting observational threshold: current PTA data neither confirm nor exclude them, which
means there is genuine inference work to be done, as opposed to a signal that is already
well-constrained or clearly absent.

---

### What Is New Here

The closest existing work is the saqqara pipeline (Alvey et al., 2023/2024), which demonstrated
that TMNRE-based SBI is feasible for SGWB inference in the LISA band. This thesis applies the
same inference framework to the PTA band, which introduces different noise characteristics, a
different frequency range, and a different signal morphology. More specifically, it replaces
saqqara's generic power-law signal module with a physically motivated cosmic string model
built on the VOS equations, and targets the publicly available NANOGrav 15-year data directly.

This is not a fundamental methodological advance over saqqara. The innovation is narrower: it
is the application of an existing inference paradigm to a specific physical model in a specific
frequency band where it has not yet been applied, combined with an attempt to quantify what
implicit SMBHB marginalisation actually does to the recovered posteriors.

---

### Open Questions

The work is driven by the following questions, to which I do not yet know the answers:

1. Can TMNRE recover posteriors on $(G\mu, p)$ from NANOGrav 15-year data that are consistent
   with — and ideally tighter than — the MCMC-based constraints of Afzal et al. (2023)?

2. How sensitive are the inferred cosmic string parameters to the assumed SMBHB model, and
   can TMNRE's implicit marginalisation reduce this sensitivity in a demonstrable way?

3. The loop distribution model is expected to influence the shape of $\Omega_{\mathrm{gw}}(f)$,
   though disentangling its effect from that of $G\mu$ and $p$ in the PTA band is part of what
   this analysis aims to clarify. Can the pipeline recover the loop model as a discrete
   inference target, or does it remain degenerate with the continuous parameters?

4. Can simulation-based calibration (SBC) confirm that the trained posteriors are reliable,
   and if not, what fails?

---

### Expected Outcome

The most realistic outcome is a validated SBI pipeline that reproduces existing cosmic string
posteriors from the NANOGrav 15-year data with competitive efficiency, accompanied by a
quantitative comparison to PTArcade. This alone constitutes a complete and self-contained
thesis result.

The longer-term ambition, which this thesis is designed to enable, is source separation: using
TMNRE's implicit marginalisation to jointly model the cosmic string signal and the SMBHB
background, treating the latter as a nuisance, and assessing whether current MCMC-based
analyses carry a systematic bias from an insufficiently flexible SMBHB template. If the
pipeline performs well on the single-source problem and cluster resources allow, this
experiment will be attempted within the thesis. If not, the architecture will have been built
with this extension explicitly in mind, and the groundwork — joint forward model, noise
injection, inference network design — will be in place for immediate follow-up work.

The codebase will be released as open-source software, with the forward simulator designed to
be compatible with the saqqara ecosystem for future extension.

---

*April 2026*


# پیش‌نمایش پایان‌نامه

## برآورد مبتنی بر شبیه‌سازی برای ریزفیزیک ریسمان‌های کیهانی در داده‌های آرایه زمان‌سنجی تپ‌اختر NANOGrav

---
فیزیک : ریسمان های کیهانی
بستر: امواج گرانشی توسط تپ اختر ها
روش: برآورد مبتنی بر شبیه سازی
### پیش‌زمینه

آرایه‌های زمان‌سنجی تپ‌اختر (PTAها) از پایداری چرخشی بسیار بالای تپ‌اخترهای میلی‌ثانیه‌ای به‌عنوان یک آشکارساز امواج گرانشی در مقیاس کهکشانی بهره می‌برند. با پایش زمان رسیدن تپ‌ها از مجموعه‌ای از این تپ‌اخترها در بازه‌هایی از چند سال تا چند دهه، هر آشفتگی هم‌بسته در فضا-زمان — مانند یک پس‌زمینهٔ تصادفی امواج گرانشی (SGWB) — به‌صورت الگویی شاخص از باقیمانده‌های زمان‌سنجی هم‌بسته میان جفت‌های تپ‌اختر پدیدار می‌شود که با هم‌بستگی زاویه‌ای هلینگز–داونز (Hellings & Downs, 1983) توصیف می‌شود.

در ژوئن ۲۰۲۳، NANOGrav شواهد نیرومندی برای چنین پس‌زمینه‌ای در داده‌های ۱۵سالهٔ خود گزارش داد (Agazie و همکاران، ۲۰۲۳)، که به‌طور جداگانه توسط همکاری‌های EPTA، PPTA و CPTA نیز تأیید شد. خاستگاه این سیگنال همچنان پرسشی گشوده است. توضیح اخترفیزیکی پیشرو، برهم‌نهی ناهمدوس امواج گرانشی از سامانه‌های دوتایی سیاه‌چاله‌های ابرپرجرم در حال مارپیچ‌زدن (SMBHBها) است. با این حال، چندین سرچشمهٔ کیهان‌شناختی نیز همچنان گزینه‌های پذیرفتنی هستند؛ از جمله شبکه‌ای از ریسمان‌های کیهانی — کاستی‌های توپولوژیک یک‌بعدی که شاید در گذارهای فازیِ شکست تقارن در جهان آغازین پدید آمده باشند.

شبکه‌های ریسمان کیهانی، در صورت وجود، با چند پارامتر ریزفیزیکی اندک شناخته می‌شوند: کشش ریسمان $G\mu$، احتمال بازپیوندی $p$، و الگوی پخش حلقهٔ فرض‌شده. این پارامترها به‌گونه‌ای مستقیم چگالی طیفی انرژی $\Omega_{\mathrm{gw}}(f)$ پس‌زمینهٔ امواج گرانشی گسیل‌شده را شکل می‌دهند و از این‌رو داده‌های PTA را به ابزاری توانمند برای کاوش فیزیک جهان آغازین در ترازهای انرژی دور از دسترس شتاب‌دهنده‌ها بدل می‌کنند.

---

### هدف این پایان‌نامه

هدف این پایان‌نامه ساخت یک زنجیرهٔ برآورد مبتنی بر شبیه‌سازی (SBI) است که بتواند پارامترهای ریزفیزیکی یک شبکهٔ ریسمان کیهانی را از داده‌های ۱۵سالهٔ NANOGrav محدود سازد و بررسی کند که آیا این رویکرد نسبت به تحلیل‌های کنونی مبتنی بر MCMC (با ENTERPRISE و PTArcade) برتری‌های عملی دارد یا نه.

این زنجیره از سه بخش ساخته شده است. بخش نخست یک شبیه‌ساز پیشرو — با نام PTAforge — است که معادلات دیفرانسیل معمولی الگوی تک‌مقیاسی وابسته به سرعت (VOS) را در یک پس‌زمینهٔ FLRW به‌صورت عددی حل می‌کند، طیف SGWB حاصل را با بهره‌گیری از الگوهای پخش حلقهٔ BOS یا LRS به‌دست می‌آورد، و سیگنال را در نویز ساختگیِ واقع‌گرایانهٔ PTA که از پسین طیف آزاد NANOGrav برگرفته شده، تزریق می‌کند. بخش دوم یک شبکهٔ فشرده‌سازی است؛ یک شبکهٔ عصبی کانولوشنی یک‌بعدی که برای کاهش داده‌های پربُعد PTA در حوزهٔ بسامد به یک آمارهٔ خلاصهٔ کم‌بُعد آموزش دیده است. بخش سوم یک برآوردگر نسبت عصبی است که با کتابخانهٔ swyft پیاده‌سازی شده و روش TMNRE را برای بازیابی پسین‌های حاشیه‌ای روی $(G\mu, p, \text{الگوی حلقه})$ به‌کار می‌گیرد.

یک هدف فرعی — به‌عنوان گسترشی بلندپروازانه و نه تعهد اصلی — بهره‌گیری از توان حاشیه‌گیری نهفتهٔ TMNRE برای جداسازی سرچشمه‌ها است: مدل‌سازی هم‌زمان سیگنال ریسمان کیهانی و پس‌زمینهٔ SMBHB، با در نظر گرفتن دومی به‌عنوان پارامتر مزاحم، برای سنجش این‌که آیا تحلیل‌های کنونی مبتنی بر MCMC به‌سبب تثبیت نادرست الگوی SMBHB دچار سوگیری سامانه‌ای هستند یا نه.

---

### چرا این کار ارزشمند است

جست‌وجوی فیزیک نو در داده‌های ۱۵سالهٔ NANOGrav (Afzal و همکاران، ۲۰۲۳) پیش‌تر با MCMC محدودیت‌هایی بر پارامترهای ریسمان کیهانی نهاده است. انگیزهٔ این کار نه از نادرست بودن آن یافته‌ها، بلکه از دو کاستی عملی در رویکرد MCMC سرچشمه می‌گیرد.

نخست، گسترش‌پذیری MCMC برای نمونه‌برداری هم‌زمان از پارامترهای ریسمان کیهانی و یک الگوی مزاحم واقع‌گرایانهٔ SMBHB پرهزینه است. پس‌زمینهٔ SMBHB چندین پارامتر تازه وارد می‌کند و چشم‌انداز پسین می‌تواند چندقله‌ای باشد. SBI، و به‌ویژه TMNRE، برای رویارویی با این چالش طراحی شده‌اند، زیرا پسین را بی‌نیاز از ارزیابی آشکار درست‌نمایی و مستقیماً از شبیه‌سازی‌ها می‌آموزند و پس از آموزش شبکه، در گام برآورد بسیار کم‌هزینه‌تر هستند.

دوم، تحلیل‌های مبتنی بر MCMC معمولاً یا الگوی SMBHB را ثابت می‌گیرند یا با یک قالب پارامتری روی آن حاشیه‌گیری می‌کنند. اگر طیف راستین SMBHB با این قالب سازگار نباشد، محدودیت‌های به‌دست‌آمده برای ریسمان‌های کیهانی می‌توانند سوگیر شوند. TMNRE در اصل می‌تواند سهم SMBHB را به‌صورت نهفته حاشیه‌گیری کند. این‌که این کار در باند PTA تا چه اندازه کارآمد است، یکی از پرسش‌های اصلی این پایان‌نامه است.

**دربارهٔ گزینش ریسمان‌های کیهانی.** در میان سرچشمه‌های کیهان‌شناختی سازگار با سیگنال NANOGrav، ریسمان‌های کیهانی جایگاهی ویژه از دیدگاه برآورد دارند. طیف امواج گرانشی آن‌ها با فضای پارامتری کوچکی کنترل می‌شود — $(G\mu, p, \text{الگوی حلقه})$ — که روشن، دارای پشتوانهٔ نظری، و به‌گونه‌ای مستقیم به شکست تقارن در جهان آغازین پیوند دارد. این ویژگی آن‌ها را برای یک زنجیرهٔ SBI هدفمند مناسب می‌سازد: مدل پیشرو سنگین ولی خوش‌تعریف است و پارامترها برداشت فیزیکی روشنی دارند. در برابر، گزینه‌هایی مانند گذارهای فازی مرتبهٔ نخست دارای فضاهای مدلی گسترده‌تر و کم‌محدودتر هستند، و پس‌زمینهٔ SMBHB با وجود انگیزهٔ اخترفیزیکی، همان پنجرهٔ مستقیم به فیزیک بنیادی را فراهم نمی‌کند. افزون بر این، ریسمان‌های کیهانی در مرزی رصدی قرار دارند که نه تأیید شده‌اند و نه رد، و این یعنی جای کار برآوردی واقعی وجود دارد.

---

### نوآوری این کار

نزدیک‌ترین کار موجود، زنجیرهٔ saqqara (Alvey و همکاران، ۲۰۲۳/۲۰۲۴) است که نشان داد SBI مبتنی بر TMNRE برای برآورد SGWB در باند LISA شدنی است. این پایان‌نامه همان چارچوب را به باند PTA می‌آورد که ویژگی‌های نویزی، بازهٔ بسامدی، و ریخت سیگنال متفاوتی دارد. به‌طور مشخص، به‌جای ماژول سیگنال قانون توانیِ saqqara، یک الگوی فیزیکی ریسمان کیهانی بر پایهٔ معادلات VOS جایگزین می‌شود و داده‌های همگانی ۱۵سالهٔ NANOGrav به‌طور مستقیم هدف قرار می‌گیرند.

این کار یک پیشرفت بنیادین روش‌شناختی نیست؛ نوآوری آن محدودتر است: به‌کارگیری یک پارادایم برآوردی موجود برای یک الگوی فیزیکی مشخص در یک باند بسامدی مشخص، همراه با تلاش برای اندازه‌گیری اثر حاشیه‌گیری نهفتهٔ SMBHB بر پسین‌های به‌دست‌آمده.

---

### پرسش‌های گشوده

این پژوهش با پرسش‌های زیر پیش می‌رود که پاسخ آن‌ها هنوز روشن نیست:

1. آیا TMNRE می‌تواند پسین‌هایی برای $(G\mu, p)$ از داده‌های ۱۵سالهٔ NANOGrav به‌دست آورد که با محدودیت‌های مبتنی بر MCMC در Afzal و همکاران (۲۰۲۳) سازگار بوده و حتی دقیق‌تر باشند؟
    
2. پارامترهای برآوردشدهٔ ریسمان کیهانی تا چه اندازه به الگوی SMBHB وابسته‌اند، و آیا حاشیه‌گیری نهفتهٔ TMNRE می‌تواند این وابستگی را به‌گونه‌ای سنجیدنی کاهش دهد؟
    
3. الگوی پخش حلقه بر شکل $\Omega_{\mathrm{gw}}(f)$ اثر می‌گذارد، اما جداسازی اثر آن از $G\mu$ و $p$ در باند PTA بخشی از هدف این کار است. آیا زنجیره می‌تواند الگوی حلقه را به‌عنوان یک کمیت گسسته بازیابی کند، یا این کمیت با پارامترهای پیوسته درهم‌تنیده می‌ماند؟
    
4. آیا کالیبراسیون مبتنی بر شبیه‌سازی (SBC) می‌تواند نشان دهد که پسین‌های آموزش‌دیده قابل اعتمادند؟ اگر نه، کدام بخش دچار شکست می‌شود؟
    

---

### دستاورد مورد انتظار

واقع‌بینانه‌ترین دستاورد، یک زنجیرهٔ SBI اعتبارسنجی‌شده است که پسین‌های موجود برای ریسمان‌های کیهانی را از داده‌های ۱۵سالهٔ NANOGrav با کارایی رقابتی بازتولید کند، همراه با یک سنجش کمّی در برابر PTArcade. همین نتیجه به‌تنهایی یک پایان‌نامهٔ کامل به‌شمار می‌آید.

چشم‌انداز بلندمدت‌تر — که این کار زمینه‌ساز آن است — جداسازی سرچشمه‌ها است: به‌کارگیری حاشیه‌گیری نهفتهٔ TMNRE برای مدل‌سازی هم‌زمان سیگنال ریسمان کیهانی و پس‌زمینهٔ SMBHB، با در نظر گرفتن دومی به‌عنوان پارامتر مزاحم، و سنجش این‌که آیا تحلیل‌های کنونی مبتنی بر MCMC به‌سبب الگوی ناکافی SMBHB دچار سوگیری سامانه‌ای هستند یا نه. اگر زنجیره در مسئلهٔ تک‌سرچشمه‌ای عملکرد خوبی داشته باشد و توان پردازشی خوشه فراهم باشد، این آزمایش در چارچوب پایان‌نامه انجام خواهد شد. در غیر این صورت، ساختار سامانه از آغاز با در نظر گرفتن این گسترش طراحی شده و زیرساخت — شامل مدل پیشروی مشترک، تزریق نویز، و طراحی شبکهٔ برآورد — برای کارهای پسین آماده خواهد بود.

کد این پروژه به‌صورت متن‌باز منتشر خواهد شد و شبیه‌ساز پیشرو به‌گونه‌ای طراحی می‌شود که با بوم‌سازگان saqqara برای گسترش‌های آینده سازگار باشد.

---

_آوریل ۲۰۲۶_