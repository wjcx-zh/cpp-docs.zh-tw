---
title: 'C/c + + 專案屬性 (Visual Studio) '
description: Visual Studio Microsoft C/c + + 專案屬性頁屬性的參考指南。
ms.date: 09/03/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: a96400e27b48b734d4002d9cef13fd52f9ccc7a5
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609165"
---
# <a name="cc-property-pages"></a>C/c + + 屬性頁

下列屬性頁位於**專案**  >  **屬性**[設定  >  **屬性**  >  **C/c + +**：

## <a name="cc-general-properties"></a>C/c + + 一般屬性

### <a name="additional-include-directories"></a>其他 Include 目錄

指定一或多個要加入 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。 將[ `/I` (其他 include 目錄) ](i-additional-include-directories.md)。

### <a name="additional-using-directories"></a>其他 #using 目錄

指定一或多個目錄， (以分號分隔的目錄名稱) 要搜尋的名稱，以解析傳遞給 #using 指示詞的名稱。 集合 [`/AI`](ai-specify-metadata-directories.md) 。

### <a name="debug-information-format"></a>偵錯資訊格式

指定編譯器所產生的偵錯資訊類型。  此屬性需要相容的連結器設定。 設定[ `/Z7` `/Zi`) 的 `/ZI` (Debug 資訊格式](z7-zi-zi-debug-information-format.md)。

#### <a name="choices"></a>Choices

- **無** - 因為不產生任何偵錯資訊，所以編譯速度會較快。
- **C7 相容** -選取為您的程式建立的偵錯工具類型，以及此資訊是否保留在物件 ( .obj) 檔案或程式資料庫 (PDB) 。
- **程式資料庫** -產生程式資料庫 (PDB) ，其中包含用於偵錯工具的類型資訊和符號調試資訊。 符號的調試資訊包括變數和函式的名稱和類型，以及行號。
- [編輯後繼續] 的**程式資料庫**-以支援 [[編輯後繼續](/visualstudio/debugger/edit-and-continue)] 功能的格式產生程式資料庫（如前文所述）。

### <a name="support-just-my-code-debugging"></a>支援 Just My Code 的調試

加入支援的程式碼，以在這個編譯單位中啟用 [Just My Code](/visualstudio/debugger/just-my-code) 的偵錯工具。 集合 [`/JMC`](jmc.md) 。

### <a name="common-language-runtime-support"></a>Common Language RunTime 支援

使用 .NET 執行時間服務。  此參數與其他一些參數不相容;如需詳細資訊，請參閱交換器系列上的檔 [`/clr`](clr-common-language-runtime-compilation.md) 。

#### <a name="choices"></a>Choices

- **無通用語言執行時間支援** -不支援 Common language runtime
- **Common Language RunTime 支援** -為您的應用程式建立可供其他 CLR 應用程式使用的中繼資料。 也可讓您的應用程式使用其他 CLR 元件之中繼資料內的類型和資料。
- **純 Msil Common Language RunTime 支援** -產生僅限 [msil](/dotnet/standard/managed-code)的輸出檔案，沒有原生可執行程式碼，但它可以包含編譯成 msil 的原生類型。
- **SAFE Msil Common Language RunTime 支援** -產生純 msil (沒有原生可執行程式碼) 和可驗證的輸出檔。

### <a name="consume-windows-runtime-extension"></a>使用 Windows 執行階段擴充功能

使用 Windows 執行時間語言擴充功能。 集合 [`/ZW`](zw-windows-runtime-compilation.md) 。

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

當編譯器在編譯期間啟動和顯示資訊訊息時，抑制登入橫幅的顯示。

### <a name="warning-level"></a>警告層級

選取您希望編譯器針對程式碼錯誤所產生的嚴謹度等級。 集合 [`/W0` - `/W4`](compiler-option-warning-level.md) 。

#### <a name="choices"></a>Choices

- 關閉**所有警告**-層級0會停用所有警告。
- 等級**1-層級 1**會顯示嚴重警告。 層級1是命令列的預設警告層級。
- 層級 2-層級2顯示所有層級1警告和**警告的嚴重性**低於層級1。
- 層級**3-層級 3**會顯示所有層級2警告和針對生產用途建議的所有其他警告。
- **Level4** 層級4會顯示所有層級3警告以及參考用警告，在大部分情況下都可以安全地忽略。
- **警告** -啟用所有警告，包括預設為停用的警告。

### <a name="treat-warnings-as-errors"></a>將警告視為錯誤

將編譯器警告視為錯誤。 針對新專案，最好 [`/WX`](wx-treat-linker-warnings-as-errors.md) 在每次編譯時使用。 解決所有警告，以將難以發現的程式碼缺失降至最低。

### <a name="warning-version"></a>警告版本

隱藏特定編譯器版本之後引進的警告。 集合 [`/Wv:xx[.yy[.zzzzz]]`](wx-treat-linker-warnings-as-errors.md) 。

### <a name="diagnostics-format"></a>診斷格式

使用診斷訊息中的資料行資訊和來源內容，啟用豐富的診斷功能。

#### <a name="choices"></a>Choices

- **插入** 點-提供診斷訊息中的資料行資訊。 然後，輸出具有表示違規資料行之插入號的相關源程式碼。
- 資料行**資訊**-另外提供發出診斷的行中的資料行編號（如果適用）。
- **傳統** -只輸出具有行號的先前、簡潔的診斷訊息。

### <a name="sdl-checks"></a>SDL 檢查

額外的安全性開發生命週期 (SDL) 建議的檢查;包括啟用額外的安全程式碼產生功能，以及將額外的安全性相關警告視為錯誤。 設定[ `/sdl` 、 `/sdl-` ](sdl-enable-additional-security-checks.md)。

### <a name="multi-processor-compilation"></a>多處理器編譯

多處理器編譯。

## <a name="cc-optimization-properties"></a>C/c + + 優化屬性

### <a name="optimization"></a>Optimization

程式碼優化的選取選項;選擇 [自訂] 以使用特定的優化選項。 設定 [`/Od`](od-disable-debug.md) 、 [ `/O1` 、 `/O2` ](o-options-optimize-code.md)。

#### <a name="choices"></a>Choices

- **自訂** - 自訂最佳化。
- **停用** - 停用最佳化。
- **最大優化 (偏好大小) ** -等於 **`/Os /Oy /Ob2 /Gs /GF /Gy`**
- **最大優化 (偏好速度) ** -相當於 **`/Oi /Ot /Oy /Ob2 /Gs /GF /Gy`**
- **優化 (優選速度) ** -相當於 **`/Oi /Ot /Oy /Ob2`**

### <a name="inline-function-expansion"></a>內嵌函式展開

選取組建的 [內嵌](../../cpp/inline-functions-cpp.md) 函式展開層級。 集合 [`/Ob`](ob-inline-function-expansion.md) 。

#### <a name="choices"></a>Choices

- **預設值**
- **Disabled** -停用內嵌展開（預設為開啟）。
- **只有 __inline** -只展開標記為、或的函式 **`inline`** **`__forceinline`** **`__inline`** 。 或者，在類別宣告中定義的 c + + 成員函式中。
- **任何適合** 擴充的函式，標記為 **`inline`** 或， **`__inline`** 以及編譯器選擇的任何其他功能。  (展開是編譯器的判斷，通常稱為 *自動內嵌*。 ) 

### <a name="enable-intrinsic-functions"></a>啟用內建函式

啟用內建函式。  使用內建函式會產生更快但可能較大的程式碼。 集合 [`/Oi`](oi-generate-intrinsic-functions.md) 。

### <a name="favor-size-or-speed"></a>偏好大小或速度

是否偏好程式碼大小或程式碼速度;必須開啟 [全域優化]。 設定[ `/Ot` 、 `/Os` ](os-ot-favor-small-code-favor-fast-code.md)。

#### <a name="choices"></a>Choices

- 偏好**小型程式碼**-藉由指示編譯器偏好較快速的大小，將 Exe 和 dll 的大小降至最低。
- 偏好**快速程式碼**-藉由指示編譯器偏好較大的速度來充分發揮 Exe 和 dll 的速度。  (此值為預設值。 ) 
- **不是-沒有** 大小和速度優化。

### <a name="omit-frame-pointers"></a>省略框架指標

在呼叫堆疊上隱藏框架指標的建立。

### <a name="enable-fiber-safe-optimizations"></a>啟用光纖安全優化

使用纖維和執行緒本機存放區存取時，啟用記憶體空間優化。 集合 [`/GT`](gt-support-fiber-safe-thread-local-storage.md) 。

### <a name="whole-program-optimization"></a>整個程式最佳化

藉由將程式碼產生延遲至連結時間，來啟用跨模組優化。 需要連結器選項 **連結時間程式碼產生**。 集合 [`/GL`](gl-whole-program-optimization.md) 。

## <a name="cc-preprocessor-properties"></a>C/c + + 預處理器屬性

### <a name="preprocessor-definitions"></a>前置處理器定義

定義原始程式檔的前置處理符號。

### <a name="undefine-preprocessor-definitions"></a>取消前置處理器的定義

指定取消一或多個前置處理器的定義。 集合 [`/U`](u-u-undefine-symbols.md) 。

### <a name="undefine-all-preprocessor-definitions"></a>取消所有前置處理器的定義

取消所有先前定義的前置處理器值。 集合 [`/u`](u-u-undefine-symbols.md) 。

### <a name="ignore-standard-include-paths"></a>忽略標準 Include 路徑

防止編譯器搜尋 INCLUDE 環境變數中指定之目錄內的 include 檔。

### <a name="preprocess-to-a-file"></a>前置處理至檔案

預先處理 C 和 c + + 原始檔，並將前置處理過的輸出寫入檔案。 此選項會隱藏編譯，而且不會產生檔案 *`.obj`* 。

### <a name="preprocess-suppress-line-numbers"></a>前置處理隱藏行號

不 #line 指示詞的前置處理。

### <a name="keep-comments"></a>保留留言

從原始程式碼隱藏批註帶;需要至少設定一個前置**處理選項。** 集合 [`/C`](c-preserve-comments-during-preprocessing.md) 。

## <a name="cc-code-generation-properties"></a>C/c + + 程式碼產生屬性

### <a name="enable-string-pooling"></a>啟用字串共用

編譯器只會在程式映射中建立一個相同字串的唯讀複本。 它會產生較小的程式，也就是稱為「 *字串*共用」的優化。 [ `/O1` 、 `/O2` ](o-options-optimize-code.md)和 [`/ZI`](z7-zi-zi-debug-information-format.md) 自動設定 [`/GF`](gf-eliminate-duplicate-strings.md) 選項。

### <a name="enable-minimal-rebuild"></a>啟用最少重建

啟用基本重建，以決定是否要重新編譯 c + + 原始程式檔，其中包含已變更的 c + + 類別定義，並儲存在頭 *`.h`* 檔中。

### <a name="enable-c-exceptions"></a>啟用 C++ 例外狀況

指定編譯器所使用的例外狀況處理模型。

#### <a name="choices"></a>Choices

- **是，使用 SEH 例外** 狀況-攔截非同步 (結構化) 和同步 (c + +) 例外狀況的例外狀況處理模型。 集合 [`/EHa`](eh-exception-handling-model.md) 。
- **是** -只會攔截 c + + 例外狀況的例外狀況處理模型，並告知編譯器假設 extern c 函數永遠不會擲回 c + + 例外狀況。 集合 [`/EHsc`](eh-exception-handling-model.md) 。
- **是，使用 Extern c 函數** -只會攔截 c + + 例外狀況的例外狀況處理模型，並告知編譯器假設 Extern c 函式確實擲回例外狀況。 集合 [`/EHs`](eh-exception-handling-model.md) 。
- **No** -無例外狀況處理。

### <a name="smaller-type-check"></a>較小的類型檢查

啟用檢查轉換成較小的類型，與 debug 以外的任何優化類型不相容。 集合 [`/RTCc`](rtc-run-time-error-checks.md) 。

### <a name="basic-runtime-checks"></a>基本執行時間檢查

啟用基本的執行階段錯誤檢查，與 debug 以外的任何優化類型不相容。 設定[ `/RTCs` 、 `/RTCu` 、 `/RTC1` ](rtc-run-time-error-checks.md)。

#### <a name="choices"></a>Choices

- **堆疊框架** -啟用堆疊框架執行階段錯誤檢查。
- **未** 初始化的變數-使用未初始化的變數時報告。
- ** (/rtc1，HTTP-equiv，以/RTCsu) 對 ** 等專案 **`/RTCsu`** 。
- **預設** 值-預設執行時間檢查。

### <a name="runtime-library"></a>執行階段程式庫

指定連結的執行階段程式庫。 設定[ `/MT` 、 `/MTd` 、 `/MD` 、 `/MDd` ](md-mt-ld-use-run-time-library.md)。

#### <a name="choices"></a>Choices

- **多執行緒** -會導致您的應用程式使用多執行緒、靜態版本的執行時間程式庫。
- **多執行緒的 Debug** -定義 _DEBUG 和 _MT。 此選項也會讓編譯器將程式庫名稱 *libcmtd.lib* 放入檔案中， *`.obj`* 讓連結器使用 *libcmtd.lib* 來解析外部符號。
- **多執行緒 DLL** -會導致您的應用程式使用多執行緒和 DLL 特定版本的執行時間程式庫。 定義 `_MT` 和 `_DLL` ，並讓編譯器將程式庫名稱 *msvcrt.lib* 放入檔案中 *`.obj`* 。
- **多執行緒的偵錯工具 DLL** -定義 `_DEBUG` 、和， `_MT` `_DLL` 並讓您的應用程式使用多執行緒和 DLL 特定版本的執行時間程式庫。 它也會讓編譯器將程式庫名稱 *msvcrtd.lib* 放入檔案中 *`.obj`* 。

### <a name="struct-member-alignment"></a>結構成員對齊

指定結構成員對齊的1、2、4或8位元組界限。 集合 [`/Zp`](zp-struct-member-alignment.md) 。

#### <a name="choices"></a>Choices

- **1 位元組** 封裝的1位元組套件結構。 與相同 **`/Zp`** 。
- 2**位元組**：在2位元組界限上封裝結構。
- 4**位元組**-在4位元組界限上封裝結構。
- 8**個位元組**-在8位元組界限上封裝結構 (預設) 。
- **16 位元組： 16** 位元組界限上的套件結構。
- **預設** 值-預設對齊設定。

### <a name="security-check"></a>安全性檢查

安全性檢查可協助偵測是否發生堆疊緩衝區滿溢的情況，這是駭客經常嘗試攻擊的程式安全性漏洞。

#### <a name="choices"></a>Choices

- **停用安全性檢查** - 停用安全性檢查。 集合 [`/GS-`](gs-buffer-security-check.md) 。
- **啟用安全性檢查** - 啟用安全性檢查。 集合 [`/GS`](gs-buffer-security-check.md) 。

### <a name="control-flow-guard"></a>控制流程防護

Guard 安全性檢查有助於偵測到不合法的程式碼區塊的嘗試。

#### <a name="choices"></a>Choices

- **是** -啟用防護集的安全性檢查 [`/guard:cf`](guard-enable-control-flow-guard.md) 。
- **否**

### <a name="enable-function-level-linking"></a>啟用函式階層連結

允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。 需要此項目才能使用編輯後繼續功能。 集合 [`/Gy`](gy-enable-function-level-linking.md) 。

### <a name="enable-parallel-code-generation"></a>啟用平行程式碼產生

允許編譯器在啟用優化時，產生使用所識別之迴圈的平行程式碼 `#pragma loop(hint_parallel[(n)])` 。

### <a name="enable-enhanced-instruction-set"></a>啟用增強的指令集

啟用在支援增強指令集的處理器上找到的指示。 例如，SSE、SSE2、AVX 和 AVX2 的增強功能為 IA-32。 以及 x64 的 AVX 和 AVX2 增強功能。 目前 **`/arch:SSE`** 和 **`/arch:SSE2`** 僅適用于 x86 架構的建立。 如果未指定任何選項，編譯器將會使用在支援 SSE2 的處理器上找到的指示。 您可以使用來停用增強的指令 **`/arch:IA32`** 。 如需詳細資訊，請參閱 [`/arch (x86)`](arch-x86.md) 、 [`/arch (x64)`](arch-x64.md) 和 [`/arch (ARM)`](arch-arm.md) 。

#### <a name="choices"></a>Choices

- **Streaming SIMD Extensions** -Streaming SIMD Extensions。 集  **`/arch:SSE`**
- **Streaming SIMD Extensions 2** -Streaming SIMD Extensions 2。 集  **`/arch:SSE2`**
- **先進向量擴充** 功能-Advanced vector extensions。 集  **`/arch:AVX`**
- **Advanced Vector extensions 2** -Advanced vector extensions 2。 集  **`/arch:AVX2`**
- **沒有增強的指示** -沒有增強的指示。 集  **`/arch:IA32`**
- **未設定** -未設定。

### <a name="floating-point-model"></a>浮動點模型

設定浮點模型。 設定[ `/fp:precise` 、 `/fp:strict` 、 `/fp:fast` ](fp-specify-floating-point-behavior.md)。

#### <a name="choices"></a>Choices

- **精確** -預設值。 改善浮點測試是否相等和不相等的一致性。
- **Strict** -最嚴格的浮點模型。 **`/fp:strict`** 導致 **`fp_contract`** 關閉並 **`fenv_access`** 開啟。 **`/fp:except`** 是隱含的，而且可以藉由明確指定來停用 **`/fp:except-`** 。 搭配使用時 **`/fp:except-`** ， **`/fp:strict`** 會強制執行嚴格的浮點語義，但不會考慮到例外狀況事件。
- 在大部分的案例中**快速**建立最快的程式碼。

### <a name="enable-floating-point-exceptions"></a>啟用浮點例外狀況

可靠的浮點例外狀況模型。 觸發之後，將會立即引發例外狀況。 集合 [`/fp:except`](fp-specify-floating-point-behavior.md) 。

### <a name="create-hotpatchable-image"></a>建立可線上修補映射

當您開啟熱修補功能時，編譯器會確保每個函式的第一個指令是兩個位元組，視需要進行熱修補。 集合 [`/hotpatch`](hotpatch-create-hotpatchable-image.md) 。

### <a name="spectre-mitigation"></a>Spectre 緩和

Spectre CVE 2017-5753 的緩和措施。 集合 [`/Qspectre`](qspectre.md) 。

#### <a name="choices"></a>Choices

- **已啟用** -啟用 CVE 2017-5753 的 Spectre 緩和功能
- **停用** -未設定。

## <a name="cc-language-properties"></a>C/c + + 語言屬性

### <a name="disable-language-extensions"></a>停用語言擴充功能

隱藏或啟用語言延伸模組。 集合 [`/Za`](za-ze-disable-language-extensions.md) 。

### <a name="conformance-mode"></a>一致性模式

啟用或隱藏一致性模式。 集合 [`/permissive-`](permissive-standards-conformance.md) 。

### <a name="treat-wchar_t-as-built-in-type"></a>將 wchar_t 視為內建類型

當指定時，類型 **`wchar_t`** 會變成對應至的原生類型，與 **`__wchar_t`** 對應的方式相同 **`short`** **`__int16`** 。 [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) 預設為開啟。

### <a name="force-conformance-in-for-loop-scope"></a>在 For 迴圈範圍中強制執行一致性

使用 Microsoft 擴充功能來執行語句迴圈的標準 c + + 行為 `for` 。 設定[ `/Za` ， `/Ze` (停用語言擴充](za-ze-disable-language-extensions.md)功能。 [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) 預設為開啟。

### <a name="remove-unreferenced-code-and-data"></a>移除未參考的程式碼和資料

若有指定，編譯器就不會再產生未參考程式碼和資料的符號資訊。

### <a name="enforce-type-conversion-rules"></a>強制型別轉換規則

用來根據 c + + 11 標準，將右值參考型別識別為轉換運算的結果。

### <a name="enable-run-time-type-information"></a>啟用執行階段類型資訊

加入程式碼，以便在執行時間檢查 c + + 物件類型 (*執行時間類型資訊*或 RTTI) 。 設定[ `/GR` 、 `/GR-` ](gr-enable-run-time-type-information.md)。

### <a name="open-mp-support"></a>Open MP 支援

啟用 OpenMP 2.0 語言延伸模組。 集合 [`/openmp`](openmp-enable-openmp-2-0-support.md) 。

### <a name="c-language-standard"></a>C + + 語言標準

判斷編譯器所啟用的 c + + 語言標準。 可能的話，請使用最新版本。 設定[ `/std:c++14` 、 `/std:c++17` 、 `/std:c++latest` ](std-specify-language-standard-version.md)。

#### <a name="choices"></a>Choices

- **預設值**
- **ISO c + + 14 標準**
- **ISO c + + 17 標準**
- **預覽-最新 c + + 工作草稿的功能**

### <a name="enable-c-modules-experimental"></a>啟用 c + + 模組 (實驗性) 

C + + 模組 TS 和標準程式庫模組的實驗性支援。

## <a name="cc-precompiled-headers-properties"></a>C/c + + 先行編譯頭檔案屬性

### <a name="createuse-precompiled-header"></a>建立/使用先行編譯標頭檔

啟用在建置期間建立或使用先行編譯標頭檔。 設定 [`/Yc`](yc-create-precompiled-header-file.md) 、 [`/Yu`](yu-use-precompiled-header-file.md) 。

#### <a name="choices"></a>Choices

- **Create** -指示編譯器建立先行編譯頭 *`.pch`* 檔 () 檔，該檔案代表特定時間點的編譯狀態。
- **Use** -指示編譯器 *`.pch`* 在目前的編譯中使用現有的先行編譯標頭檔 () 檔。
- **不使用** 先行編譯的標頭-不使用先行編譯標頭檔。

### <a name="precompiled-header-file"></a>先行編譯標頭檔

指定建立或使用先行編譯標頭檔時要使用的標頭檔名稱。 設定 [`/Yc`](yc-create-precompiled-header-file.md) 、 [`/Yu`](yu-use-precompiled-header-file.md) 。

### <a name="precompiled-header-output-file"></a>先行編譯標頭檔輸出檔

指定所產生之先行編譯標頭檔的路徑或名稱。 集合 [`/Fp`](fp-name-dot-pch-file.md) 。

## <a name="cc-output-files-properties"></a>C/c + + 輸出檔屬性

### <a name="expand-attributed-source"></a>展開屬性化來源

建立清單檔，其展開的屬性會插入原始檔中。 集合 [`/Fx`](fx-merge-injected-code.md) 。

### <a name="assembler-output"></a>組合語言輸出

指定組合語言輸出檔案的內容。 設定[ `/FA` 、 `/FAc` 、 `/FAs` 、 `/FAcs` ](fa-fa-listing-file.md)。

#### <a name="choices"></a>Choices

- **無清單** -沒有清單。
- **僅限元件清單** -元件碼; *`.asm`*
- **具有電腦程式代碼的元件** -電腦和元件程式碼; *`.cod`*
- **具有原始程式碼的元件** ：來源和程式碼; *`.asm`*
- **元件、機器碼和來源** 元件、電腦程式代碼和原始程式碼; *`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>使用 Unicode 進行組合語言清單

導致以 UTF-8 格式建立輸出檔。

### <a name="asm-list-location"></a>ASM 清單位置

指定 ASM 清單檔的相對路徑或名稱;可以是檔案或目錄名稱。 集合 [`/Fa`](fa-fa-listing-file.md) 。

### <a name="object-file-name"></a>物件檔案名稱

指定要覆寫預設物件檔案名稱的名稱；可以是檔案或目錄名稱。 集合 [`/Fo`](fo-object-file-name.md) 。

### <a name="program-database-file-name"></a>程式資料庫檔案名

指定編譯器產生之 PDB 檔的名稱;也會指定所需編譯器產生之 .IDB 檔案的基底名稱;可以是檔案或目錄名稱。 集合 [`/Fd`](fd-program-database-file-name.md) 。

### <a name="generate-xml-documentation-files"></a>產生 XML 檔檔案

指定編譯器應產生 XML 檔批註檔案 (。) 的 .XDC。 集合 [`/doc`](doc-process-documentation-comments-c-cpp.md) 。

### <a name="xml-documentation-file-name"></a>XML 檔檔案名

指定所產生之 XML 檔檔案的名稱;可以是檔案或目錄名稱。 集合 [`/doc:`\<name>](doc-process-documentation-comments-c-cpp.md) 。

## <a name="cc-browse-information-properties"></a>C/c + + 流覽資訊屬性

### <a name="enable-browse-information"></a>啟用流覽資訊

指定檔案中流覽資訊的層級 *`.bsc`* 。 集合 [`/FR`](fr-fr-create-dot-sbr-file.md) 。

### <a name="browse-information-file"></a>流覽資訊檔

指定瀏覽器資訊檔的選擇性名稱。 集合 [`/FR`\<name>](fr-fr-create-dot-sbr-file.md) 。

## <a name="cc-advanced-properties"></a>C/c + + Advanced 屬性

### <a name="calling-convention"></a>呼叫慣例

為您的應用程式選取預設的呼叫慣例， (可以由函式) 來覆寫。 設定[ `/Gd` 、 `/Gr` 、 `/Gz` 、 `/Gv` ](gd-gr-gv-gz-calling-convention.md)。

#### <a name="choices"></a>Choices

- **`__cdecl`** -指定 **`__cdecl`** 所有函數的呼叫慣例，但 c + + 成員函式和標記為或的函式除外 **`__stdcall`** **`__fastcall`** 。
- **`__fastcall`** -指定 **`__fastcall`** 所有函數的呼叫慣例，但 c + + 成員函式和標記為或的函式除外 **`__cdecl`** **`__stdcall`** 。 所有 **`__fastcall`** 函數都必須有原型。
- **`__stdcall`** -指定 **`__stdcall`** 所有函數的呼叫慣例，但 c + + 成員函式和標記為或的函式除外 **`__cdecl`** **`__fastcall`** 。 所有 **`__stdcall`** 函數都必須有原型。
- **`__vectorcall`** -指定 **`__vectorcall`** 所有函數的呼叫慣例，但 c + + 成員函式和標記為、或的函式除外 **`__cdecl`** **`__fastcall`** **`__stdcall`** 。 所有 **`__vectorcall`** 函數都必須有原型。

### <a name="compile-as"></a>編譯為

針對和檔案選取 [編譯語言] 選項 *`.c`* *`.cpp`* 。 設定[ `/TC` 、 `/TP` ](tc-tp-tc-tp-specify-source-file-type.md)。

#### <a name="choices"></a>Choices

- **預設** - 預設值。
- **編譯成 C 程式碼** - 編譯成 C 程式碼。
- **編譯為 c + + 程式碼** -編譯成 c + + 程式碼。

### <a name="disable-specific-warnings"></a>停用特定警告

停用指定的警告編號。 將警告號碼放在以分號分隔的清單中。 集合 [`/wd`\<number>](compiler-option-warning-level.md) 。

### <a name="forced-include-file"></a>強制的 Include 檔案

一或多個強制 Include 檔案。 集合 [`/FI`\<name>](fi-name-forced-include-file.md) 。

### <a name="forced-using-file"></a>強制 #using 檔案

指定一或多個強制的 #using 檔案。 集合 [`/FU`\<name>](fu-name-forced-hash-using-file.md) 。

### <a name="show-includes"></a>顯示 Include

產生 Include 檔清單以及編譯器輸出。 集合 [`/showIncludes`](showincludes-list-include-files.md) 。

### <a name="use-full-paths"></a>使用完整路徑

在診斷訊息中使用完整路徑。 集合 [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) 。

### <a name="omit-default-library-name"></a>省略預設程式庫名稱

不會在檔案中包含預設的程式庫名稱 *`.obj`* 。 集合 [`/Zl`](zl-omit-default-library-name.md) 。

### <a name="internal-compiler-error-reporting"></a>報告內部編譯器錯誤

> [!NOTE]
> 這個選項已被取代。 從 Windows Vista 開始，錯誤報表是由 [Windows 錯誤報告 (WER) ](/windows/win32/wer/windows-error-reporting) 設定來控制。

### <a name="treat-specific-warnings-as-errors"></a>將特定警告視為錯誤

將特定編譯器警告視為錯誤，其中 n 是編譯器警告。

### <a name="additional-options"></a>其他選項

其他選項。
