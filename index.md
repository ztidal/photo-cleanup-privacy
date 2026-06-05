---
title: "Privacy Policy · 隐私政策 — Local Photo Cleanup"
---

# 隐私政策 / Privacy Policy

**本地智能照片清理 / Local Photo Cleanup**

生效日期 / Effective date: 2026-06-05
最近更新 / Last updated: 2026-06-05
开发者 / Developer: ZTIDAL
联系邮箱 / Contact: 494485959@qq.com

---

# 中文版

## 引言

「本地智能照片清理」(以下简称「本应用」)是一款**隐私优先**的照片清理工具。我们的核心承诺是:

> **照片不出手机 · 100% 本地处理 · 0 上传**

本应用帮助你找出旧截图、相似照片、模糊废片和占空间的大视频,以便你自行清理、释放设备存储。**所有照片与视频的分析、比对和识别全部在你的设备本地完成,绝不会上传到任何服务器,也绝不会离开你的手机。**

我们没有服务器、没有账号系统、没有云存储。我们无法看到、收集或访问你的照片。

本隐私政策说明本应用如何处理信息,适用于 iOS 与 Android 两个平台。请在使用本应用前仔细阅读。

---

## 1. 我们收集什么 / 不收集什么

### 我们不收集任何个人信息

- **我们不收集你的照片或视频。** 它们仅在你的设备本地被读取与分析,绝不上传、绝不外传。
- **我们不收集你的姓名、邮箱、电话、位置或任何账号信息。** 本应用无需注册、无需登录。
- **我们不为识别你而收集设备标识符**(详见第 6 节关于广告的说明)。
- **我们不建立用户画像,也不进行跨应用 / 跨网站的行为追踪。**
- **我们(开发者)在自有服务器上不留存任何用户数据——因为我们根本没有服务器。**

### 仅在你的设备本地存在的数据

为实现核心功能,以下数据**仅保存在你的设备本地**,不会发送给我们或任何第三方:

| 数据 | 用途 | 存储位置 |
|---|---|---|
| 相册中的照片 / 视频内容 | 本地识别可清理项(见第 2、3 节) | 始终保留在你的相册中,本应用仅在内存中临时分析 |
| 暂存箱条目(待删除项的引用,如相册资源 ID、分类、时间戳、文件大小) | 删除前的安全缓冲,支持恢复(见第 4 节) | 设备本地存储 |
| 应用设置与偏好(语言、深色模式、保护规则、是否默认进暂存箱等) | 记住你的选择 | 设备本地(系统的本地键值存储 `shared_preferences`) |

以上数据均不离开设备,卸载应用即随之清除(已被你确认删除的照片除外,删除是不可逆的系统操作)。

---

## 2. 设备本地处理(On-Device Processing)

本应用的全部「智能」分析均在你的设备本地、完全离线地运行,**不需要联网即可完成照片分析**。具体包括:

- **感知哈希(Perceptual Hash)** —— 用于找出相似 / 重复照片;
- **拉普拉斯模糊检测(Laplacian Blur Detection)** —— 用于识别模糊废片;
- **二维码 / 条码识别(`flutter_zxing`,本地编译的 ZXing C++ 核心)** —— 仅对截图类照片做识别,用于「保护含二维码的截图」等功能,**不下载任何模型、不联网、不调用任何云端识别服务**;
- **基于元数据的筛选** —— 如截图的拍摄时间、视频文件大小等。

这些计算在后台隔离线程(isolate)中进行,处理过程中照片数据仅短暂存在于设备内存,分析结束即释放,**不写入任何外部存储、不发送到网络**。

---

## 3. 相册访问与用途

为了帮你找出可清理的照片和视频,本应用需要访问你的设备相册。

**我们请求相册权限的唯一目的,是在你的设备本地读取并分析照片 / 视频,以识别可清理项(旧截图、相似照片、模糊照片、大视频)。**

