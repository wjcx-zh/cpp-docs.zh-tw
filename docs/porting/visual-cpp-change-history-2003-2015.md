---
title: Visual C++ 變更歷程記錄 2003 - 2015
ms.date: 08/30/2017
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 20920a5f1a1cdf2a4e10263a7b1de3010f24f9c0
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58329035"
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ 變更歷程記錄 2003 - 2015

這篇文章說明自 Visual Studio 2015 回溯到 Visual Studio 2003 的所有的重大變更，並會在文章中使用「新行為」或 「目前」表示 Visual Studio 2015 及更新版本。 「舊行為」與「過去」表示 Visual Studio 2013 及更舊版本。

如需 Visual Studio 2017 的資訊，請參閱 [Visual Studio 2017 中 Visual C++ 的新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)及[Visual Studio 2017 中 Visual C++ 的合規性改進](../cpp-conformance-improvements-2017.md)。

> [!NOTE]
> Visual Studio 2015 與 Visual Studio 2017 之間沒有二進位檔重大變更。

當您升級到新版 Visual Studio 時，先前正常編譯及執行的程式碼可能會發生編譯和 (或) 執行階段錯誤。 新版本中會造成這類問題的變更稱為 *「重大變更」*(Breaking Change)，在進行 C++ 語言標準、函式簽章或記憶體內部物件配置的修改時通常都會有重大變更。