- **iOS:** 我们请求「照片」访问权限(`NSPhotoLibraryUsageDescription`)以读取相册进行本地分析;在你确认删除时,请求写入权限(`NSPhotoLibraryAddUsageDescription`)以执行删除。你可以选择仅授予「部分照片」访问权限,本应用将仅分析你所选择的范围。
- **Android:** 我们请求 `READ_MEDIA_IMAGES`、`READ_MEDIA_VIDEO`(及旧系统上的 `READ_EXTERNAL_STORAGE`)以读取相册;`ACCESS_MEDIA_LOCATION` 用于在读取媒体时正确处理图片(如保留原始元数据),**我们不收集、不上传你的位置信息**。

**删除行为完全由你发起和确认。** 本应用不会在未经你明确确认的情况下删除任何照片或视频。删除是通过系统相册接口执行的标准操作。

---

## 4. 暂存箱(删除前的安全缓冲)

为防止误删,本应用提供「暂存箱」机制:

- 当你选择清理某些照片 / 视频时,它们会**先进入暂存箱**,而非立即被永久删除;
- 暂存箱中的项目**你可以随时恢复**;
- 暂存箱**完全保存在你的设备本地**(以本地存储的形式持久化,使其在重启应用后依然存在),其中仅保存待删除项的引用信息(相册资源 ID、所属分类、加入时间、文件大小),**不复制、不上传照片本身**;
- 只有当你**最终确认删除**后,本应用才会通过系统接口执行真正的删除。**真正的删除是不可逆的**,请在最终确认前谨慎检查。

---

## 5. 网络与服务器

- 本应用**没有自有后端服务器**,**不上传**你的照片、视频或任何个人数据。
- 本应用的核心清理功能**完全离线**,无需联网即可使用。
- 唯一会产生网络连接的情形,是下文第 6 节所述的第三方广告 SDK(用于拉取广告)。除此之外,本应用不主动进行任何与用户数据相关的网络传输。

---

## 6. 第三方 SDK 及其数据处理

本应用集成了以下第三方组件。我们已尽力以最克制、最不侵犯隐私的方式进行配置。

### 6.1 Google AdMob（广告）

本应用通过 Google AdMob 展示横幅广告与插页广告,以支持应用的免费提供。

- **仅投放非个性化广告(Non-Personalized Ads)。** 我们在所有广告请求中强制设置 `nonPersonalizedAds = true`,即广告**不基于你的个人兴趣画像**,仅可能根据上下文等粗略信息投放。
- **iOS:不弹出 ATT(App Tracking Transparency)追踪许可弹窗。** 因为我们不进行跨应用 / 跨网站追踪。本应用的 iOS 隐私清单中 `NSPrivacyTracking` 标记为 `false`,所声明的「收集数据类型」为空。
- **iOS:SKAdNetwork 归因。** 我们在 iOS 上支持 SKAdNetwork——这是 Apple 提供的**保护隐私的广告归因机制**,用于在**不识别个人**的前提下衡量广告效果(例如广告安装转化)。它由 Apple 居中处理,不会向我们或广告方暴露你的身份。
- **Android:已剥离广告标识符相关权限。** 为贯彻「不追踪」原则,我们已在 Android 清单中**移除**广告 ID 及相关权限(`com.google.android.gms.permission.AD_ID`、`ACCESS_ADSERVICES_AD_ID`、`ACCESS_ADSERVICES_ATTRIBUTION`、`ACCESS_ADSERVICES_TOPICS`)。

广告由 Google 作为独立的数据控制者提供,展示广告过程中 Google 可能处理有限的设备 / 网络信息(如粗略 IP、设备类型)以投放和计量广告。请参阅 Google 的隐私政策了解其数据处理:
https://policies.google.com/privacy
以及 Google 如何在其服务中使用数据:
https://policies.google.com/technologies/partner-sites

### 6.2 Google Firebase（仅核心组件）

本应用仅集成 **Firebase Core(`firebase_core`)** 用于基础初始化。

- **我们未启用 Firebase Analytics、未启用 Crashlytics,也未启用任何会收集用户数据或使用统计的 Firebase 子模块。**
- Firebase Core 本身不收集你的个人数据,也不会上传你的照片或使用行为。
- Firebase 初始化失败时,不影响本应用的核心清理功能。

如需了解 Firebase 的数据实践,请参阅:https://firebase.google.com/support/privacy

### 6.3 穿山甲 / Pangle（未集成)

当前发布版本**未集成**穿山甲 / Pangle 广告 SDK——其代码与依赖均已从本应用中移除,**不会运行,也不会收集或传输任何数据**。若未来版本(例如面向中国大陆应用商店的单独版本)集成该 SDK,我们将在发布前更新本隐私政策,并相应说明其数据处理方式。

### 第三方汇总表

| SDK | 用途 | 是否启用 | 是否收集可识别个人的数据 |
|---|---|---|---|
| Google AdMob | 展示非个性化广告 | 是 | 否(仅非个性化 + SKAdNetwork 归因) |
| Google Firebase Core | 基础初始化 | 是(仅 Core) | 否 |
| 穿山甲 / Pangle | 广告 | **否(未集成)** | 不适用 |

---

## 7. 儿童隐私

本应用并非面向 13 周岁(或你所在司法辖区规定的相应年龄)以下的儿童设计,我们不会有意收集儿童的个人信息。由于本应用本身不收集个人身份信息、不设账号、不进行行为追踪,因此不会专门面向儿童收集数据。若你认为有儿童在未经监护人同意的情况下向本应用提供了信息,请通过第 11 节的联系方式与我们联系。

---

## 8. 数据留存

- **服务端留存:无。** 我们没有服务器,因此不在任何后端留存你的任何数据。
- **设备本地留存:** 暂存箱条目、应用设置等本地数据保存在你的设备上,直到你将其清空、恢复、或卸载本应用。
- **照片 / 视频:** 始终由你掌控,保存在你的系统相册中;经你最终确认删除的项目会被系统永久移除(不可逆)。

---

## 9. 你的权利与控制

由于数据均在本地,你对自己的数据拥有完全、直接的控制权:

- **撤销相册权限:** 可随时在 iOS / Android 系统设置中撤销或调整(如改为「部分照片」)本应用的相册访问权限。
- **恢复误删:** 在最终确认删除前,可从暂存箱恢复任何项目。
- **清除本地数据:** 卸载本应用即可清除其在设备上保存的所有本地数据(设置、暂存箱引用等)。
- **退出个性化广告:** 本应用本就仅投放非个性化广告;你还可在系统级广告设置中进一步管理偏好。
- 视你所在地区的法律(如 GDPR、CCPA 等)你可能享有其他权利;但由于我们不持有你的个人数据,绝大多数请求可由你在设备本地直接完成。如有疑问可联系我们。

---

## 10. 政策变更

我们可能会不时更新本隐私政策(例如功能调整或启用新的第三方组件时)。更新后的版本将在应用内「隐私政策」页面发布,并更新顶部的「最近更新」日期。重大变更我们会通过应用内适当方式提示。继续使用本应用即表示你接受更新后的政策。

---

## 11. 联系我们

如对本隐私政策或你的隐私有任何疑问、意见或请求,请联系:

- 开发者 / Developer: ZTIDAL
- 邮箱 / Email: 494485959@qq.com

---
---

# English Version

## Introduction

**Local Photo Cleanup** (the "App") is a **privacy-first** photo cleaning tool. Our core promise is:

> **Your photos never leave your phone · 100% on-device · 0 uploads**

The App helps you find old screenshots, similar photos, blurry shots, and space-hogging large videos so that you can clean them up and free storage. **All analysis, comparison, and recognition of your photos and videos happens entirely on your device, locally. Nothing is ever uploaded to any server, and nothing ever leaves your phone.**

We have no servers, no accounts, and no cloud storage. We cannot see, collect, or access your photos.

This Privacy Policy explains how the App handles information and applies to both iOS and Android. Please read it before using the App.

---

## 1. What We Collect / Do Not Collect

### We do not collect any personal information

- **We do not collect your photos or videos.** They are only read and analyzed locally on your device — never uploaded, never transmitted off the device.
- **We do not collect your name, email, phone number, location, or any account information.** No sign-up or login is required.
- **We do not collect identifiers used to identify you** (see Section 6 regarding advertising).
- **We do not build user profiles and do not perform cross-app / cross-site behavioral tracking.**
- **We (the developer) retain no user data on any server of ours — because we have no server.**

### Data that exists only locally on your device