為了避免發生難以偵測及診斷的執行階段錯誤，我們建議您絕不要以靜態方式連結至使用不同版本編譯器所編譯的二進位檔。 此外，當您升級 EXE 或 DLL 專案時，請務必也要升級它所連結的程式庫。 請勿在使用不同版本編譯器所編譯的二進位檔 (包括 DLL) 之間，傳遞 CRT (C 執行階段) 或 C++ 標準程式庫 (C++ 標準程式庫) 類型。 如需詳細資訊，請參閱[跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。

您絶對不要為不是 COM 介面或 POD 物件之物件撰寫依賴特定配置的程式碼。 如果您撰寫了這種程式碼，則必須確定它在升級之後可以正確運作。 如需詳細資訊，請參閱 [ABI 界限上的可攜性](../cpp/portability-at-abi-boundaries-modern-cpp.md)。

此外，隨著編譯器合規性不斷改進，有時候可能會改變編譯器解讀您現有原始程式碼的方式。 例如，可能會在您建置時發現不同或新的錯誤，甚至程式碼的行為與上版組建不同且看似正常運作。 雖然這些改善並非本文件中所討論的中斷性變更，但為了解決這些問題，仍然可能需要變更原始程式碼：

- [C 執行階段 (CRT) 程式庫的重大變更](#BK_CRT)

- [標準 C++ 與 C++ 標準程式庫的重大變更](#BK_STL)

- [MFC 與 ATL 的重大變更](#BK_MFC)

- [並行執行階段的重大變更](#BK_ConcRT)

## <a name="VC_2015"></a> Visual C++ 2015 的合規性變更

###  <a name="BK_CRT"></a> C 執行階段程式庫 (CRT)

#### <a name="general-changes"></a>一般變更

- **重構的二進位檔**

   CRT 程式庫已重構成兩個不同的二進位檔：通用 CRT (ucrtbase)，其中包含大部分的標準功能，以及 VC 執行階段程式庫 (vcruntime)。 vcruntime 程式庫包含編譯器相關功能，例如例外狀況處理和內建。 如果您正使用預設的專案設定，則這項變更不會對您造成影響，因為此連結器會自動使用新的預設程式庫。 如果您已將此專案 [連結器] 屬性的 [忽略所有預設程式庫] 設定為 [是]，或您在命令列使用 `/NODEFAULTLIB` 連結器選項，則必須更新程式庫清單 (在 [其他相依性] 屬性中)，藉此包含重構的新程式庫。 請將舊的 CRT 程式庫 (libcmt.lib、libcmtd.lib、msvcrt.lib、msvcrtd.lib) 取代為對等的重構程式庫。 這兩個重構程式庫中的任何一個皆有靜態 (.lib) 和動態 (.dll) 版本，也都有發行 (沒有後置詞) 和偵錯版本 (具有 "d" 後置詞)。 此動態版本具有您可與其連結的匯入程式庫。 這兩個重構程式庫為：通用的 CRT (具體而言，即 ucrtbase.dll 或 ucrtbase.lib、ucrtbased.dll 或 ucrtbased.lib) 及 VC 執行階段程式庫 (即 libvcruntime.lib、vcruntime*version*.dll、libvcruntimed.lib，以及 vcruntimed*version*.dll)。 Visual Studio 2015 和 Visual Studio 2017 中的 *version* 皆為 140。 請參閱 [CRT 程式庫的功能](../c-runtime-library/crt-library-features.md)。

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   已啟用[個別執行緒的地區設定](../parallel/multithreading-and-locales.md)時，在 locale.h 中宣告的 [localeconv](../c-runtime-library/reference/localeconv.md) 函式即可正確運作。 在此程式庫的舊版中，這個函式會傳回全域地區設定的 `lconv` 資料，而非此執行緒的地區設定。

   如果您使用個別執行緒的地區設定，您應該檢查您的 `localeconv` 使用方式。 如果您的程式碼假設所傳回 `lconv` 資料是全域地區設定，您應該加以更正。

#### <a name="mathh"></a>\<math.h>

- **數學程式庫函式的 C++ 多載**

   在舊版中，\<math.h> 定義了一些 (但不是所有) 數學程式庫函式的 C++ 多載。 多載的其餘部分都在 \<cmath> 標頭中。 只包含 \<math.h> 的程式碼可能會出現函式多載解析的問題。 現在，C++ 多載皆已從 \<math.h> 中移除，且只能在 \<cmath> 中找到。

   若要解決錯誤，請包含 \<cmath>，以取得已從 \<math.h> 移除的函式宣告。 下列函式已移動：

  - `double abs(double)` 和 `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float` 和 `long double` 版本的浮動點函式 `acos`、`acosh`、`asin`、`asinh`、`atan`、`atanh`、`atan2`、`cbrt`、`ceil`、`copysign`、`cos`、`cosh`、`erf`、`erfc`、`exp`、`exp2`、`expm1`、`fabs`、`fdim`、`floor`、`fma`、`fmax`、`fmin`、`fmod`、`frexp`、`hypot`、`ilogb`、`ldexp`、`lgamma`、`llrint`、`llround`、`log`、`log10`、`log1p`、`log2`、`lrint`、`lround`、`modf`、`nearbyint`、`nextafter`、`nexttoward`、`remainder`、`remquo`、`rint`、`round`、`scalbln`、`scalbn`、`sin`、`sinh`、`sqrt`、`tan`、`tanh`、`tgamma` 及 `trunc`

  如果您有使用 `abs` 搭配浮點類型撰寫的程式碼，且該程式碼只包含 \<math.h> 標頭，則此浮點版本將不再可用。 即使使用浮點引數，現在仍會將呼叫解析成 `abs(int)`，這會產生錯誤：

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  若要修正這個警告，可將 `abs` 呼叫取代為 `abs` 的浮點版本；例如 `fabs` (雙精度浮點引數) 或 `fabsf` (浮點引數)，或包含 \<cmath> 標頭，即可繼續使用 `abs`。

- **浮點的一致性**

   針對特殊案例的輸入，例如 NaN 和無限大，為了與 IEEE-754 和 C11 附錄 F 規格更加一致，此數學程式庫已有許多變更。 例如，在舊版的程式庫中通常將無訊息的 NaN 輸入視為錯誤，如今已不再視為錯誤。 請參閱 [IEEE 754 標準](https://standards.ieee.org/standard/754-2008.html) 和 [C11 標準](http://www.iso-9899.info/wiki/The_Standard)的附錄 F。

   這些變更不會造成編譯時期錯誤，但根據此標準，可能會導致程式的行為不同且更加正確。

- **FLT_ROUNDS**

   這是在 Visual Studio 2013 中，展開為常數運算式的 FLT_ROUNDS 巨集，因為此捨入模式為可在執行階段設定的，例如可由呼叫 fesetround 設定，所以這是不正確的。 FLT_ROUNDS 巨集現在是動態的，而且會正確反映目前的捨入模式。

#### <a name="new-and-newh"></a>\<new> 與 \<new.h>

- **new 和 delete**

   在此程式庫的舊版中，實作定義的 operator new 和 delete 函式會從此執行階段程式庫 DLL (例如，msvcr120.dll) 中匯出。 這些 operator 函式現在一律以靜態方式連結到您的二進位檔，即使是使用執行階段程式庫 DLL 亦同。

   對於原生或混合程式碼 (`/clr`) 而言，這不是中斷性變更，但對於編譯成 [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) 的程式碼，此變更可能會造成您的程式碼無法編譯。 若將程式碼編譯成 `/clr:pure`，可能必須新增 `#include <new>` 或 `#include <new.h>` 來因應此變更所造成的建置錯誤。 `/clr:pure` 選項在 Visual Studio 2015 中已淘汰，且 Visual Studio 2017 已不支援此選項。 必須是「純」程式碼才能移植到 C#。

#### <a name="processh"></a>\<process.h>

- **_beginthread 和 _beginthreadex**

   [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 函式現在會保留模組的參考，在該模組中，執行緒程序是為了該執行緒持續期間而定義的。 這有助於確保在執行緒執行到完成之前，不會卸載模組。

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start 和參考類型**

   編譯 C++ 程式碼時，現在 [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 會在編譯時間驗證傳遞給它的引數不屬於參考類型。 此 C++ 標準禁止參考類型引數。

#### <a name="stdioh-and-conioh"></a>\<stdio.h> 與 \<conio.h>

- **printf 與 scanf 系列的函式現在會在函式中定義。**

   所有 `printf` 與 `scanf` 函式的定義均已移至 \<stdio.h>、\<conio.h> 及其他 CRT 標頭內。 針對區域宣告這些函式但不包含適當 CRT 標頭的任何程式而言，這個中斷性變更會導致連結器錯誤 (LNK2019，無法解析的外部符號)。 如有可能，您應更新程式碼，將 CRT標頭 (亦即新增 `#include <stdio.h>`) 及內嵌函式包含在其中；若您不想修改程式碼來包含這些標頭檔案，也可以採用替代解決方法，在您的連結器輸入 legacy_stdio_definitions.lib 中新增額外的程式庫。

   若要在 IDE 中將此程式庫新增至您的連結器輸入，請開啟專案節點的操作功能表，選擇 [屬性] ，然後在 [專案屬性]  對話方塊中選擇 [連結器] ，並編輯 [連結器輸入]，將 `legacy_stdio_definitions.lib` 新增至分號分隔的清單。

   如果您的專案與靜態程式庫連結，且此程式庫使用 2015 之前的 Visual Studio 版本進行編譯，則此連結器可能會回報無法解析的外部符號。 這些錯誤可能會參考 `_iob`、`_iob_func` 的內部定義，或某些以 _imp_\* 格式之 \<stdio.h> 函式的相關匯入。 Microsoft 建議您在升級專案時，應以最新版本的 C++ 編譯器和程式庫重新編譯所有的靜態程式庫。 如果該程式庫是其來源無法取得的協力廠商程式庫，則您應該向協力廠商要求更新的二進位檔，或將該程式庫使用方式封裝成以舊版編譯器和舊版程式庫編譯的獨立 DLL。

    > [!WARNING]
    > 如果您要以 Windows SDK 8.1 或更早版本連結，您可能會遇到這些無法解析的外部符號錯誤。 在該情況下，您應該如先前所述地將 legacy_stdio_definitions.lib 加入連結器輸入來解決此錯誤。

   若要疑難排解未解析之符號錯誤的問題，可以嘗試使用 [dumpbin.exe](../build/reference/dumpbin-reference.md) 檢查二進位檔中定義的符號。 請嘗試下列的命令列，檢視程式庫中定義的符號。

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets 和 _getws**

   已移除 [gets](../c-runtime-library/gets-getws.md) 和 [_getws](../c-runtime-library/gets-getws.md) 函式。 因為無法安全使用，所以 gets 函式已從 C11 中的 C 標準程式庫中移除。 _getws 函式曾是 Microsoft 擴充功能，相當於 gets，但卻是用於寬字串。 您可以考慮使用這些函式的替代函式 [fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[gets_s](../c-runtime-library/reference/gets-s-getws-s.md) 及 [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。

- **_cgets 和 _cgetws**

   已移除 [_cgets](../c-runtime-library/cgets-cgetws.md) 和 [_cgetws](../c-runtime-library/cgets-cgetws.md) 函式。 您可以考慮使用這些函式的替代函數 [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) 與 [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。

- **無限大和 NaN 格式化**

   在舊版本中，會使用一組 MSVC 特定的 Sentinel 字串，將無限大和 NaN 格式化。

  - 無限大：1.#INF

  - 無訊息 NaN：1.#QNAN

  - 訊號 NaN：1.#SNAN

  - 不確定的 NaN：1.#IND

  其中任何一種格式都可能會有正負號，也可能根據欄位寬度和精確度而有稍微不同的格式 (有時會有不尋常的效果，例如：`printf("%.2f\n", INFINITY)` 可能會印出 1.#J，因為有可能會將 #INF「四捨五入」為 2 位數精確度)。 C99 導入了無限大和 NaN 格式化方式之新的需求。 MSVC 實作現在符合這些需求。 新的字串如下：

  - 無限大：inf

  - 無訊息的 NaN：nan

  - 訊號 NaN：nan(snan)

  - 不確定的 NaN：nan(ind)

  其中任何一項都可以有正負號的前置詞。 如果使用了大寫格式指定名稱 (%F，而非 %f)，則此字串會視需要以大寫字母 (`INF`，而非 `inf`) 來列印。

  [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函式在經過修改之後，已可剖析這些新字串，讓這些字串現在可以透過 `printf` 及 `scanf` 來回。

- **浮點數格式化和剖析**

   已引進新的浮點數格式化和剖析演算法來改善正確性。 此變更影響 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 及 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 系列函式及 [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 一類的函式。

   舊格式的演算法會產生有限位數的數字，然後以零填滿剩餘的小數位數。 它們通常會產生對原始浮點數值反覆存取的字串，但如果您想要精確值 (或其中最接近的十進位表示)，就會不夠合適。 新的格式演算法會視需要產生足夠多的位數，用來代表該值 (或用來填入指定的精確度)。 做為改進的範例，請考慮列印 2 的大型乘冪時之結果：

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   舊的輸出：

    ```Output
    1208925819614629200000000
    ```

   新的輸出：

    ```Output
    1208925819614629174706176
    ```

   舊的剖析演算法只會考慮輸入字串中最多 17 個有效位數，並會捨棄其餘位數。 這個方法足以產生字串所代表值的接近近似值，且通常會產生非常接近捨入正確的結果。 新的實作會考慮所有出現的位數，而且會針對所有輸入 (長度最多 768 位數) 產生正確捨入的結果。 此外，這些函式現在會遵循捨入模式 (可透過 fesetround 控制)。  這可能是中斷性行為變更，因為這些函式可能會輸出不同的結果。 新的結果永遠比舊的結果正確。

- **十六進位和無限大/NaN 浮點數剖析**

   如同以上所述，浮點數剖析演算法現在會剖析十六進位浮點數字串 (例如那些由 %a 和 %A printf 格式指定名稱所產生的浮點數字串) 和所有由此 `printf` 函式產生的無限大和 NaN 字串。

- **%A 和 %a 零填補**

   %a 和 %A 格式規範會將浮點數格式化為十六進位的尾數和二進位的指數。 在先前的版本中，`printf` 函式無法正確對字串進行零填補。 例如，`printf("%07.0a\n", 1.0)` 會印出 00x1p+0，但這應為 0x01p+0。 這項缺陷已獲得修正。

- **%A 和 %a 的精確度**

   在此程式庫的舊版中，%A 和 %a 格式規範的預設精確度是 6。 為了與 C 標準一致，現在此預設精確度為 13。

   在搭配 %A 或 %a 使用格式字串的任何函式輸出中，此為執行階段行為變更。 在舊版的行為中，使用 %A 規範的輸出可能為 "1.1A2B3Cp+111"。 現在對於相同值的輸出是 "1.1A2B3C4D5E6F7p+111"。 若要取得舊的行為，您可以指定精確度，例如 %.6A。 請參閱[精確度規格](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision)。

- **%F 規範**

   現在支援 %F 格式/轉換規範。 它的功能相當於 %f 格式指定名稱，不同之處在於無限大和 NaN 的格式使用大寫字母。

   在舊版中，此實作用來剖析 F 和 N 為長度修飾詞。 這種行為可追溯至分段位址空間的年代：這些長度修飾詞曾分別用來表示遠指標和近指標，如同 %Fp 或 %Ns。 已移除這種行為。 如果遇到 %F，現在會將它視為 %F 格式指定名稱；如果遇到 %N 時，現在會將它視為無效的參數。

- **指數格式化**

   %e 和 %E 格式規範會將浮點數格式化為十進位的尾數和指數。 在某些情況下，%g 和 %G 格式規範也會將數字格式化為這種形式。 在舊版中，CRT 永遠會產生具有三位數指數的字串。 例如，`printf("%e\n", 1.0)` 會印出 1.000000e+000，這不是正確的。 如果可使用一位數或兩位數表示該指數，則 C 要求只能印出兩位數。

   Visual Studio 2005 加入了全域合規性參數：[_set_output_format](../c-runtime-library/set-output-format.md)。 程式可以用引數 _TWO_DIGIT_EXPONENT 呼叫這個函式，以啟用符合標準的指數列印。 這項預設行為已變更為符合標準的指數列印模式。

- **格式字串驗證**

   在舊版中，`printf` 和 `scanf` 函式會以無訊息模式接受許多無效的格式字串，有時會產生不尋常的作用。 例如，會將 %hlhlhld 視為 %d。 現在會將所有無效的格式字串視為無效的參數。

- **fopen 模式字串驗證**

   在舊版中，`fopen` 系列的函式會以無訊息模式接受某些無效的模式字串 (例如 `r+b+`)。 現在會偵測到無效的模式字串並將其視為無效的參數。

- **_O_U8TEXT mode**

   [_setmode](../c-runtime-library/reference/setmode.md) 函式現在已可正確回報 in_O_U8TEXT 模式中開啟的資料流模式。 在此程式庫的舊版中，它會報告這類資料流為在 _O_WTEXT 中所開啟。

   如果您的程式碼解譯 _O_WTEXT 模式，其中資料流的編碼是 UTF-8，這就會是一項重大變更。 如果您的應用程式不支援 UTF_8，請考慮將這項日漸普遍之編碼方式的支援加入。

- **snprintf 和 vsnprintf**

   現在已實作 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 和 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)。 舊版程式碼通常會為巨集版本的這些函式提供定義，因為 CRT 程式庫並沒有實作它們，但是在較新版本中已不再需要這些函式。 現在若在加入 <\<tdio.h> 之前先將 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 或 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 定義為巨集，編譯將會失敗，並傳回錯誤指出巨集的定義位置。

   一般來說，修正這個問題之方式為刪除使用者程式碼中 `snprintf` 或 `vsnprintf` 的任何宣告。

- **tmpnam 產生可使用的檔案名稱**

   在舊版中，`tmpnam` 和 `tmpnam_s` 函式會在磁碟機的根目錄中 (例如 \sd3c.) 產生檔案名稱。 現在這些函式會在暫存目錄中產生可用的檔案名稱路徑。

- **FILE 封裝**

   在舊版中，已於 \<stdio.h> 中公開定義完整 FILE 類型，所以使用者程式碼可進入 FILE 並修改其內部項目。 此程式庫已變更為隱藏實作詳細資料。 作為這項變更的一部分，現在 \<stdio.h> 中定義的 FILE 為不透明類型，且無法從此 CRT 的外部存取其成員。

- **_outp 和 _inp**

   已移除函式 [_outp](../c-runtime-library/outp-outpw-outpd.md)、[_outpw](../c-runtime-library/outp-outpw-outpd.md)、[_outpd](../c-runtime-library/outp-outpw-outpd.md)、[_inp](../c-runtime-library/inp-inpw-inpd.md)、[_inpw](../c-runtime-library/inp-inpw-inpd.md) 和 [_inpd](../c-runtime-library/inp-inpw-inpd.md)。

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>、\<malloc.h> 及 \<sys/stat.h>

- **strtof 和 wcstof**

   當 `strtof` 和 `wcstof` 函式的值無法以浮點數表示時，就無法將 `errno` 設定為 ERANGE。 這個錯誤是這兩個函式所特定；`strtod`、`wcstod`、`strtold` 和 `wcstold` 函式不會受到影響。 這個問題已獲得修正，且是執行階段的中斷性變更。

- **對齊的配置函式**

   在先前版本中，對齊配置函式 (`_aligned_malloc`、`_aligned_offset_malloc` 等) 會以無訊息的方式接受對齊等於 0 的區塊要求。 要求的對齊必須是 2 的乘冪，而不是 0。 現在會將要求的對齊為 0 視為無效參數。 這個問題已獲得修正，且是執行階段的中斷性變更。

- **堆積函式**

   已移除 `_heapadd`、`_heapset` 和 `_heapused` 函式。 這些函式已無作用，因為 CRT 已更新為使用 Windows 堆積。

- **小型堆積**

   已移除 `smallheap` 連結選項。 請參閱[連結選項](../c-runtime-library/link-options.md)。

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   `wcstok` 函式的簽章已變更為符合 C 標準所需的簽章。 在此程式庫的舊版中，這個函式的簽章是：

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   它使用內部個別執行緒內容來追蹤呼叫之間的狀態，如同 `strtok` 所執行的。 此函式現在已有 `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` 簽章，需要呼叫者使用第三個引數將內容傳遞給此函式。

   已將舊簽章新增至新的 `_wcstok` 函式，藉此簡化移轉。 在編譯 C++ 程式碼時，還有一個具有舊簽章的 `wcstok` 內嵌多載。 會將這個多載宣告為已被取代。 在 C 程式碼中，您可能會定義 _CRT_NON_CONFORMING_WCSTOK，使用 `_wcstok` 來取代 `wcstok`。

#### <a name="timeh"></a>\<time.h>

- **時鐘**

   在舊版中，會使用 Windows API [GetSystemTimeAsFileTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime) 實作 [clock](../c-runtime-library/reference/clock.md) 函式。 連同這項實作，clock 函式會受系統時間影響，因此並不一定是單調函式。 已根據 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 重新實作 clock 函式，因此該函式現在是單調函式。

- **fstat 和 _utime**

   在舊版中，[_stat](../c-runtime-library/reference/stat-functions.md)、[fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 和 [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 函式未正確處理日光節約時間。 在 Visual Studio 2013 之前，這些函式全都未正確調整標準時間的時間，如同它們是在日光節約時間一樣。

   在 Visual Studio 2013 中，已在 **_stat** 系列函式中修正此問題，但是在 **fstat** 和 **_utime** 系列函式中，類似問題未獲修正。 這項部分修正會導致因函式之間不一致而產生的問題。 現在已修正 **fstat** 和 **_utime** 系列函式，因此這些函式現在全都能正確且一致地處理日光節約時間。

- **asctime**

   在舊版中，[asctime](../c-runtime-library/reference/asctime-wasctime.md) 函式會在個位數的天數前面填補零，例如：`Fri Jun 06 08:00:00 2014`。 此規格需要這類天數以空格填補，如 `Fri Jun  6 08:00:00 2014` 中所示。 已修正此問題。

- **strftime 和 wcsftime**

   `strftime` 和 `wcsftime` 函式現已支援 %C、%D、%e、%F、%g、%G、%h、%n、%r、%R、%t、%T、%u 和 %V 格式規範。 此外，會剖析 E 和 O 修飾詞 (但也會將其忽略)。

   會指定 %c 格式規範為對於目前地區設定產生「適當的日期和時間表示法」。 在 C 的地區設定中，這個表示法必須與 `%a %b %e %T %Y` 相同，即與 `asctime` 所產生的形式相同。 在舊版中，%c 格式指定名稱未正確使用 `MM/DD/YY HH:MM:SS` 表示法將時間格式化。 已修正此問題。

- **timespec 和 TIME_UTC**

   \<time.h> 標頭現在已定義 C11 標準的 `timespec` 類型與 `timespec_get` 函式。 此外也定義了 TIME_UTC 巨集，可與 `timespec_get` 函式搭配使用。 這項更新對於其中任何一個識別碼有衝突定義的程式碼而言是中斷性變更。

- **CLOCKS_PER_SEC**

   現在 CLOCKS_PER_SEC 巨集會展開成類型 `clock_t` 的整數，如同 C 語言所要求。

####  <a name="BK_STL"></a>C++ 標準程式庫

為了啟用新的最佳化和偵錯檢查，Visual Studio 所實作的 C++ 標準程式庫是刻意中斷各個版本之間的二進位碼相容性 (Binary Compatibility)。 因此，使用 C++ 標準程式庫時，使用不同版本所編譯的目的檔和靜態程式庫不可以混合在一個二進位檔 (EXE 或 DLL) 中，也不可以在使用不同版本所編譯的二進位檔之間傳遞 C++ 標準程式庫物件。 這類混合會發出有關 _MSC_VER 不符的連結器錯誤  (_MSC_VER 是包含此編譯器主要版本的巨集，例如對於 Visual Studio 2013 為 1800。)這項檢查無法偵測 DLL 混合，且無法偵測包含 Visual Studio 2008 及較舊版本的混合。

- **C++ 標準程式庫 Include 檔案**

   C++ 標準程式庫標頭中的 Include 結構已有一些變更。 C++ 標準程式庫標頭可以一些未經指定的方式加入彼此之中。 一般來說，您在撰寫程式碼時，應依據 C++ 標準小心地包含程式碼所需的所有標頭，而不要使用 C++ 標準程式庫標頭相互包含的這項特性。 這使其成為可攜式跨版本和跨平台的程式碼。 在 Visual Studio 2015 中，至少有兩種標頭的變更會影響使用者程式碼。 首先，\<string> 不再包含 \<iterator>。 其次，\<tuple> 現在只會宣告 `std::array`，而不會包含所有的 \<array>。此函式可能會經由下列程式碼建構組合中斷程式碼：您的程式碼具有名為 "array" 的變數及 using 指示詞 "using namespace std;"，而且包含內有 \<tuple> (現在會宣告 `std::array`) 的 C++ 標準程式庫標頭 (例如 \<functional>)。

- **steady_clock**

   [steady_clock](../standard-library/steady-clock-struct.md) 的 \<chrono> 實作已變更為符合 C++ 標準的穩定性和單一性需求。 `steady_clock` 目前是以 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 為基礎，而 `high_resolution_clock` 現在是 `steady_clock` 的 typedef。 因此，在 Visual Studio 中，`steady_clock::time_point` 現在是 `chrono::time_point<steady_clock>` 的 typedef；但是，其他實作的情況不一定也如此。

- **配置器和常數**

   我們現在要求配置器的等號/不等比較要在兩邊接受常數引數。 如果您的配置器如下定義這些運算子，

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   則您應該將其更新，並將它們宣告為 const 成員：

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **常數元素**

   C++ 標準一律禁止常數元素 (例如 vector\<const T> or set\<const T>) 的容器。 Visual Studio 2013 及較舊版接受這類容器。 在目前版本中，這類容器無法編譯。

- **std::allocator::deallocate**

   在 Visual Studio 2013 和舊版中，`std::allocator::deallocate(p, n)` 會忽略針對 *n* 而傳入的引數。  C++ 標準一直都要求 *n* 與作為第一個引數傳遞至 `allocate` 引動過程的值必須相等，該引動過程會傳回 *p*。 不過，在目前版本中，會檢查 *n* 的值。 傳遞 *n* 之引數和此標準要求不同的程式碼，可能會在執行階段損毀。

- **hash_map 和 hash_set**

   非標準的標頭檔案 \<hash_map> 和 \<hash_set> 在 Visual Studio 2015 中已淘汰，並將於後續版本中移除。 請改用 \<unordered_map> 和 \<unordered_set>。

- **比較子和 operator()**

   現在，關聯容器 (\<map> 系列) 要求其比較子具有可呼叫常數的函式呼叫運算子。 現在比較子類別宣告中的下列程式碼無法編譯：

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   若要解決這個錯誤，請將此函式宣告變更為：

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **類型特性**

   已移除來自較早版本 C++ 標準草案之類型特性的舊名稱。 這些在 C++11 中已有所變更，且已在 Visual Studio 2015 中更新為 C++11 的值。 下表顯示舊名稱和新名稱。

   |舊名稱|新名稱|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **launch::any 和 launch::sync 原則**

   已移除非標準的 `launch::any` 和 `launch::sync` 原則。 針對 `launch::any`，請改為使用 `launch:async | launch:deferred`。 對於 `launch::sync`，請使用 `launch::deferred`。 請參閱 [launch Enumeration](../standard-library/future-enums.md#launch)。

####  <a name="BK_MFC"></a> MFC 與 ATL

- **Microsoft Foundation Classes (MFC)**

   因為其大小太大而不再隨附於 Visual Studio 的「一般」安裝。 若要安裝 MFC，請在 Visual Studio 2015 安裝程式中選擇 [自訂] 安裝選項。 如果已安裝 Visual Studio 2015，您可以再次執行 **Visual Studio** 安裝程式來安裝 MFC。 選擇 [自訂] 安裝選項，然後選擇 [Microsoft Foundation Classes]。 您可以從 [控制台] 控制項、[程式和功能]，或從安裝媒體執行 **Visual Studio** 安裝程式。

   Visual C++ 可轉散發套件仍然包含這個程式庫。

####  <a name="BK_ConcRT"></a> 並行執行階段

- **Windows.h 中的 Yield 巨集與 concurrency::Context::Yield 發生衝突**

   並行執行階段之前使用 `#undef` 取消 Yield 巨集的定義，以避免 Windows.h h 和 `concurrency::Context::Yield` 函式中定義的 Yield 巨集發生衝突。 此 `#undef` 已移除，並新增了不衝突的對等 API 呼叫 [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution)。 若要因應與 Yield 的衝突，您可以更新程式碼，改成呼叫 `YieldExecution` 函式，或在呼叫位置將 `Yield` 函式名稱加上括弧，如下列範例所示：

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015 的編譯器一致性改進

從舊版升級程式碼時，也可能會因為 Visual Studio 2015 的一致性改進而發生編譯器錯誤。 這些改進並不影響較舊版 Visual Studio 的二進位相容性，但可能會產生之前從未發生過的編譯器錯誤。 如需詳細資訊，請參閱[Visual C++ What's New 2003 through 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md) (Visual C++ 2003 至 2015 的新功能)。

在 Visual Studio 2015 中，隨著編譯器一致性不斷改進，有時候可能會改變編譯器解讀您現有原始程式碼的方式。 因此，可能會在您建置時發生新的或不同錯誤，甚至程式碼的行為與上版組建不同且看似正常運作。

幸運的是，這些差異對大部分的程式碼只有一點影響，或沒有任何影響。 需要原始程式碼或其他變更才能解決這些差異時，修正會傾向小型且簡單易懂。 我們包含了許多先前接受，但後來可能需要變更的原始程式碼範例 (之前)，以及用以更正的修正 (之後)。

雖然這些差異可能影響您的原始程式碼或其他組建成品，但並不影響每版 Visual Studio 更新之間的二進位相容性。 「中斷性變更」較為嚴重，會影響二進位相容性，但這類二進位相容性中斷只會發生在 Visual Studio 的主要版本之間；例如，在 Visual Studio 2013 與 Visual Studio 2015 之間。 如需 Visual Studio 2013 與 Visual Studio 2015 之間的中斷變更資訊，請參閱 [Visual Studio 2015 一致性變更](#VC_2015)。

- [Visual Studio 2015 的一致性改善](#VS_RTM)

- [Update 1 的合規性改進](#VS_Update1)

- [Update 2 的合規性改進](#VS_Update2)

- [Update 3 的合規性改進](#VS_Update3)

###  <a name="VS_RTM"></a> Visual Studio 2015 的一致性改善

- /Zc:forScope- 選項

   `/Zc:forScope-` 編譯器選項已淘汱，並將在未來版本中移除。

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   通常，這個選項是在非標準程式碼的迴圈變數應該已經超出範圍 (根據該標準) 之後，用來允許此非標準程式碼。 只有當您使用 `/Za` 選項編譯時才需要這樣做，因為在沒有指定 `/Za` 的情況下，會一律允許在迴圈結束之後使用 for 迴圈變數。 如果您不在意標準一致性 (例如，如果您並不打算將程式碼設計成可移植到其他編譯器)，則可以關閉 `/Za` 選項 (或將**停用語言延伸模組**屬性設為**否**)。 如果您在意撰寫可攜式且符合標準規範的程式碼，就應該要重寫程式碼，將這類變數的宣告移至該迴圈外，使其符合此標準。

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` 編譯器選項

   `/Zg` 編譯器選項 (產生函式原型) 已無法使用。 這個編譯器選項之前已遭取代。

- 您再也無法從命令列藉由 mstest.exe 使用 C++ /CLI 來執行單元測試。 請改用 vstest.console.exe。 請參閱 [VSTest.Console.exe 命令列選項](/visualstudio/test/vstest-console-options)。

- **可變動的關鍵字**

   在 **mutable** 儲存類別指定名稱原先可編譯而不會發生錯誤的位置，已無法再加以使用。 現在，此編譯器會發生錯誤 C2071 (不合法的儲存類別)。 根據該標準，**mutable** 指定名稱只能套用至類別資料成員名稱，而不能套用至宣告為 const 或 static 的名稱，也不能套用至參考成員。

   例如，請參考下列程式碼：

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   舊版的編譯器可接受這種做法，但現在該編譯器會產生下列錯誤：

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   若要修正此錯誤，請移除冗餘的 **mutable** 關鍵字即可。

- **char_16_t 與 char32_t**

   您無法繼續使用 `char16_t` 或 `char32_t` 作為 **typedef** 的別名，因為現在會將這些類型視為內建類型。 使用者和程式庫作者通常會分別定義 `char16_t` 和 `char32_t` 作為 `uint16_t` 和 `uint32_t` 的別名。

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   若要更新您的程式碼，請移除此 **typedef** 宣告，並重新命名任何其他與這些名稱衝突的識別項。

- **非類型範本參數**

   在您提供明確的樣板引數之際，和非類型樣板參數有關的特定程式碼之類型相容性檢查即為正確。 例如，下列程式碼可在舊版的 Visual Studio 中正確無誤地編譯。

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   在目前的編譯器中，按照常理則會發生錯誤，因為該樣板參數類型與樣板引數不相符 (該參數是指向常數成員的指標，但該函式 f 卻是非常數函式)：

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   若要解決程式碼中的這個錯誤，請確定您使用的樣板引數的類型與此樣板參數的宣告類型相符。

- **__declspec(align)**

   該編譯器已不再接受函式上的 `__declspec(align)` 。 之前一律會忽略此建構，但現在會產生編譯器錯誤。

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   若要修正這個問題，請從此函式宣告中移除 `__declspec(align)` 。 因為它沒有任何作用，移除它並不會變更任何項目。

- **例外狀況處理**

   有幾個例外狀況處理的變更。 首先，例外狀況物件必須可複製或可移動。 下列程式碼在 Visual Studio 2013 中可成功編譯，但無法在 Visual Studio 2015 中編譯：

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   問題是出在於此複製建構函式為私用，無法如同處理例外狀況的正常過程中所發生物件一樣複製，因此並不能複製該物件。 相同情況也適用於將複製建構函式宣告為 **explicit** 的時候。

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   若要更新您的程式碼，請確定例外狀況物件的複製建構函式為 **public**，而未標示為 **explicit**。

   以傳值方式攔截例外狀況也需要可複製的例外狀況物件。 下列程式碼在 Visual Studio 2013 中可成功編譯，但無法在 Visual Studio 2015 中編譯：

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   您可以將 **catch** 的參數類型變更為參考，以修正這個問題。

    ```cpp
    catch (D& d)
    {
    }
    ```

- **後接巨集的字串常值**

   該編譯器現在支援使用者定義的常值。 因此，會將後面接著巨集且不含任何中間空白字元的字串常值解譯為使用者定義常值，這可能會產生錯誤或非預期的結果。 例如，在舊版編譯器中，下列程式碼可順利編譯：

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   該編譯器會將此程式碼解譯為後面接著巨集的字串常值 "hello"，且將該巨集展開成 "there"，然後將這兩個字串常值串連成一個。 在 Visual Studio 2015 中，編譯器會將此序列解譯為使用者定義的常值，但是沒有相符的使用者定義常值 `_x`，所以會產生錯誤。

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   若要修正這個問題，請在此字串常值和巨集之間加入空格。

- **相鄰字串常值**

   如同前面所述，因為字串剖析時相關變更的緣故，在舊版的 Visaul C++ 版本中，會將不含任何空白字元的相鄰字串常值 (寬字元或窄字元字串常值) 解譯為單一的串連字串。 在 Visual Studio 2015 中，您必須在兩個字串之間新增空白字元。 例如，下列程式碼必須有所變更：

    ```cpp
    char * str = "abc""def";
    ```

   若要修正此問題，請在兩個字串之間新增空格：

    ```cpp
    char * str = "abc" "def";
    ```

- **placement new 與 delete**

   為了讓 **delete** 運算子與 C++ 14 標準一致，已對它進行變更。 如需此標準之變更的詳細資訊，請參閱 [C++ 調整大小的解除配置](http://isocpp.org/files/papers/n3778.html)。 變更當中新增了一種全域 **delete** 運算子，該運算子會採用大小參數。 中斷性變更是如果您先前使用具有相同簽章 (藉此對應至 **placement new** 運算子) 的運算子 **delete**，就會發生編譯器錯誤 (C2956，於使用 placement new 處發生，因為在程式碼的該位置上，編譯器會嘗試識別合適且相符的 **delete** 運算子)。

   函式 `void operator delete(void *, size_t)` 曾是 **placement delete** 運算子，對應至 C++ 11 中的 **placement new** 函式 `void * operator new(size_t, size_t)`。 搭配 C++14 調整大小的解除配置，這個 delete 函式現在為「一般解除配置函式」 (全域 **delete** 運算子)。 此標準的要求為如果 placement new 的使用會查詢對應的 delete 函式，並找到一般解除配置函式，則此程式語式錯誤。

   例如，假設您的程式碼同時定義 **placement new** 和 **placement delete**：

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   您已定義的 **placement delete** 運算子與調整大小的全域新 **delete** 運算子之間，因為函式簽章相符，而導致此問題發生。 對於任何 **placement new** 和 **delete** 運算子，請考慮是否可以使用 `size_t` 以外的其他類型。 `size_t` **typedef** 的類型與編譯器有關；在 MSVC 中，它會是 **unsigned int** 的 **typedef**。 較佳的解決方案是使用這類列舉類型：

    ```cpp
    enum class my_type : size_t {};
    ```

   然後，變更 **placement new** 和 **delete** 的定義，以使用此類型取代 `size_t` 成為第二個引數。 您也需要更新對 placement new 的呼叫，以傳遞新的類型 (例如，使用 `static_cast<my_type>` 從整數值加以轉換)，並且更新 **new** 和 **delete** 的定義，用來轉換回整數類型。 您不需要為此使用 **enum**；具有 `size_t` 成員的類別類型也適用。

   另一個解決方案是，您或許可以完全排除 **placement new**。 如果您的程式碼使用 **placement new** 實作記憶體集區，其中 placement 引數是配置或刪除的物件大小，則調整大小解除配置功能或許會很適合取代您自己的自訂記憶體集區程式碼，而且您可以不使用 placement 函式，只使用您自己的雙引數 **delete** 運算子，用來取代此 placement 函式。

   如果您不想立即更新您的程式碼，則可以使用編譯器選項 `/Zc:sizedDealloc-` 來還原舊版的行為。 如果您使用這個選項，則雙引數 delete 函式將不存在，也不會與您的 **placement delete** 運算子發生衝突。

- **等位資料成員**

   等位資料成員不再具有參考類型。 下列程式碼會在 Visual Studio 2013 中成功編譯，但在 Visual Studio 2015 中會產生錯誤。

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   前一個程式碼會產生下列錯誤：

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   若要解決這個問題，請將參考類型變更為指標或值。 將此類型變更為指標需要變更使用此等位欄位的程式碼。 將此程式碼變更為值也可能會變更此等位中儲存的資料，這會影響其他欄位，因為在等位類型中的欄位會共用相同的記憶體。 根據值的大小而定，它也可能會變更等位的大小。

- 現在匿名等位與標準更一致。 舊版的編譯器會產生匿名等位的明確建構函式和解構函式。 這些編譯器產生的函式已於 Visual Studio 2015 中刪除。

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   前述程式碼會在 Visual Studio 2015 產生下列錯誤：

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   若要解決這個問題，請提供您自己的建構函式和 (或) 解構函式之定義。

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **具匿名結構的等位**

   為了符合標準，此執行階段行為為了等位中匿名結構的成員而有所變更。 建立這類等位時，不再隱含呼叫等位中匿名結構成員的建構函式。 此外，當此等位超出範圍時，將不再隱含呼叫等位中的匿名結構成員的解構函式。 請考慮下列程式碼，其中等位 U 包含匿名結構，該結構包含具有解構函式的具名成員結構 S。

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   在 Visual Studio 2013 中，會在建立 union 時呼叫 S 的建構函式，而在清除函式 f 的堆疊時，會呼叫 S 的解構函式。 但在 Visual Studio 2015 中，不會呼叫此建構函式和解構函式。 該編譯器會提供有關這項行為變更的警告。

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   若要還原原始行為，請對此匿名結構命名。 不論編譯器版本為何，非匿名結構的執行階段行為是相同的。

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   或者，請嘗試將建構函式和解構函式的程式碼移到新的函式，並加入這些來自此等位之建構函式和解構函式的函式呼叫。

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **範本解析**

   已變更樣板的名稱解析。 在 C++ 中，在考慮名稱解析的候選時，也可能產生這種情況：一或多個考慮為可能符合的名稱產生無效的樣板具現化。 這些無效的具現化通常不會造成編譯器錯誤，也就是稱為 SFINAE (替代失敗不是錯誤) 的原則。

   現在，如果 SFINAE 需要此編譯器具現化類別樣板的特製化，則在這個程序期間發生的任何錯誤都會是編譯器錯誤。 在舊版中，此編譯器會忽略這類錯誤。 例如，請參考下列程式碼：

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   如果您使用目前的編譯器編譯時，會產生下列錯誤：

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   這是因為在類別的 is_base_of 進行第一個引動過程時，尚未定義 `D`。

   在這種情況下，修正是在定義此類別之前不使用這類類型特性。 如果您將 `B` 和 `D` 的定義移至此程式碼檔案的開頭，則可解決此錯誤。 如果此定義位於標頭檔中，請檢查標頭檔之 include 陳述式的順序，藉此確定在使用有問題的樣板之前，會先編譯任何類別的定義。

- **複製建構函式**

   在 Visual Studio 2013 和 Visual Studio 2015 中，如果類別具有使用者定義的移動建構函式，但沒有使用者定義的複製建構函式，則編譯器會為該類別產生複製建構函式。 在 Dev14 中，也會將這個隱含產生的複製建構函式標示為"= delete"。

<!--From here to VS_Update1 added 04/21/2017-->

- **宣告為 extern "C" 的 main 現在需要傳回類型。**

   下列程式碼現在會產生 C4430。

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   若要修正錯誤，請新增傳回類型：

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **成員初始設定式中不允許 typename**

   下列程式碼現在會產生 C2059：

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   若要修正錯誤，請從初始設定式中移除 `typename`：

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **進行明確特製化時會忽略儲存類別。**

   在下列程式碼中，會忽略靜態儲存類別規範

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **類別範本內 static_assert 中所使用的常數將一律失敗。**

   下列程式碼會導致 `static_assert` 一律失敗：

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   若要因應此問題，請將值包裝於 **struct** 中：

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **針對向前宣告強制執行規則(只適用於 C)。**

   下列程式碼現在會產生 C2065：

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   若要修正此問題，請新增適當的向前宣告：

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **以更一致的方式強制執行函式指標類型**

   下列程式碼現在會產生 C2197：

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **模稜兩可的呼叫多載函式**

   下列程式碼現在會產生 C266：'N::bind'：模稜兩可地呼叫多載函式

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   若要修正錯誤，您可以完整限定對 `bind: N::bind(...)` 的呼叫。 不過，如果這項變更顯然是透過未宣告的識別項 (C2065) 進行的，則可能適合使用 **using** 宣告來修正此問題。

   此模式經常發生於 `Microsoft::WRL` 命名空間中的 ComPtr 和其他類型。

- **修正不正確的位址**

   下列程式碼現在會產生 C2440：'=': 無法從 'type *' 轉換為 'type'。 若要修正錯誤，請將 &(type) 變更為 (type)，以及將 (&f()) 變更為 (f())。

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **字串常值是常數陣列**

   下列程式碼現在會產生 C2664：f(void *)': 無法將引數 1 從 'const char (*)[2]' 轉換為 'void *'

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   若要修正錯誤，請將函式參數類型變更為 `const void*`，或是變更 `h` 的內容，使其看起來如以下範例所示：

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C++11 UDL 字串**

   下列程式碼現在會產生錯誤 C3688︰常值後置字元 'L' 無效; 找不到常值運算子或常值運算子範本 'operator ""L'

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   若要修正錯誤，請將程式碼變更為新增一個空格：

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   在上述範例中，不再將 `MACRO` 剖析為兩個語彙基元 (字串後面接著巨集)。 現在會將它剖析為單一語彙基元 UDL。 這同樣適用於 L""L""，此字串先前會剖析為 L"" 和 L""，而現在會剖析為 L""L 和 ""。

   字串串連規則也會符合規範，這表示 L"a" "b" 相當於 L"ab"。 舊版的 Visual Studio 不接受字元寬度不同之字串的串連。

- **已移除 C++11 空字元**

   下列程式碼現在會產生錯誤 C2137︰空的字元常值

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   若要修正錯誤，請變更程式碼以使 Null 更為明確：

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **無法依值攔截 MFC 例外狀況，因為其為不可複製**

   MFC 應用程式中的下列程式碼現在會造成錯誤 C2316：'D'：無法攔截，因為解構函式和/或複製建構函式無法存取或已遭刪除

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   若要修正程式碼，您可以將 catch 區塊變更為 `catch (const D &)`，但更好的解決方案通常是使用 MFC TRY/CATCH 巨集。

- **alignof 現在是關鍵字**

   下列程式碼現在會產生錯誤 C2332：'class': 遺漏標記名稱。 若要修正程式碼，您必須將類別重新命名；或者，如果類別正在執行與 **alignof** 相同的工作，則只需使用新的關鍵字來取代類別。

    ```cpp
    class alignof{}
    ```

- **constexpr 現在是關鍵字**

   下列程式碼現在會產生錯誤 C2059︰語法錯誤: ')'。 若要修正程式碼，您必須將任何名為 "constexpr" 的函式或變數名稱重新命名。

    ```cpp
    int constexpr() {return 1;}
    ```

- **可移動的類型不能是 const**

   當函式傳回想要移動的類型時，其傳回類型不應是 **const**。

- **刪除複製建構函式**

   下列程式碼現在會產生 C2280：'S::S(S &&)': 嘗試參考被刪除的函式：

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   若要修正錯誤，請針對 `S2` 使用直接初始化：

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **只有在未擷取任何 lambda 時，才會產生函式指標轉換**

   下列程式碼會在 Visual Studio 2015 中產生 C2664。

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   若要修正錯誤，請從擷取清單中移除 `=`。

- **涉及轉換運算子的模稜兩可呼叫**

   下列程式碼現在會產生錯誤 C2440：「類型轉換」：無法從 'S2' 轉換成 'S1'：

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   若要修正錯誤，請明確地呼叫轉換運算子：

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   下列程式碼現在會產生錯誤 C2593：「運算子 =」是模稜兩可的：

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   若要修正錯誤，請明確地呼叫轉換運算子：

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **修正非靜態資料成員初始化 (NSDMI) 中無效的複製初始化**

   下列程式碼現在會產生錯誤 C2664：'S1::S1(S1 &&)'：無法將引數 1 從 'bool' 轉換成 'const S1 &'：

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   若要修正錯誤，請使用直接初始化：

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **存取 decltype 陳述式內的建構函式**

   下列程式碼現在會產生 C2248：'S::S'：無法存取類別 'S' 中宣告的私人成員：

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   若要修正錯誤，請在 `S` 中新增 `S2` 的 friend 宣告：

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **lambda 預設的 ctor 會被隱含刪除**

   下列程式碼現在會產生錯誤 C3497︰您無法建構 Lambda 的執行個體：

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   若要修正錯誤，無須呼叫預設建構函式。 如果 Lambda 不會擷取任何項目，則可將它轉換為函式指標。

- **具有已刪除指派運算子的 Lambda**

   下列程式碼現在會產生錯誤 C2280：

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   若要修正錯誤，請使用 functor 類別取代 lambda，或者無須使用指派運算子。

- **嘗試使用已刪除的複製建構函式來移動物件**

   下列程式碼現在會產生錯誤 C2280：'moveable::moveable(const moveable &)': 嘗試參考被刪除的函式

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   若要修正錯誤，請改為使用 `std::move`：

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **區域類別無法參考稍後在相同函式中定義的其他區域類別**

   下列程式碼現在會產生錯誤 C2079︰'s' 使用未定義的 struct 'main::S2'

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   若要修正錯誤，請將 `S2` 的定義往上移動：

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **無法在衍生的 ctor 主體中呼叫受保護的基底 ctor。**

   下列程式碼現在會產生錯誤 C2248：'S1::S1'：無法存取類別 'S1' 中宣告的受保護成員

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   若要修正錯誤，請在 `S2` 中，從建構函式移除對 `S1()` 的呼叫，然後視需要將其放在另一個函式中。

- **{} 會避免轉換為指標**

   下列程式碼現在會產生 C2439：'S::p': 無法將成員初始化

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   若要修正錯誤，請移除 `0` 周圍的括弧，或是改用 **nullptr**，如下列範例所示：

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **含有括號的不正確巨集定義與使用方式**

   下列範例現在會產生錯誤 C2008：';': 未預期會出現在巨集定義中的字元

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   若要修正問題，請將第一行變更為 `#define A();`

   下列程式碼會產生錯誤 C2059︰語法錯誤: ')'

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   若要修正程式碼，請移除 A 與 () 之間的空格。

   下列程式碼會產生錯誤 C2091︰函式傳回函式：

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   若要修正錯誤，請在 S 中移除 DECLARE 之後的括號：`DECLARE;`。

   下列程式碼會產生錯誤 C2062︰未預期的類型 'int'

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   若要修正問題，請定義 `A`，如下：

    ```cpp
    #define A int
    ```

- **宣告中額外的括弧**

   下列程式碼會產生錯誤 C2062︰未預期的類型 'int'

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   若要修正錯誤，請移除 `j` 周圍的括弧。 如果為了清楚起見而需要括弧，則請使用 **typedef**。

- **編譯器產生的建構函式和 __declspec(novtable)**

   在 Visual Studio 2015 中，與 `__declspec(dllimport)` 結合使用時，在具有虛擬基底類別的抽象類別中，由編譯器所產生內嵌建構函式來公開 `__declspec(novtable)` 不當使用方式的可能性會提高。

- **auto 必須要在 direct-list-initialization 中使用單一運算式**

   下列程式碼現在會產生錯誤 C3518：’testPositions’：在 direct-list-initialization 內容中，’auto’ 的類型僅能從單一初始設定式運算式推斷

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   若要修正錯誤，一個可能方式是初始化 `testPositions`，如下：

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **針對 is_convertible 檢查類型與類型指標**

   下列程式碼現在會導致靜態判斷提示失敗。

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   若要修正錯誤，請變更 `static_assert`，使它能夠比較 `D` 和 `B2` 的指標：

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **__declspec(novtable) 宣告必須一致**

   `__declspec` 宣告在所有程式庫之間必須一致。 下列程式碼現在會產生一個定義規則 (ODR) 違規：

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

###  <a name="VS_Update1"></a> Update 1 的合規性改進

- **私用的虛擬基底類別與間接繼承**

   舊版編譯器允許衍生類別呼叫其間接衍生之 `private virtual` 基底類別的成員函式。 這個舊的行為不正確且不符合 C++ 標準。 編譯器不再接受以這種方式撰寫的程式碼，且會發出編譯器錯誤 C2280。

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   範例 (之前)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   範例 (之後)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \-或-

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **多載的運算子 new 與運算子 delete**

   編譯器先前版本允許非成員 **operator new** 和非成員 **operator delete** 宣告為 static，以及在全域命名空間以外的命名空間中宣告。  這種舊行為造成的風險是，程式不會呼叫程式設計人員所預期的 **new** 或 **delete** 運算子實作，導致無訊息的錯誤執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2323。

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   範例 (之前)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   範例 (之後)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   此外，雖然編譯器不提供特定的診斷，但內嵌運算子 **new** 會被視為語式錯誤。

- **對非類別類型呼叫 'operator *type*()' (使用者定義的轉換)**

   舊版編譯器允許在非類別類型上呼叫 'operator *type*()'，但以無訊息方式略過。 這種舊行為造成的風險是，會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2228。

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   範例 (之前)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   範例 (之後)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **詳細類型指定名稱中有重複的類型名稱**

   編譯器先前版本允許複雜的類型指定名稱中有 **typename**，但以這種方式撰寫的程式碼語意並不正確。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C3406。

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   範例 (之前)

    ```cpp
    template <typename class T>
    class container;
    ```

   範例 (之後)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **從初始設定式清單推斷陣列類型**

   舊版編譯器不支援初始設定式清單的陣列類型推斷。 編譯器現在支援這種形式的類型推斷，而這樣一來，使用初始設定式清單呼叫函式範本現在可能會模稜兩可，也可能和舊版編譯器選擇不同的多載。 若要解決這些問題，程式現在必須明確指定程式設計人員所要的多載。

   當這種新行為讓多載解析考慮和過去候選項目同樣適合的其他候選項目時，呼叫就會變得模稜兩可，而編譯器則會發出編譯器錯誤 C2668。

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   範例 1：模稜兩可地呼叫多載函式 (之前)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   範例 1：模稜兩可地呼叫多載函式 (之後)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   當這種新行為讓多載解析考慮比過去候選項目更適合的其他候選項目時，呼叫會明確解析為新的候選項目，讓程式行為變得和程式設計人員預期的不同。

   範例 2：多載解析的變更 (之前)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   範例 2：多載解析的變更 (之後)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **還原 switch 陳述式警告**

   舊版編譯器中移除了某些與 **switch** 陳述式相關的警告；現在則已還原這些警告。 編譯器現在會發出還原的警告，而與特定情況相關的警告 (包括預設的情況) 都會在包含違規情況的程式行發出，而不是在 switch 陳述式的最後一行發出。 現在，在和過去不一樣的程式行中發出警告的結果是，以前使用 `#pragma warning(disable:####)` 隱藏的警告，可能不會如預期隱藏起來。 若想要如預期隱藏這些警告，就必須將 `#pragma warning(disable:####)` 指示詞移至第一個違規情況的上一行。 下列為還原的警告：

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   C4063 範例 (之前)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   C4063 範例 (之後)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   其他還原警告的範例會於其各自文件中提供。

- **#include：路徑名稱使用上層目錄指定名稱 '..'** (只會影響 `/Wall` `/WX`)

   舊版編譯器未偵測到 在 `#include` 指示詞的路徑名稱中是否使用上層目錄指定名稱 '..'。 以這種方式撰寫的程式碼通常會包含因為錯誤使用專案相對路徑而存在於專案以外的標頭。 這種舊行為造成的風險是，編譯程式時所包含的原始程式檔，可能不是程式設計人員想要的檔案，或是這些相對路徑無法移植到其他建置環境。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會發出選擇性的編譯器警告 C4464。

    ```Output
    warning C4464: relative include path contains '..'
    ```

   範例 (之前)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   範例 (之後)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   此外，雖然編譯器不會提供特定的診斷，但仍建議您不要使用上層目錄指定名稱 ".." 來指定專案的 include 目錄。

- **#pragma optimize() 延伸超出了標頭檔結尾** (只會影響 `/Wall` `/WX`)

   舊版編譯器未偵測到最佳化旗標設定的變更，這會逸出包含在轉譯單位內的標頭檔。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在違反 `#include`的位置發出選擇性的編譯器警告 C4426。 只有當變更與編譯器命令列引數設定的最佳化旗標發生衝突時，才會發出這個警告。

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   範例 (之前)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   範例 (之後)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **不相符的 #pragma warning(push)** 和 **#pragma warning(pop)** (只會影響 `/Wall` `/WX`)

   舊版編譯器偵測不到要與不同原始程式碼檔案中，`#pragma warning(pop)` 狀態變更配對的 `#pragma warning(push)` 狀態變更，這種規劃極為罕見。 這種舊行為造成的風險是，編譯程式所啟用的警告集合不是程式設計人員想要的集合，可能導致無訊息的錯誤執行階段行為。 現在編譯器會偵測以此方式撰寫的程式碼，通知其程式設計人員，同時在符合 `#pragma warning(pop)` 的位置發出選擇性的編譯器警告 C5031 (如有啟用)。 此警告包含參考對應 #pragma warning(push) 位置的附註。

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   範例 (之前)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   範例 (之後)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   以此方式撰寫的程式碼雖然不常見，但有時是刻意為之。 以此方式撰寫的程式碼對於 `#include` 順序的變更十分敏感；如有可能，建議原始程式碼檔案獨立管理警告狀態。

- **不相符的 #pragma warning(push)** (只會影響 `/Wall` `/WX`)

   舊版編譯器轉在轉譯單位的結尾未偵測到不相符的 `#pragma warning(push)` 狀態變更。 編譯器現在會偵測以此方式撰寫的程式碼並通知其程式設計人員，同時在不相符的 `#pragma warning(push)` 位置發出選擇性的編譯器警告 C5032 (如有啟用)。 只有轉譯單位沒有任何編譯錯誤時，才會發出這個警告。

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   範例 (之前)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   範例 (之後)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **改進之後的 #pragma 警告狀態追蹤也可能會發出其他警告**

   舊版編譯器過去追蹤 #pragma 警告狀態變更的能力不佳，無法發出所有預期出現的警告。 這種行為造成的風險是，某些有效隱藏警告的情況，不是程式設計人員所預想的情況。 編譯器現在追蹤 `#pragma warning` 狀態的能力更強大，特別是關於範本內部的 `#pragma warning` 狀態變更，可以選擇性發出新的警告 C5031 和 C5032，其目的是協助程式設計人員找出非預期使用的 `#pragma warning(push)` 和 `#pragma warning(pop)`。

   在 `#pragma warning` 狀態變更追蹤經過改良之後，以往不當隱藏的警告或先前與誤判問題有關的警告，現在都能夠發出。

- **不可能執行到之程式碼的識別改善**

   C++ 標準程式庫的變更，以及比舊版編譯器強大的內嵌函式呼叫能力，可能會讓編譯器證明不可能執行到某些程式碼。 這種新行為可能會導致新的警告 C4720 的執行個體，且更頻繁地發出這個警告。

    ```Output
    warning C4720: unreachable code
    ```

   在許多情況下，只有啟用最佳化編譯時，才可能發出這個警告；因為最佳化可能內嵌更多的函式呼叫、消除多餘的程式碼，或者可能判斷某不可能執行到些程式碼。 我們觀察到，警告 C4720 的新執行個體經常發生在 **try/catch** 區塊，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) 時。

   範例 (之前)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   範例 (之後)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

###  <a name="VS_Update2"></a> Update 2 的合規性改進

- **運算式 SFINAE 的部分支援也可能會發出其他警告與錯誤**

   編譯器先前版本因為不支援 SFINAE 運算式，所以無法剖析 **decltype** 指定名稱內某些種類的運算式。 這個舊的行為不正確且不符合 C++ 標準。 編譯器現在會剖析這些運算式，並隨著一致性逐漸改進來提供運算式 SFINAE 的部分支援。 如此一來，編譯器現在就會發出在舊版編譯器未剖析的運算式中找到的警告與錯誤。

   當這個新行為剖析 **decltype** 運算式，而其中包含尚未宣告的類型時，編譯器會發出編譯器錯誤 C2039。

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   範例 1：使用未宣告的型別 (之前)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   範例 1 (之後)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   當這個新行為剖析缺少必要 **typename** 關鍵字的 **decltype** 運算式來指定相依名稱為類型時，編譯器會發出編譯器警告 C4346 與編譯器錯誤 C2923。

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   範例 2：相依名稱不是類型 (之前)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   範例 2 (之後)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- `volatile`  **成員變數會禁止隱含定義的建構函式與指派運算子**

   編譯器先前版本允許具有 **volatile** 成員變數類別自動產生預設的複製/移動建構函式，以及預設的複製/移動指派運算子。 這個舊的行為不正確且不符合 C++ 標準。 編譯器現在會考慮讓具有 **volatile** 成員變數的類別擁有非一般建構和指派運算子，其可防止自動產生這些運算子的預設實作。 當此類別是等位 (或類別內的匿名等位) 的成員時，就會將等位 (或包含匿名等位的類別) 的複製/移動建構函式和複製/移動指派運算子隱含定義為已刪除。 在未明確定義的情況下，嘗試建構或複製等位 (或包含匿名等位的類別) 將會發生錯誤，導致編譯器發出編譯器錯誤 C2280。

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   範例 (之前)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   範例 (之後)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **靜態成員函式不支援 cv 限定詞**

   舊版 Visual Studio 2015 允許靜態成員函式擁有 cv 限定詞。 此行為起因於 Visual Studio 2015 與 Visual Studio 2015 Update 1 的迴歸；Visual Studio 2013 與舊版編譯器拒絕以此方式撰寫的程式碼。 Visual Studio 2015 與 Visual Studio 2015 Update 1 的行為不正確且不符合 C++ 標準。  Visual Studio 2015 Update 2 拒絕以此方式撰寫的程式碼，並會發出編譯器錯誤 C2511。

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   範例 (之前)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   範例 (之後)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **WinRT 程式碼不允許列舉的向前宣告** (只會影響 `/ZW`)

   為 Windows 執行階段 (WinRT) 編譯的程式碼不允許向前宣告 **enum** 類型，類似於使用 `/clr` 編譯器參數為 .Net Framework 編譯受控 C++ 程式碼的情形。 此行為可確保一律得知列舉的大小，並能正確將其投影至 WinRT 類型系統。 編譯器拒絕以此方式撰寫的程式碼，且會發出編譯器錯誤 C2599 以及編譯器錯誤 C3197。

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   範例 (之前)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   範例 (之後)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **不得以內嵌方式宣告多載的非成員運算子 new 與運算子 delete** (層級 1 (`/W1`) 預設為開啟)

   舊版編譯器不會在以內嵌方式宣告多載的非成員運算子 new 與運算子 delete 函式時發出警告。 以此方式撰寫的程式碼語式錯誤 (不需要診斷)，且可能因為 new 與 delete 運算子不相符 (尤其在搭配調整大小後的解除配置使用時)，而導致難以診斷的記憶體問題。 編譯器現在會發出編譯器警告 C4595，協助識別以此方式撰寫的程式碼。

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   範例 (之前)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   範例 (之後)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   可能需要先將運算子定義從標頭檔移出，再將其移入對應的原始程式檔，才能修正以此方式撰寫的程式碼。

###  <a name="VS_Update3"></a> Update 3 的合規性改進

- **std::is_convertable 現在已可偵測自我指派** (標準程式庫)

   當舊版 `std::is_convertable` 類型特性的複製建構函式被刪除或為私用時，其無法正確地偵測類別類型的自我指派。 現在在套用到複製建構函式已刪除或為 private 的類別類型時，`std::is_convertable<>::value` 會正確設定為 **false**。

   此變更沒有相關聯的編譯器診斷。

   範例

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   在編譯器先前版本中，因為 `std::is_convertable<>::value` 不正確地設定為 **true**，致使此範例底部的靜態判斷提示能夠通過。 `std::is_convertable<>::value` 現在會正確地設定為 **false**，讓靜態判斷提示失敗。

- **預設或已刪除的 trivial 複製及移動建構函式會採用存取指定名稱**

   舊版編譯器不會檢查預設或已刪除之 trivial 複製及移動建構函式的存取指定名稱，就允許其接受呼叫。 這個舊的行為不正確且不符合 C++ 標準。 在某些情況下，這項舊行為的風險是會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器現在會檢查預設或已刪除之 trivial 複製及移動建構函式的存取指定名稱，據此決定其是否可以接受呼叫；若無法呼叫，即發出編譯器警告 C2248。

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   範例 (之前)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   範例 (之後)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **屬性化 ATL 程式碼支援已標示為即將淘汰** (層級 1 (`/W1`) 預設為開啟)

   舊版編譯器支援屬性化 ATL 程式碼。 因為從 [Visual Studio 2008 開始](https://msdn.microsoft.com/library/bb384632)下一階段對屬性化 ATL 支援的移除，所以已淘汰屬性化 ATL 程式碼。 編譯器現在會發出編譯器警告 C4467，協助識別這類已標示為即將淘汰的程式碼。

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   若要繼續使用屬性化 ATL 程式碼直到從編譯器移除支援為止，可將 `/Wv:18` 或 `/wd:4467` 命令列引數傳遞給編譯器，或在原始程式碼中新增 `#pragma warning(disable:4467)` 來停用此警告。

   範例 1 (之前)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   範例 1 (之後)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   您偶爾可能會需要或想要建立 IDL 檔案，以避免使用已標示為即將淘汰的 ATL 屬性，如下列範例程式碼所示

   範例 2 (之前)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   首先，請建立 *.idl 檔案；產生的 vc140.idl 檔案可用於取得包含介面及註釋的 \*.idl 檔案。

   接著請在您的組建中新增 MIDL 步驟，確保 C++ 介面定義能夠順利產生。

   範例 2 IDL (之後)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   然後請直接在實作檔案中使用 ATL，如下列範例程式碼所示。

   範例 2 實作 (之後)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **先行編譯的標頭檔 (PCH) 與不相符的 #include 指示詞** (僅會影響 `/Wall` `/WX`)

   使用先行編譯的標頭檔 (PCH) 時，舊版編譯器接受 `-Yc` 與 `-Yu` 編譯之間原始程式碼中的 `#include` 指示詞不相符。 編譯器現在已不再接受以此方式撰寫的程式碼。   現在在使用 PCH 檔案時，編譯器會發出編譯器警告 CC4598 協助識別不相符的 `#include` 指示詞。

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   範例 (之前)：

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   範例 (之後)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **先行編譯的標頭檔 (PCH) 與不相符的 #include 目錄** (僅會影響 `/Wall` `/WX`)

   使用先行編譯的標頭檔 (PCH) 時，舊版編譯器接受 `-Yc` 與 `-Yu` 編譯之間與編譯器不相符的 include 目錄 (`-I`) 命令列引數。 編譯器現在已不再接受以此方式撰寫的程式碼。 現在在使用 PCH 檔案時，編譯器會發出編譯器警告 CC4599 協助識別不相符的 include 目錄 (`-I`) 命令列引數。

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   範例 (之前)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   範例 (之後)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 一致性變更

### <a name="compiler"></a>編譯器

- **final** 關鍵字現在會在先前編譯過的位置產生無法解析的符號錯誤：

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   在舊版中，由於呼叫為 **virtual** 呼叫，因此不會發出錯誤；儘管如此，程式還是會在執行階段損毀。 現在，由於已知類別為 final，因此會發出連結器錯誤。 在這個範例中，為了修正錯誤，您會連結包含 `S2::f` 之定義的 obj。

- 當您在命名空間中使用 friend 函式時，必須先重新宣告 friend 函式才能加以參考，否則將會收到錯誤；這是因為編譯器現在遵循 ISO C++ 標準。 例如，此範例不再編譯：

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   若要修正這個程式碼，請宣告 **friend** 函式：

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- 此 C++ 標準不允許在類別中明確特製化。 雖然 Microsoft Visual C++ 編譯器在某些情況下允許這種做法，但是在像下列範例這樣的情況下，現在就會產生錯誤，因為編譯器不會將第二個函式視為第一個函式的特製化。

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   若要更正這個程式碼，請修改第二個函式：

    ```cpp
    template <> void f(char& val);
    ```

- 編譯器不會再嘗試清楚區別下列範例中的兩個函式，且現在還會發出錯誤：

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   若要更正這個程式碼，請釐清呼叫：

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- 在編譯器符合 ISO C++11 之前，下列程式碼會進行編譯並導致 `x` 解析為 **int** 類型：

    ```cpp
    auto x = {0};
    int y = x;
    ```

   這個程式碼現在會將 `x` 解析為 `std::initializer_list<int>` 類型，而導致在下一行上嘗試將 `x` 指派給 **int** 類型時發生錯誤。(預設不會進行轉換)。若要修正此程式碼，請使用 **int** 取代 **auto**︰

    ```cpp
    int x = {0};
    int y = x;
    ```

- 當右側值類型不符合左側要初始化的值類型時，將無法再彙總初始化且會發出錯誤；因為根據 ISO C++11 標準的要求，初始化必須在不縮小轉換的情況下統一執行。 過去在舊版中如可使用縮小轉換，會發出[編譯器警告 (層級 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) 警告，而不會發出錯誤。

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   若要更正這個程式碼，請加入明確的縮小轉換：

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- 下列初始化已無法再執行：

    ```cpp
    void *p = {{0}};
    ```

   若要更正這個程式碼，請使用下列任一形式：

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- 名稱查閱已變更。 Visual Studio 2012 與 Visual Studio 2013 中的 C++ 編譯器 會以不同方式解析下列程式碼︰

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   Visual Studio 2012 中 `E1::b` 運算式的 `E1`，會解析為全域範圍中的 `::E1`。 Visual Studio 2013 中 `E1::b` 運算式的 `E1`，會解析為 `main()` 中的 `typedef E2` 定義，且具有 `::E2` 類型。

- 物件配置已變更。 在 x64 上，類別的物件配置可能會和先前的版本不同。 如果它具有 **virtual** 函式，但沒有具有 **virtual** 函式的基底類別，則編譯器物件模型會在資料成員配置之後插入指向 **virtual** 函式表的指標。 這表示該配置可能無法在所有情況下都是最佳。 在舊版中，一項針對 x64 的最佳化項目會嘗試為您改善配置，但因為該項目在複雜的程式碼中無法正確運作，所以在 Visual Studio 2013 中已將其移除。 例如，請參考這個程式碼：

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- 在 Visual Studio 2013 中，x64 上 `sizeof(S2)` 的結果為 48，但在舊版中會評估為 32。 若要在 x64 版的 Visual Studio 2013 C++ 編譯器中將其評估為 32，請新增具有 **virtual** 函式的虛設基底類別：

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   若要在程式碼中尋找舊版本嘗試進行最佳化的地方，請搭配 `/W3` 編譯器選項來使用該版本的編譯器並開啟警告 4370。 例如：

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   在 Visual Studio 2013 以前，此程式碼會輸出此訊息：「警告 C4370：'S2'：因為較佳的封裝，類別配置已從舊版的編譯器變更」。

   在所有版本的編譯器中，x86 編譯器都具有相同配置的次佳問題。 例如，如果這個程式碼是為 x86 而編譯：

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   
  `sizeof(S)` 的結果會是 24。 不過，如果您使用提到的 x64 因應措施，則可以減少為 16：

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>標準程式庫

Visual Studio 2013 中的 C++ 編譯器可偵測 _ITERATOR_DEBUG_LEVEL 中不符的情況 (實作於 Visual Studio 2010 中) 以及 RuntimeLibrary 不符的情況。 當編譯器選項 `/MT` (靜態發行)、`/MTd` (靜態偵錯)、`/MD` (動態發行) 和 `/MDd` (動態偵錯) 混和時，就會發生這些不相符的情況。

- 若您的程式碼認可舊版的模擬別名範本，必須加以變更。 例如，現在您必須改成 `allocator_traits<A>::rebind_alloc<U>::other`，而不是 `allocator_traits<A>::rebind_alloc<U>`。 雖然已不再需要 `ratio_add<R1, R2>::type`，而且現在建議您使用 `ratio_add<R1, R2>`，但前者還是會進行編譯，因為 `ratio<N, D>` 必須有縮減一定比例的「類型」typedef (如果已經縮減，則會是相同類型)。

- 在呼叫 `#include <algorithm>` 或 `std::min()` 時，您必須使用 `std::max()`。

- 若您現有的程式碼使用舊版的模擬範圍列舉 (包裝在命名空間中傳統不限範圍的列舉)，必須加以變更。 例如，如果您原本參考 `std::future_status::future_status` 類型，則現在必須改為 `std::future_status`。 不過，大部分的程式碼不會受影響，例如 `std::future_status::ready` 仍會編譯。

- `explicit operator bool()` 會比運算子 unspecified-bool-type() 更為嚴格。 `explicit operator bool()` 允許明確轉換為 bool (例如，假設有一個 `shared_ptr<X> sp`，則 `static_cast<bool>(sp)` 和 `bool b(sp)` 都有效)，以及可轉換為 bool 之可進行布林值測試的「內容轉換」(例如 `if (sp)`、`!sp`、`sp &&`)。 不過，`explicit operator bool()` 會禁止隱含轉換成 bool，因此您不能使用 `bool b = sp;`，且假設傳回類型為 bool，則您不能使用 `return sp`。

- 因為現在是實作真正的 variadic 範本，所以 _VARIADIC_MAX 與相關的巨集不會有任何作用。 如果您仍然正在定義 _VARIADIC_MAX，則會將它忽略。 如果您認可我們的巨集機制主要在於以任何其他方式支援模擬的 variadic 樣板，那麼您必須變更程式碼。

- 除了一般關鍵字之外，C++ 標準程式庫標頭現在禁止對隨內容改變的關鍵字 **override** 及 **final** 執行巨集取代。

- `reference_wrapper`、`ref()` 及 `cref()` 現在禁止繫結至暫存物件。

- \<random> 現在會嚴格實施其編譯時期前置條件。

- 各種不同的 C++ 標準程式庫類型特性都有「T 應為完整的類型」這項前置條件。 雖然編譯器現在會更嚴格實施這項先決條件，但並非在所有情況中都能實施。 (因為 C++ 標準程式庫前置條件違規會觸發未經定義的行為，所以這項標準無法保證一定能夠實施)。

- C++ 標準程式庫不支援 `/clr:oldSyntax`。

- C++11 的 common_type<> 指定會出現未預期及預期外的結果，特別是會讓 common_type\<int, int>::type 傳回 int&&。 因此，編譯器實作了針對程式庫工作小組問題 2141 所提出的解決方法，讓 common_type\<int, int="">::type 傳回 int。

   這項變更的副作用就是無法再使用識別案例 (common_type\<T> 不一定會產生類型 T)。 此行為符合建議的解決方法，不過它會破壞依賴之前行為的任何程式碼。

   如需識別類型特徵，請勿使用 \<type_traits> 中定義的非標準 `std::identity`，因為其不適用於 \<void>。 請改為依照您的需求，實作自己的識別類型特性。 以下為範例：

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC 和 ATL

- **僅限 Visual Studio 2013**：因為 Unicode 現在已相當普遍且 MBCS 的使用率大幅降低，所以 Visual Studio 不會隨附 MFC MBCS 程式庫。 這項變更也讓 MFC 與 Windows SDK 本身更為相符，因為許多新的控制項和訊息都限用 Unicode。 不過，如果您必須繼續使用 MBCS MFC 程式庫，您可以從 MSDN 下載中心下載 [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770)。 Visual C++ 可轉散發套件仍然包含這個程式庫。  (注意：在 Visual Studio 2015 和更新版本中，MBCS DLL 會隨附在 C++ 安裝程式元件內)。

- MFC 功能區的協助工具已有變更。  一改過去的單層架構，現在改為階層式架構。 您仍然可以藉由呼叫 `CRibbonBar::EnableSingleLevelAccessibilityMode()` 使用舊有行為。

- `CDatabase::GetConnect` 方法已移除。 為使安全性變得更好，連接字串現在會加密儲存且只在必要時解密；其無法再以純文字格式傳回。  字串可透過使用 `CDatabase::Dump` 方法來取得。

- `CWnd::OnPowerBroadcast` 的簽章已變更。 這個訊息處理常式的簽章已變更為接受 LPARAM 做為第二個參數。

- 簽章已變更為可容納訊息處理常式。 下列函式的參數清單已變更為使用新加入的 ON_WM_* 訊息處理常式：

   - `CWnd::OnDisplayChange` 已變更為 (UINT, int, int)，而不再是 (WPARAM, LPARAM)，所以可在訊息對應中使用新的 ON_WM_DISPLAYCHANGE 巨集。

   - `CFrameWnd::OnDDEInitiate` 已變更為 (CWnd*, UINT, UNIT)，而不再是 (WPARAM, LPARAM)，所以可在訊息對應中使用新的 ON_WM_DDE_INITIATE 巨集。

   - `CFrameWnd::OnDDEExecute` 已變更為 (CWnd*, HANDLE)，而不再是 (WPARAM, LPARAM)，所以可在訊息對應中使用新的 ON_WM_DDE_EXECUTE 巨集。

   - `CFrameWnd::OnDDETerminate` 已變更為 (CWnd*) 作為參數，而不再是 (WPARAM, LPARAM)，所以可在訊息對應中使用新的 ON_WM_DDE_TERMINATE 巨集。

   - `CMFCMaskedEdit::OnCut` 已變更為不使用任何參數，而不再是 (WPARAM, LPARAM)，所以可以在訊息對應中使用新的 ON_WM_CUT 巨集。

   - `CMFCMaskedEdit::OnClear` 已變更為不使用任何參數，而不再是 (WPARAM, LPARAM)，所以可以在訊息對應中使用新的 ON_WM_CLEAR 巨集。

   - `CMFCMaskedEdit::OnPaste` 已變更為不使用任何參數，而不再是 (WPARAM, LPARAM)，所以可以在訊息對應中使用新的 ON_WM_PASTE 巨集。

- MFC 標頭中的 `#ifdef` 指示詞已移除。 已移除 MFC 標頭檔中許多與不支援之 Windows 版本相關的 `#ifdef` (WINVER &lt; 0x0501)。

- ATL DLL (atl120.dll) 已移除。 現在提供的 ATL 為標頭和靜態程式庫 (atls.lib)。

- Atlsd.lib、atlsn.lib 和 atlsnd.lib 已移除。 Atls.lib 不再具有字元集相依性或偵錯/發行專屬的程式碼。 由於對於 Unicode/ANSI 和偵錯/發行，它的運作方式相同，因此只需要一個版本的程式庫。

- ATL/MFC 追蹤工具會隨 ATL DLL 移除，追蹤機制也有所簡化。 `CTraceCategory` 建構函式現在會接受一個參數 (分類名稱)，而 TRACE 巨集會呼叫 CRT 偵錯報告函式。

## <a name="visual-c-2012-breaking-changes"></a>Visual C++ 2012 的重大變更

### <a name="compiler"></a>編譯器

- `/Yl` 編譯器選項已變更。 編譯器預設會使用此選項，在某些情況下，可能會導致 LNK2011 錯誤。 如需詳細資訊，請參閱 [/Yl (Inject PCH Reference for Debug Library)](../build/reference/yl-inject-pch-reference-for-debug-library.md) (/Yl (插入偵錯程式庫的 PCH 參考))。

- 在使用 `/clr` 編譯的程式碼中，**enum** 類別關鍵字會定義 C++11 列舉，而非通用語言執行平台 (CLR) 列舉。 若要定義 CLR 列舉，其協助工具必須明確。

- 使用範本關鍵字明確釐清相依名稱 (符合 C++ 語言標準)。 在下列範例中，反白顯示的範本關鍵字是解析模稜兩可問題的必備項目。 如需詳細資訊，請參閱 [Name Resolution for Dependent Types](../cpp/name-resolution-for-dependent-types.md) (相依類型的名稱解析)。

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- 類型 float 的常數運算式已不可再用為範本引數，如下列範例所示。

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- 使用 `/GS` 命令列選項編譯並具有差一 (off-by-one) 弱點的程式碼可能會在執行階段期間導致處理序終止，如下列虛擬程式碼範例所示。

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- x86 組建的預設結構已變更為 SSE2；因此，編譯器可能會發出 SSE 指令，並會使用 XMM 暫存器執行浮點計算。 若要還原成先前的行為，可使用 `/arch:IA32` 編譯器旗標將架構指定為 IA32。

- 編譯器可能會發出下列警告：[編譯器警告 (層級 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)及 C4701，但先前不會如此。 編譯器會加強對使用指標類型未經初始化區域變數的檢查。

- 如有指定新連結器旗標 `/HIGHENTROPYVA`，Windows 8 通常會導致記憶體配置傳回 64 位元的位址。 (在 Windows 8 之前，這類配置更常傳回小於 2 GB 的位址)。這項變更可能會暴露現有程式碼中的指標截斷 Bug。 此參數預設為開啟。 若要停用此行為，請指定 `/HIGHENTROPYVA:NO`。

- 針對受控組建，受控編譯器 (Visual Basic/C#) 也支援 `/HIGHENTROPYVA`。  但在此情況下，`/HIGHENTROPYVAswitch` 預設為關閉。

### <a name="ide"></a>IDE

- 雖然我們建議您不要使用 C++/CLI 建立 Windows Form 應用程式，但仍能維護現有的 C++ /CLI 應用程式。 若您已經建立了 Windows Form 應用程式或任何其他 .NET UI 應用程式，請使用 C# 或 Visual Basic。 唯有在互通性的考量下，才使用 C++/CLI。

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>平行模式程式庫與並行執行階段程式庫

`UmsThreadDefault` 的 `SchedulerType` 列舉已淘汰。 指定 `UmsThreadDefault` 會產生淘汰的警告，並會在內部對應回 `ThreadScheduler`。

### <a name="standard-library"></a>標準程式庫

- 下列為 C++98/03 與 C++11 標準之間的中斷性變更︰在 Visual Studio 2012 中的 Visual C++ 內使用明確範本引數來呼叫 `make_pair()` (即 `make_pair<int, int>(x, y)`) 通常無法編譯。 解決方案是只呼叫 `make_pair() `，而不要指定明確範本引數 (例如 `make_pair(x, y)`)。 提供明確的範本引數會導致函式失效。 若您需要精確控制產生的類型，請改為使用 `pair` 而非 `make_pair`，如同 `pair<short, short>(int1, int2)`。

- C++98/03 和 C++11 標準之間的另一項中斷性變更為：當 A 可以隱含轉換成 B，且 B 可以隱含轉換成 C，但 A 卻無法隱含轉換成 C 時，C++98/03 和 Visual C++ 2010 允許將 `pair<A, X>` 轉換 (隱含或明確) 成 `pair<C, X>`。 (另一個類型 X 不是此處的重點，且不是配對中第一種類型的專用類型)。Visual Studio 2012 中的 C++ 編譯器偵測到 A 並未隱含表示可轉換成 C，所以會從多載解析中移除配對轉換。 這項變更對許多狀況而言有益。 例如，多載 `func(const pair<int, int>&)` 和 `func(const pair<string, string>&)`，以及使用 `pair<const char *, const char *>` 呼叫 `func()` 時，便會使用這項變更進行編譯。 但此變更會破壞需要積極執行 pair 轉換的程式碼。 一般可以藉由明確執行轉換的其中一部分來修正這類程式碼，例如將 `make_pair(static_cast<B>(a), x)` 傳遞給需要 `pair<C, X>` 的函式。

- Visual C++ 2010 可模擬 variadic 範本 (例如 `make_shared<T>(arg1, arg2, argN)`) 高達 10 個引數之多，方法是停止前置處理器機器的多載與特製化。 在 Visual Studio 2012 中，此限制縮減為五個引數，以改善大多數使用者的編譯時間及編譯器記憶體耗用量。 但您可以藉由將 _VARIADIC_MAX 明確定義為 10 來將整個專案設定成先前的限制。

- 當包含 C++ 標準程式庫標頭時，C++11 17.6.4.3.1 [macro.names]/2 會禁止對關鍵字執行巨集取代。 當標頭偵測到巨集取代的關鍵字時，現在會發出編譯器錯誤。 (定義 _ALLOW_KEYWORD_MACROS 可允許編譯這類程式碼，但極力建議不要如此定義)。作為例外狀況，預設允許使用巨集形式的 `new`，因為標頭使用 `#pragma push_macro("new")`/`#undef new`/`#pragma pop_macro("new")` 進行全面自我防禦。 定義 _ENFORCE_BAN_OF_MACRO_NEW 不全然如其名稱所示。

- 為實作各種最佳化及偵錯檢查，C++ 標準程式庫實作是刻意中斷了各版 Visual Studio (2005、2008、2010、2012) 之間的二進位相容性。 當使用 C++ 標準程式庫時，這會導致無法將物件檔案與使用不同版本編譯的靜態程式庫混合成一個二進位檔 (EXE 或 DLL)，且也無法在使用不同版本編譯的二進位檔之間傳遞 C++ 標準程式庫物件。 混合物件檔案與靜態程式庫 (使用由 Visual Studio 2010 編譯的 C++ 標準程式庫與使用 Visual Studio 2012 之 C++ 編譯器編譯的 C++ 標準程式庫) 會發出有關 _MSC_VER 不符的連結器錯誤，其中 _MSC_VER 是包含編譯器主要版本 (Visual Studio 2012 的 Visual C++ 為 1700) 的巨集。 這項檢查無法偵測 DLL 混合，且無法偵測包含 Visual C++ 2008 及較舊版本的混合。

- 除了偵測 _ITERATOR_DEBUG_LEVEL 不符的情況 (實作於 Visual Studio C++ 2010) 之外，Visual Studio 2012 的 C++ 編譯器還會偵測執行階段程式庫不符的錯誤。 當編譯器選項 `/MT` (靜態發行)、`/MTd` (靜態偵錯)、`/MD` (動態發行) 和 `/MDd` (動態偵錯) 混合時，就會發生這些不相符的情況。

- 針對 `std::unordered_map` 和 `stdext::hash_map` 容器系列，先前可以使用 `operator<()`、`operator>()`、`operator<=()` 和 `operator>=()`，雖然其實作並不是很有用。 因此 Visual Studio 2012 的 Visual C++ 移除了這些非標準運算子。 此外，`std::unordered_map` 系列的 `operator==()` 和 `operator!=()` 實作已延伸至涵蓋 `stdext::hash_map` 系列。 (建議您避免在新的程式碼中使用 `stdext::hash_map` 系列。)

- C++11 22.4.1.4 [locale.codecvt] 指定 `codecvt::length()` 和 `codecvt::do_length()` 應接受可修改的 `stateT&` 參數，但 Visual Studio 2010 接受的參數為 `const stateT&`。 而 Visual Studio 2012 的 C++ 編譯器則因為遵循標準而接受 `stateT&`。 對於想要覆寫虛擬函式 `do_length()` 的使用者而言，此差異相當重大。

### <a name="crt"></a>CRT

- new 與 malloc() 中使用的 C 執行階段 (CRT) 堆積已不再是私用。 CRT 現在會使用處理序堆積。 這表示堆積不會在 DLL 卸載之後終結，因此靜態連結到 CRT 的 DLL 必須在卸載之前先清除 DLL 程式碼所配置的記憶體。

- `iscsymf()` 函式使用負數值進行判斷提示。

- `threadlocaleinfostruct` 結構已變更為可接受地區設定函式的變更。

- 具有對應內建函式的 CRT 函式 (例如 `memxxx()`、`strxxx()`) 已從 intrin.h 中移除。 若這些函式中只包含 intrin.h，現在也必須加入相對應的 CRT 標頭。

### <a name="mfc-and-atl"></a>MFC 和 ATL

- 已移除 Fusion 支援 (afxcomctl32.h)；因此所有在 \<afxcomctl32.h> 中定義的方法也會一併移除。 標頭檔 \<afxcomctl32.h> 和 \<afxcomctl32.inl> 已刪除。

- 已將 `CDockablePane::RemoveFromDefaultPaneDividier` 的名稱變更為 `CDockablePane::RemoveFromDefaultPaneDivider`。

- 已將 `CFileDialog::SetDefExt` 的簽章變更為使用 LPCTSTR，因此會影響 Unicode 組建。

- 移除了過時的 ATL 追蹤分類。

- 已變更 `CBasePane::MoveWindow` 的簽章，使其接受 `const CRect`。

- 已變更 `CMFCEditBrowseCtrl::EnableBrowseButton` 的簽章。

- 已從 `CMFCBaseTabCtrl` 移除 `m_fntTabs` 和 `m_fntTabsBold`。

- 已將參數新增至 `CMFCRibbonStatusBarPane` 建構函式。 (這是預設參數，所以不是來源中斷的問題)。

- 已將參數新增至 `CMFCRibbonCommandsListBox` 建構函式。 (這是預設參數，所以不是來源中斷的問題)。

- 已移除 `AFXTrackMouse` API (及相關計時器處理序)。 請改為使用 Win32 `TrackMouseEvent` API。

- 已將參數新增至 `CFolderPickerDialog` 建構函式。 (這是預設參數，所以不是來源中斷的問題)。

- `CFileStatus` 結構大小變更︰`m_attribute` 成員已從 BYTE 變更為 DWORD (以符合從 `GetFileAttributes` 傳回的值)。

- `CRichEditCtrl` 和 `CRichEditView` 會在 Unicode 組建中使用 MSFTEDIT_CLASS (RichEdit 4.1 控制) 而非 RICHEDIT_CLASS (RichEdit 3.0 控制)。

- 已移除 `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground`，因為它在 Windows Vista、Windows 7 和 Windows 8 上一律為 TRUE。

- 已移除 `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable`，因為它在 Windows Vista、Windows 7 和 Windows 8 上一律為 TRUE。

- 已移除 `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`。 直接在 Windows Vista、Windows 7 及 Windows 8 上呼叫 Windows API。

- 已移除 `AFX_GLOBAL_DATA::DwmDefWindowProc`。 直接在 Windows Vista、Windows 7 及 Windows 8 上呼叫 Windows API。

- 已將 `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` 重新命名為 `IsDwmCompositionEnabled` 以避免名稱衝突。

- 變更了許多 MFC 內部計時器的識別碼，並將定義移至 afxres.h (AFX_TIMER_ID_ *)。

- 已將 `OnExitSizeMove` 方法的簽章變更為與 ON_WM_EXITSIZEMOVE 巨集一致：

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- 已將 `OnDWMCompositionChanged` 的名稱和簽章變更為與 ON_WM_DWMCOMPOSITIONCHANGED 巨集一致：

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- 已將 `OnMouseLeave` 方法的簽章變更為與 ON_WM_MOUSELEAVE 巨集一致：

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` ReplaceThisText

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- 已將 `OnPowerBroadcast` 的簽章變更為與 ON_WM_POWERBROADCAST 巨集一致：

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- 已將 `OnStyleChanged` 的簽章變更為與 ON_WM_STYLECHANGED 巨集一致：

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- 已將內部方法 `FontFamalyProcFonts` 重新命名為 `FontFamilyProcFonts`。

- 已移除多個全域靜態 `CString` 物件，以解決某些狀況中的記憶體流失問題 (由 #defines 取代)，同時也移除了下列類別成員變數：

   - `CKeyBoardManager::m_strDelimiter`

   - `CMFCPropertyGridProperty::m_strFormatChar`

   - `CMFCPropertyGridProperty::m_strFormatShort`

   - `CMFCPropertyGridProperty::m_strFormatLong`

   - `CMFCPropertyGridProperty::m_strFormatUShort`

   - `CMFCPropertyGridProperty::m_strFormatULong`

   - `CMFCPropertyGridProperty::m_strFormatFloat`

   - `CMFCPropertyGridProperty::m_strFormatDouble`

   - `CMFCToolBarImages::m_strPngResType`

   - `CMFCPropertyGridProperty::m_strFormat`

- 已變更 `CKeyboardManager::ShowAllAccelerators` 的簽章，並移除了快速鍵分隔符號參數。

- 已新增 `CPropertyPage::GetParentSheet`，並在 `CPropertyPage` 類別中改為呼叫它而非 `GetParent`，以取得正確的父代工作表視窗，而該視窗可能是 `CPropertyPage` 的父代視窗或父父代視窗。 您可能必須變更您的程式碼，才能呼叫 `GetParentSheet` 而不是 `GetParent`。

- 修正了 ATLBASE.H 中不對稱的 #pragma warning(push) ATLBASE，其會導致警告不正確地停用。 這些警告現在在 ATLBASE 經過剖析之後，都會正確地啟用。

- 移動了 AFX_GLOBAL_DATA to _AFX_D2D_STATE 中與 D2D 相關的方法：

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - 例如，並非呼叫 `afxGlobalData.IsD2DInitialized` 不同，而是改為呼叫 `AfxGetD2DState->IsD2DInitialized`。

- 移除了 \atlmfc\include\ 資料中過時的 ATL*.CPP 檔案。

- 已將 `afxGlobalData` 初始化移至隨選，而不是在 CRT 初始化階段，以滿足 `DLLMain` 需求。

- 已將 `RemoveButtonByIndex` 方法新增至 `CMFCOutlookBarPane` 類別。

- 已將 `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` 修正為 `IsFrequentlyUsedCmd`。

- 已將 `RestoreOriginalstate` 的數個執行個體修正為 `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`。

- 已從 `CDockablePane` 移除未使用的方法：`SetCaptionStyle`、`IsDrawCaption`、`IsHideDisabledButtons`、`GetRecentSiblingPaneInfo` 和 `CanAdjustLayout`。

- 已移除 `CDockablePane` 靜態成員變數 `m_bCaptionText` 及 `m_bHideDisabledButtons`。

- 已將覆寫 `DeleteString` 方法新增至 `CMFCFontComboBox`。

- 已從 `CPane` 移除未使用的方法：`GetMinLength` 和 `IsLastPaneOnLastRow`。

- 已將 `CPane::GetDockSiteRow(CDockingPanesRow *)` 重新命名為 `CPane::SetDockSiteRow`。

## <a name="visual-c-2010-breaking-changes"></a>Visual C++ 2010 的重大變更

### <a name="compiler"></a>編譯器

- **auto** 關鍵字已有新的預設意義。 因為舊的意義甚少使用，所以這項變更對於大多數的應用程式沒有影響。

- 因為引進了新的 **static_assert** 關鍵字，所以您的程式碼中如有同名的識別項，將會引發名稱衝突。

- 新的 lambda 標記法支援不支援在 IDL UUID 屬性中編寫未加引號的的 GUID。

- .NET Framework 4 引進了損毀狀態例外狀況概念，亦即在此例外狀況中，處理序會處於無法復原的損毀狀態。 根據預設，您無法捕捉損毀狀態例外狀況，即使使用可捕捉所有其他例外狀況的 /EHa 編譯器選項也無法達成此目的。                 若要明確捕捉損毀狀態例外狀況，請使用 __try-\__except 陳述式。 或是套用 [HandledProcessCorruptedStateExceptions] 屬性啟用函式，以捕捉損毀狀態例外狀況。  此變更主要會影響可能需要擷取損毀狀態例外狀況的系統程式設計人員。 這八個例外狀況包括：STATUS_ACCESS_VIOLATION、STATUS_STACK_OVERFLOW、EXCEPTION_ILLEGAL_INSTRUCTION、EXCEPTION_IN_PAGE_ERROR、EXCEPTION_INVALID_DISPOSITION、EXCEPTION_NONCONTINUABLE_EXCEPTION、EXCEPTION_PRIV_INSTRUCTION、STATUS_UNWIND_CONSOLIDATE。                 如需這些例外狀況的詳細資訊，請參閱 [GetExceptionCode](/windows/desktop/Debug/getexceptioncode) 巨集。

- 相較於舊版，修改後的 `/GS` 編譯器選項會更密集地監視緩衝區滿溢狀況。 此版可能會在堆疊中插入額外安全性檢查，因而造成效能降低。 使用新的 `__declspec(safebuffers)` 關鍵字可指示編譯器，針對特定函式不要插入安全性檢查。

- 若同時使用 `/GL` (整個程式最佳化) 與 `/clr` (通用語言執行平台編譯) 編譯器選項進行編譯，將會忽略 `/GL` 選項。 變更的原因是並用這兩個編譯器所能選項的好處並不多。 此變更讓建置的效能獲得提升。

- Visual C++ 2010 預設會停用對三併詞的支援。 若要啟用三併詞的支援，可使用 `/Zc:trigraphs` 編譯器選項。 三併詞包含兩個連續的問號 ("？") 後接唯一的第三個字元。 編譯器會以對應的標點符號字元取代三併詞。 例如，編譯器會將 `??=` 三併詞取代為 '#' 字元。 若在 C 原始程式檔中使用的字元集不含某些標點符號字元的慣用圖形表示，您可改用三併詞。

- 連結器已不再支援 Windows 98 的最佳化。 若指定 `/OPT:WIN98` 或 `/OPT:NOWIN98`，`/OPT` (最佳化) 選項會產生編譯時期錯誤。

- 由 RuntimeLibrary 與 DebugInformationFormat 建置系統屬性指定的預設編譯器選項已有變更。 這些屬性預設會在 Visual C++ 第 7.0 版到 10.0 版所建立的專案中指定。 若您移轉了 Visual C++ 6.0 所建立的專案，請考慮是否要指定這些屬性的值。

- 在 Visual C++ 2010 中，RuntimeLibrary = MultiThreaded (`/MD`) 且 DebugInformationFormat = ProgramDatabase (`/Zi`)。 在 Visual C++ 9.0 中，RuntimeLibrary = MultiThreaded (`/MT`) 且 DebugInformationFormat = Disabled。

### <a name="clr"></a>CLR

- Microsoft C# 與 Visual Basic 編譯器現在都不會產生任何主要 interop 組件 (非 PIA)。 非 PIA 組件不需要部署相關的主要 interop 組件 (PIA)，就能使用 COM 類型。 取用 Visual C# 或 Visual Basic 所產生的非 PIA 組件時，必須在您參考編譯命中的 PIA 組件，才能參考使用該程式庫的任何非 PIA 組件。

### <a name="visual-c-projects-and-msbuild"></a>Visual C++ Projects 與 MSBuild

- Visual C++ 專案現在會使用 MSBuild 工具。 因此，專案檔會使用新的 XML 檔案格式與 .vcxproj 檔案後置字元。 Visual C++ 2010 會自動舊版 Visual Studio 的專案檔轉換成新的檔案格式。 現有的專案若是使用舊版的建置工具 VCBUILD.exe 或專案檔案後置字元.vcproj，便會受到影響。

- 舊版的 Visual C++ 支援延遲評估屬性工作表。 例如，父屬性工作表雖無法匯入子屬性工作表，但可使用子系中定義的變數來定義其他變數。 延遲評估讓父系在子屬性工作表匯入之前就能使用子變數。 在 Visual C++ 2010 中，因為 MSBuild 只支援早期評估，所以無法在定義專案工作表變數之前先行使用。

### <a name="ide"></a>IDE

- 此應用程式的終止對話方塊不會再結束應用程式。 在先前版本中，當 `abort()` 或 `terminate()` 函式關閉應用程式的零售版本時，C 執行階段程式庫會在主控台視窗或對話方塊中顯示應用程式終止訊息。 此訊息只顯示部分：「此應用程式要求執行階段以異常方式將其終止。 如需詳細資訊，請連絡應用程式支援小組。」 因為 Windows 會接著顯示目前的終止處理常式 (通常為 Windows 錯誤報告 (Dr.Watson) 對話方塊或 Visual Studio 偵錯工具)，讓此應用程式終止訊息顯得多餘。 自 Visual Studio 2010 起，C 執行階段程式庫不再顯示此訊息。 此外，此執行階段會造成應用程式無法在偵錯工具啟動前結束。 僅當您使用了此應用程式終止訊息的舊行為，這項中斷性變更對您才有影響。

- 僅限 Visual Studio 2010：IntelliSense 不適用於 C++/CLI 程式碼或屬性；[尋找所有參考] 不適用於本機變數；程式碼模型不會從匯入的組件擷取類型名稱，也不會將類型解析成完整名稱。

### <a name="libraries"></a>程式庫

- SafeInt 類別包含在 Visual C++ 中，而且不再需要個個別下載。 只有在您開發的類別名稱也稱為 "SafeInt" 時，此中斷性變更對您才有影響。

- 程式庫部署模型不再使用訊清單來尋找特定版本的動態連結程式庫。 取而代之地是在每個動態連結程式庫名稱中加入其版本號碼，讓您可以使用該名稱尋找程式庫。

- 在舊版的 Visual Studio 中，您可以重建執行階段程式庫。 在 Visual C++ 2010 中，您已無法再建置自己的 C 執行階段程式庫檔案。

### <a name="standard-library"></a>標準程式庫

- 其他許多標頭檔已不再自動包含 \<iterator> 標頭。 相反地，如果您需要對標頭中所定義獨立迭代器的支援，請明確包含該標頭。 現有專案若是使用舊版建置工具 VCBUILD.exe 或專案檔案後置字元 .vcproj.iterator，便會受到影響。

- \<algorithm> 標頭中的 checked_* 與 unchecked_\* 函式已移除。 然後在 \<iterator>> 標頭中，`checked_iterator` 類別已移除，並且已新增 `unchecked_array_iterator` 類別。

- 已移除 `CComPtr::CComPtr(int)` 建構函式。 該建構函式允許從 NULL 巨集建構 `CComPtr` 物件，但這並非必要，而且它也允許從非零整數產生的無意義建構。

   `CComPtr` 仍然可從 NULL (定義為 0) 建構，但若是從常值 0 以外的整數建構則會失敗。 請改為使用 **nullptr**。

- 下列 `ctype` 成員函式已移除：`ctype::_Do_narrow_s`、`ctype::_Do_widen_s`、`ctype::_narrow_s`、`ctype::_widen_s`。 若應用程式使用下列其中一個成員函式，您必須使用對應的不安全版本取代：`ctype::do_narrow`、`ctype::do_widen`、`ctype::narrow`、`ctype::widen`。

### <a name="crt-mfc-and-atl-libraries"></a>CRT、MFC 及 ATL 程式庫

- 使用者已無法再建置 CRT、MFC 及 ATL 程式庫。 例如，未提供任何適當的 NMAKE 檔案。 但使用者仍能存取這些程式庫的原始程式碼。 且描述 Microsoft 使用 MSBuild 選項來建置這些程式庫時的文件，可能會張貼在 Visual C++ 小組部落格中。

- IA64 的 MFC 支援已移除。 但仍支援 IA64 上的 CRT、 ATL。

- 序數在 MFC 模組定義 (.def) 檔案中已無法再重複使用。 此變更表示次數版本之間的序數不再不同，而且 Service Pack 及快速修正工程版本的二進位相容性將有所改進。

- 已將新虛擬函式新增至 `CDocTemplate` 類別。 這個新的虛擬函式是 [CDocTemplate 類別](../mfc/reference/cdoctemplate-class.md)。 `OpenDocumentFile` 的先前版本有兩個參數。 新版則具有三個參數。 為了支援重新啟動管理員，任何從 `CDocTemplate` 衍生的類別，都必須實作擁有三個參數的版本。 新的參數為 `bAddToMRU`。

### <a name="macros-and-environment-variables"></a>巨集與環境變數

- 環境變數 __MSVCRT_HEAP_SELECT 已不再支援。 此環境變數已予移除，而且不提供任何取代項目。

### <a name="microsoft-macro-assembler-reference"></a>Microsoft 巨集組合程式參考

- Microsoft 巨集組合程式參考編譯器移除了幾個指示詞。 移除的指示詞為 `.186`、`.286`、`.286P`、`.287`、`.8086`、`.8087` 及 `.NO87`。

## <a name="visual-c-2008-breaking-changes"></a>Visual C++ 2008 的重大變更

### <a name="compiler"></a>編譯器

- 不再支援 Windows 95、Windows 98、Windows ME 及 Windows NT 平台。 這些作業系統已從目標平台清單中移除。

- 此編譯器已不再支援多個直接關聯到 ATL 伺服器的屬性。 以下是不再支援的屬性︰

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-c-projects"></a>Visual C++ 專案

- 從舊版的 Visual Studio 升級專案時，可能須修改 WINVER 及 _WIN32_WINNT 巨集，使其大於或等於 0x0500。

- 自 Visual Studio 2008 起，[新增專案精靈] 不再提供建立 C++ SQL Server 專案的選項。 使用舊版 Visual Studio 建立的 SQL Server 專案仍可正常地編譯及運作。

- Windows API 標頭檔 Winable.h 已移除。 請改為加入 Winuser.h。

- Windows API 程式庫 Rpcndr.lib 已移除。 請改為連結 rpcrt4.lib。

### <a name="crt"></a>CRT

- 對 Windows 95、Windows 98、Windows Millennium Edition 及 Windows NT 4.0 的支援已移除。

- 以下是移除的全域變數︰

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- 下列函式已移除。 請改為使用 Windows API 函式 `GetVersion` 或 `GetVersionEx`：

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- SAL 註釋的語法已變更。 如需詳細資訊，請參閱 [SAL 註釋](../c-runtime-library/sal-annotations.md)。

- IEEE 篩選現在支援 SSE 4.1 指令集。 如需詳細資訊，請參閱 [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt。

- Visual Studio 隨附的 C 執行階段程式庫已不再使用系統 DLL msvcrt.dll。

### <a name="standard-library"></a>標準程式庫

- 對 Windows 95、Windows 98、Windows Millennium Edition 及 Windows NT 4.0 的支援已移除。

- 在定義 _HAS_ITERATOR_DEBUGGING (Visual Studio 2010 之後由[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 的偵錯模式中編譯時，應用程式現在已可斷定迭代器何時須嘗試遞增或遞減過去的基礎容器界限。

- 現在堆疊類別的成員變數 C 在宣告後會受到保護。 此成員變數先前宣告為公用。

- `money_get::do_get` 的行為已變更。 先前剖析之貨幣金額的小數位數若多於為 `frac_digits` 呼叫的小數位數，將會使用 `do_get` 全部取用。 現在，`do_get` 會在取用最多 `frac_digits` 個字元之後停止剖析。

### <a name="atl"></a>ATL

- 若不相依於 CRT，即無法建置 ATL。 在舊版 Visual Studio 中，您可以使用 #define ATL_MIN_CRT 讓 ATL 專案使用最少的 CRT。 在 Visual C++ 2008 中，無論是否定義 ATL_MIN_CRT，所有 ATL 專案都會使用最少的 CRT。

- ATL Server 程式碼基底已發行到 CodePlex 成為共用原始碼專案，且不再隨 Visual Studio 一起安裝。 atlenc.h 中的資料編碼與解碼類別，以及 atlutil.h 與 atlpath.h 中的公用程式函式與類別皆予保留，現在是 ATL 程式庫的一部分。 有幾個與 ATL Server 相關聯的檔案已不再屬於 Visual Studio 的一部分。

- 有些函式已不再包含在 DLL 中， 但仍然位於匯入程式庫。 這不會影響靜態使用函式的程式碼。 只有動態使用這些函式的程式碼才會受到影響。

- 基於安全考量，PROP_ENTRY 和 PROP_ENTRY_EX 巨集已標示為已淘汱，並會由 PROP_ENTRY_TYPE 和 PROP_ENTRY_TYPE_EX 取代。

### <a name="atlmfc-shared-classes"></a>ATL/MFC 共用類別

- 若不相依於 CRT，即無法建置 ATL。 在舊版 Visual Studio 中，您可以使用 `#define ATL_MIN_CRT` 讓 ATL 專案使用最少的 CRT。 在 Visual C++ 2008 中，無論是否定義 ATL_MIN_CRT，所有 ATL 專案都會使用最少的 CRT。

- ATL Server 程式碼基底已發行到 CodePlex 成為共用原始碼專案，且不再隨 Visual Studio 一起安裝。 atlenc.h 中的資料編碼與解碼類別，以及 atlutil.h 與 atlpath.h 中的公用程式函式與類別皆予保留，現在是 ATL 程式庫的一部分。 有幾個與 ATL Server 相關聯的檔案已不再屬於 Visual Studio 的一部分。

- 有些函式已不再包含在 DLL 中， 但仍然位於匯入程式庫。 這不會影響靜態使用函式的程式碼。 只有動態使用這些函式的程式碼才會受到影響。

### <a name="mfc"></a>MFC

- `CTime` 類別：`CTime` 類別現在接受自公元 1900 年 1 月 1 日起的日期 而不是西元 1/1/1970。

- MFC 對話方塊中控制項的定位順序：當在定位順序中插入 MFC ActiveX 控制項時，會影響 MFC 對話方塊中多個控制項的正確定位順序。 此變更修正了這個問題。

   例如建立具有 ActiveX 控制項與幾個編輯控制項的 MFC 對話方塊應用程式。 將 ActiveX 控制項置於編輯控制項的索引標籤定位中間。 啟動應用程式中，再按一下索引標籤順序位於 ActiveX 控制項之後的編輯控制項，然後按一下索引標籤。在此變更之前，焦點會從 ActiveX 控制項轉往該編輯控制項，而不會轉往索引標籤順序中的下一個編輯控制項。

- `CFileDialog` 類別：`CFileDialog` 類別的自訂範本無法自動移植到 Windows Vista。 這些範本仍可使用，但沒有額外的功能，也沒有 Windows Vista [樣式] 對話方塊的外觀。

- `CWnd` 類別和 `CFrameWnd` 類別：`CWnd::GetMenuBarInfo` 方法已移除。

   `CFrameWnd::GetMenuBarInfo` 方法現在為非虛擬方法。 如需詳細資訊，請參閱 Windows SDK 中的＜GetMenuBarInfo 函式＞。

- MFC ISAPI 支援：MFC 已不再支援透過網際網路伺服器應用程式開發介面 (ISAPI) 建置應用程式。 若要建置 ISAPI 應用程式，請直接呼叫 ISAPI 延伸模組。

- 已淘汰的 ANSI API：有幾個 MFC 方法的 ANSI 版本已淘汰。 在您後續的應用程式中，須改用這些方法的 Unicode 版本。 如需詳細資訊，請參閱＜Windows Vista 通用控制項的建置需求＞。

## <a name="visual-c-2005-breaking-changes"></a>Visual C++ 2005 的重大變更

### <a name="crt"></a>CRT

- 許多函式已標示為即將淘汰。 請參閱＜已淘汱的 CRT 函式＞。

- 許多函式現在會驗證其參數，並在提供的參數無效時停止執行。 這項驗證可中斷程式碼傳遞無效的參數，並利用函式忽略這些參數或只是傳回錯誤碼。 請參閱＜參數驗證＞。

- 現在會使用檔案描述元值 -2 指出輸出無法使用 `stdout` 及 `stderr`，例如在沒有主控台視窗的 Windows 應用程式中。 先前使用的值為 -1。 如需詳細資訊，請參閱 [_fileno](../c-runtime-library/reference/fileno.md)。

- 已移除單一執行緒的 CRT 程式庫 (libc.lib 與 libcd.lib)。 請使用多執行緒的 CRT 程式庫。 已不再支援 `/ML` 編譯器旗標。 針對多執行緒程式碼與單一執行緒程式碼的效能可能會出現大幅差異的情況新增了一些非鎖定版本的功能。

- pow, double pow(int, int) 的多載已移除，以更加貼近標準的要求。

- 有鑑於 %n 格式指定名稱本身就不安全，所以所有 printf 系列函式預設都不再提供此支援。 如果出現 %n，預設行為是叫用無效參數處理常式。 若要啟用 %n 支援，請使用 `_set_printf_count_output` (另請參閱 `_get_printf_count_output`)。

- 對於帶正負號的零，`sprintf` 現在會列印負號。

- `swprintf` 已變更為符合標準，所以現在會需要大小參數。 已淘汱沒有大小參數的 `swprintf` 形式。

- 已移除 `_set_security_error_handler`。 移除任何對該函式的呼叫。預設處理常式在處安全性錯誤上安全性更高。

- `time_t` 現在是 64 位元值 (除非定義 _USE_32BIT_TIME_T)。

- `_spawn`、`_wspawn` 函式現在會依照 C 標準的規定，在成功時保留原有的 `errno`。

- RTC 現在預設會使用寬字元。

- 浮點控制字組支援函式已淘汰，不再供以 `/CLR` 或 `/CLR:PURE` 編譯的應用程式使用。 受影響的函式包括 `_clear87`、`_clearfp`、`_control87`、`_controlfp`、`_fpreset`、`_status87`、`_statusfp`。 您可以藉由定義 _CRT_MANAGED_FP_NO_DEPRECATE 來停用已標示為即將淘汰的警告，但在 Managed 程式碼中使用這些函式可能會造成無法預期且不受支援的結果。

- 有些函式現在會傳回 const 指標。 舊的 非 const 行為可藉由定義 _CONST_RETURN 重新啟用。 受影響的函式包括：

   - memchr、wmemchr

   - strchr、wcschr、_mbschr、_mbschr_l

   - strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l

   - strrchr、wcsrchr、_mbsrchr、_mbsrchr_l

   - strstr、wcsstr、_mbsstr、_mbsstr_l

- 當連結到 Setargv.obj 或 Wsetargv.obj 之後，即使將萬用字元括上雙引號，也無法在命令列上隱藏展開的萬用字元。 如需詳細資訊，請參閱 [Expanding Wildcard Arguments](../c-language/expanding-wildcard-arguments.md) (展開萬用字元引數)。

### <a name="standard-library-2005"></a>標準程式庫 (2005)

- 例外狀況類別 (位於 \<exception> 標頭中) 已移至 `std` 命名空間。 在舊版中，此類別位於全域命名空間。 若要解決指出找不到例外狀況類別的任何錯誤，請在您的程式碼中新增下列 using 陳述式︰`using namespace std;`

- 當呼叫 `valarray::resize()` 時，`valarray` 的內容會遺失並會由預設值取代。 `resize()` 方法主要用於重新初始化 `valarray`，而不是像 vector 一樣動態增加。

- 偵錯迭代器：使用偵錯版本 C 執行階段程式庫建置的應用程式若是不正確地使用迭代器，可能會在執行階段看到判斷提示。 若要停用這些判斷提示，必須將 _HAS_ITERATOR_DEBUGGING (Visual Studio 2010 之後由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 定義為 0。 如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。

## <a name="visual-c-net-2003-breaking-changes"></a>Visual c + +.NET 2003 的重大變更

### <a name="compiler"></a>編譯器

- 定義的前置處理器指示詞現在需要右括號 (C2004)。

- 明確特製化已無法再從主要範本 ([編譯器錯誤 C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)) 中尋找範本參數。

- 受保護的成員只可透過繼承自類別 (A) (其 (n) 為([編譯器錯誤 C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md) 的成員) 之類別 (B) 的成員函式存取。

- 編譯器中改進後的協助工具現在會偵測無法存取的基底類別 ([編譯器錯誤 C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md))。

- 若解構函式及/或複製建構函式無法存取，就無法捕捉例外狀況 (C2316)。

- 函式指標已不再有任何預設引數 ([編譯器錯誤 C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md))。

- 靜態資料成員無法再透過衍生類別初始化 ([編譯器錯誤 C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md))。

- 依據標準規定不可初始化 **typedef**，且現在會產生編譯器錯誤 ([編譯器錯誤 C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md))。

- **bool** 現在是正確的類型 ([編譯器錯誤 C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md))。

- UDC 現在可以建立具有多載運算子的模稜兩可 ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md))。

- 多個運算式現在會被視為有效的 null 指標常數 ([編譯器錯誤 C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md))。

- 過去編譯器可以隱含表示的 template<> 現在必須明確存在 ([編譯器錯誤 C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md))。

- 若函式已透過範本類別特製化明確特製化，即不得在類別外部明確特製化成員函式 ([編譯器錯誤 C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md))。

- 浮動點非類型範本參數不得再使用 ([編譯器錯誤 C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md))。

- 類別範本不得作為範本類型引數使用 (C3206)。

- 包含命名空間已不再導入 Friend 函式名稱 ([編譯器錯誤 C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md))。

- 編譯器不允許巨集中有任何額外的逗點 (C4002)。

- 預設會初始化使用 form () 之初始設定式建構的 POD 類型物件 (C4345)。

- 當將相依名稱視為類型時，現在需要 typename ([編譯器警告 (層級 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md))。

- 先前被誤認為樣板特製化的函式現在已能正確辨認 (C4347)。

- 靜態資料成員無法透過衍生類別初始化 (C4356)。

- 必須先定義類別範本特製化，才能在傳回型別中加以使用 ([編譯器警告 (層級 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md))。

- 編譯器現在會回報無法存取的程式碼 (C4702)。

## <a name="see-also"></a>另請參閱

[Visual Studio 之 Visual C++ 的新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)