To deliver core functionality, the following data is **stored only on your device** and is never sent to us or any third party:

| Data | Purpose | Where it is stored |
|---|---|---|
| Photo / video content in your library | Local identification of cleanable items (see Sections 2, 3) | Always remains in your photo library; the App only analyzes it transiently in memory |
| Staging-bin entries (references to items pending deletion: library asset ID, category, timestamp, file size) | A safety buffer before deletion, enabling restore (see Section 4) | Local on-device storage |
| App settings and preferences (language, dark mode, protection rules, whether items go to the staging bin by default, etc.) | To remember your choices | Locally on the device (the system's local key-value store, `shared_preferences`) |

None of this leaves the device, and it is removed when you uninstall the App (except for photos you have confirmed for deletion, which is an irreversible system operation).

---

## 2. On-Device Processing

All "smart" analysis in the App runs entirely on your device, fully offline. **No internet connection is required to analyze your photos.** This includes:

- **Perceptual hashing** — to find similar / duplicate photos;
- **Laplacian blur detection** — to identify blurry shots;
- **QR / barcode recognition** (`flutter_zxing`, a locally compiled ZXing C++ core) — applied only to screenshots, used for features such as "protect screenshots that contain a QR code." **It downloads no models, makes no network calls, and uses no cloud recognition service;**
- **Metadata-based filtering** — such as a screenshot's capture date or a video's file size.

These computations run in background isolates. During processing, photo data exists only briefly in device memory and is released when analysis completes. **Nothing is written to external storage and nothing is sent over the network.**

---

## 3. Photo Library Access and Its Purpose

To help you find cleanable photos and videos, the App needs access to your device's photo library.

**The sole purpose for which we request photo access is to read and analyze your photos / videos locally on your device, in order to identify cleanable items (old screenshots, similar photos, blurry photos, large videos).**

- **iOS:** We request Photos access (`NSPhotoLibraryUsageDescription`) to read your library for local analysis; when you confirm a deletion, we request add/write access (`NSPhotoLibraryAddUsageDescription`) to perform it. You may grant access to **selected photos only**, in which case the App analyzes only what you choose.
- **Android:** We request `READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO` (and `READ_EXTERNAL_STORAGE` on older systems) to read your library. `ACCESS_MEDIA_LOCATION` is used to correctly process images when reading media (e.g., preserving original metadata); **we do not collect or upload your location.**

**Deletion is always initiated and confirmed by you.** The App never deletes any photo or video without your explicit confirmation. Deletion is a standard operation performed through the system photo library interface.

---

## 4. Staging Bin (Safety Buffer Before Deletion)

To prevent accidental deletion, the App provides a "staging bin":

- When you choose to clean certain photos / videos, they **first go into the staging bin** rather than being permanently deleted immediately;
- You can **restore** items from the staging bin at any time;
- The staging bin is **stored entirely on your device** (persisted in local storage so that it survives an app restart). It holds only reference information about pending items (library asset ID, category, time added, file size) — **the photos themselves are not copied and not uploaded**;
- Only after you **finally confirm deletion** does the App perform the actual deletion via the system interface. **Actual deletion is irreversible**, so please review carefully before final confirmation.

---

## 5. Network and Servers

- The App **has no backend server of its own** and **does not upload** your photos, videos, or any personal data.
- The App's core cleanup functionality is **fully offline** and works without an internet connection.
- The only situation that produces a network connection is the third-party advertising SDK described in Section 6 (to fetch ads). Apart from that, the App does not initiate any network transmission involving user data.

---

## 6. Third-Party SDKs and Their Data Handling

The App integrates the following third-party components, configured in the most restrictive, least privacy-invasive way we can.

### 6.1 Google AdMob (Advertising)

The App shows banner and interstitial ads via Google AdMob to support offering the App for free.

- **Non-personalized ads only.** We force `nonPersonalizedAds = true` on every ad request, meaning ads are **not based on a profile of your personal interests** and may only use coarse signals such as context.
- **iOS: no ATT (App Tracking Transparency) prompt.** Because we do not perform cross-app / cross-site tracking, the App's iOS privacy manifest marks `NSPrivacyTracking` as `false` and declares an **empty** set of collected data types.
- **iOS: SKAdNetwork attribution.** On iOS we support SKAdNetwork — Apple's **privacy-preserving ad attribution** mechanism that measures ad performance (e.g., install conversions) **without identifying you as an individual.** It is mediated by Apple and does not expose your identity to us or to advertisers.
- **Android: ad-identifier permissions stripped.** To honor our "no tracking" stance, we **remove** the advertising-ID and related permissions from the Android manifest (`com.google.android.gms.permission.AD_ID`, `ACCESS_ADSERVICES_AD_ID`, `ACCESS_ADSERVICES_ATTRIBUTION`, `ACCESS_ADSERVICES_TOPICS`).

Ads are served by Google as an independent data controller. In serving ads, Google may process limited device / network information (such as coarse IP and device type) to deliver and measure ads. Please see Google's privacy policy for its data handling:
https://policies.google.com/privacy
and how Google uses data in its services:
https://policies.google.com/technologies/partner-sites

### 6.2 Google Firebase (Core Only)

The App integrates **only Firebase Core (`firebase_core`)** for basic initialization.

- **We have not enabled Firebase Analytics, have not enabled Crashlytics, and have not enabled any Firebase module that collects user data or usage statistics.**
- Firebase Core itself does not collect your personal data and does not upload your photos or usage behavior.
- If Firebase initialization fails, the App's core cleanup functionality is unaffected.

For Firebase's data practices, see: https://firebase.google.com/support/privacy

### 6.3 Pangle (穿山甲) — Not Integrated

The current released version **does not integrate** the Pangle ad SDK — its code and dependencies have been removed from the App. **It does not run and does not collect or transmit any data.** If a future version (for example, a separate build for mainland-China app stores) integrates this SDK, we will update this Privacy Policy before release and describe its data handling accordingly.

### Third-Party Summary

| SDK | Purpose | Enabled | Collects personally identifiable data |
|---|---|---|---|
| Google AdMob | Show non-personalized ads | Yes | No (non-personalized + SKAdNetwork attribution only) |
| Google Firebase Core | Basic initialization | Yes (Core only) | No |
| Pangle (穿山甲) | Advertising | **No (not integrated)** | N/A |

---

## 7. Children's Privacy

The App is not designed for children under 13 (or the corresponding age in your jurisdiction), and we do not knowingly collect personal information from children. Because the App itself collects no personally identifying information, has no accounts, and performs no behavioral tracking, it does not collect data from children in any targeted way. If you believe a child has provided information to the App without guardian consent, please contact us using Section 11.

---

## 8. Data Retention

- **Server-side retention: none.** We have no servers and therefore retain none of your data on any backend.
- **On-device retention:** Local data such as staging-bin entries and app settings is kept on your device until you clear it, restore it, or uninstall the App.
- **Photos / videos:** Always under your control, kept in your system photo library; items you finally confirm for deletion are permanently removed by the system (irreversible).

---

## 9. Your Rights and Controls

Because data stays local, you have full, direct control over your own data:

- **Revoke photo access:** You can revoke or adjust the App's photo access at any time in iOS / Android system settings (e.g., switch to "selected photos").
- **Restore deletions:** Before final confirmation, you can restore any item from the staging bin.
- **Clear local data:** Uninstalling the App clears all local data it stored on your device (settings, staging-bin references, etc.).
- **Opt out of personalized ads:** The App already serves non-personalized ads only; you may further manage preferences in system-level ad settings.
- Depending on your region's laws (e.g., GDPR, CCPA), you may have additional rights; however, since we do not hold your personal data, you can carry out the vast majority of such requests directly on your device. Contact us with any questions.

---

## 10. Changes to This Policy

We may update this Privacy Policy from time to time (for example, when features change or a new third-party component is enabled). The updated version will be published on the in-app "Privacy Policy" page, with the "Last updated" date at the top revised. We will signal material changes through appropriate in-app means. Your continued use of the App constitutes acceptance of the updated policy.

---

## 11. Contact Us

If you have any questions, comments, or requests regarding this Privacy Policy or your privacy, please contact:

- Developer: ZTIDAL
- Email: 494485959@qq.com
