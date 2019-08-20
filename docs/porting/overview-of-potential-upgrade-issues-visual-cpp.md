---
title: 潛在升級問題概觀 (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 10c2de547611cf7b1b47de2b1ec05dcf419c6225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511549"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>潛在升級問題概觀 (Visual C++)

多年來，Microsoft C++ 編譯器經過許多變更，包括 C++ 語言本身、C++ 標準程式庫、C 執行階段 (CRT) 以及 MFC 和 ATL 這類其他程式庫。 因此，從較舊版 Visual Studio 升級應用程式時，您可能會在先前編譯無誤的程式碼中遇到編譯器和連結器錯誤及警告。 原始程式碼基底越舊，這類錯誤的可能性就越大。 本概觀摘要說明您可能會遇到的最常見問題類別，並提供更多詳細資訊的連結。

> [!NOTE]
> 以往，我們建議應一次一個版本，以累加方式執行跨越數個 Visual Studio 版本的升級。 我們不再建議這種方法。 我們發現，不論程式碼基底多舊，升級至目前 Visual Studio 版本幾乎一律較為簡單。

有關升級程序的問題或意見都可以傳送至 vcupgrade@microsoft.com。

## <a name="library-and-toolset-dependencies"></a>程式庫和工具組相依性

> [!NOTE]
> 本節適用於以 Visual Studio 2013 及更早版本建置的應用程式和程式庫。 Visual Studio 2015、Visual Studio 2017 與 Visual Studio 2019 所使用的工具組為二進位相容。 如需詳細資訊，請參閱 [Visual Studio 2015 和 Visual Studio 2019 之間的 C++ 二進位相容性](binary-compat-2015-2017.md)。

將應用程式升級至新版 Visual Studio 時，建議 (且許多情況下為必要) 您也升級應用程式所連結的所有程式庫和 DLL。 您需要具備原始程式碼的存取權，或程式庫廠商必須可以提供使用編譯器相同主要版本所編譯的新二進位檔。 如果符合其中一個條件，則您可以略過處理二進位檔相容性詳細資料的這一節。 如果非為上述情況，則可能無法在已升級的應用程式中使用程式庫。 本節中的資訊將協助您了解是否可以繼續進行升級。

### <a name="toolset"></a>Toolset

.obj 和 .lib 檔案格式定義良好並且極少變更。 有時會針對這些檔案格式進行新增，但這些新增通常不會影響較新工具組使用較舊工具組所產生的物件檔案和程式庫。 這裡的一個重要例外狀況是您使用 [/GL (整個程式最佳化)](../build/reference/gl-whole-program-optimization.md) 進行編譯。 如果您使用 `/GL` 進行編譯，則只能使用用來產生目的檔的相同工具組來連結所產生的目的檔。 因此，如果您使用 `/GL` 以及使用 Visual Studio 2017 (v141) 編譯器產生目的檔，則必須使用 Visual Studio 2017 (v141) 連結器來加以連結。 原因是目的檔的內部資料結構在工具組主要版本中不穩定，且較新工具組不了解較舊的資料格式。

C++ 沒有穩定的應用程式二進位介面 (ABI)。 但 Visual Studio 會為版本所有次要版本維持穩定的 C++ ABI。 Visual Studio 2015 (v140)、Visual Studio 2017 (v141) 和 Visual Studio 2019 (v142) 只在次要版本有所不同。 它們都有相同的主要版本號碼，也就是 14。 如需詳細資訊，請參閱 [Visual Studio 2015 和 Visual Studio 2019 之間的 C++ 二進位相容性](binary-compat-2015-2017.md)。

如果您的目的檔包含具有 C++ 連結的外部符號，則該目的檔可能未正確地連結到以不同主要工具組版本所產生的目的檔。 有許多可能的結果︰連結可能完全失敗 (例如，如果名稱裝飾已變更的話)。 連結可能成功，但執行階段可能無法運作 (例如，如果型別版面配置已變更的話)。 或者在許多情況下，可能剛好能夠運作且未發生任何錯誤。 另請注意，雖然 C++ ABI 不穩定，但是 COM 所需的 C ABI 和 C++ ABI 子集則十分穩定。

若您連結到匯入程式庫，在執行階段即會使用會保留 ABI 相容性的 Visual Studio 可轉散發程式庫之任一新版。 例如，如果您的應用程式使用 Visual Studio 2015 Update 3 工具組進行編譯及連結，則可以使用任一 Visual Studio 2017 或 Visual Studio 2019 的可轉散發套件，因為 2015、2017 與 2019 的程式庫有保留二進位的回溯相容性。 反向操作則不行：您所使用可轉散發套件版本不可早於用於建置您程式碼的工具組，即使它們有相容的 ABI 也不行。

### <a name="libraries"></a>程式庫

如果您使用特定版本的 Visual Studio C++ 程式庫標頭檔來編譯來源檔案 (方法是使用 #including 包含標頭)，則產生的目的檔必須連結到相同版本的程式庫。 因此，例如，若您使用 Visual Studio 2015 Update 3 \<immintrin.h> 編譯原始程式檔，即必須連結到 Visual Studio 2015 Update 3 vcruntime 程式庫。 同樣地，若您使用 Visual Studio 2017 15.5 版的 \<iostream> 編譯原始程式檔，即必須連結到 Visual Studio 2017 15.5 版標準 C++ 程式庫：msvcprt。 不支援混合和比對。

針對 C++ 標準程式庫，自 Visual Studio 2010 之後，已透過在標準標頭中使用 `#pragma detect_mismatch` 明確不允許混合和比對。 如果您嘗試連結不相容的物件檔案，或嘗試連結到錯誤的標準程式庫，連結將會失敗。

針對 CRT，因為 API 介面在經過一段時間後並未進行大幅變更，所以至少在 Visual Studio 2015 和通用 CRT 之前，絕不支援混合和比對，但經常可以運作。 通用 CRT 已中斷回溯相容性，因此未來我們可以維持回溯相容性。 換句話說，我們未來不想要引進新的已版本控制的通用 CRT 二進位檔。 相反地，已就地更新現有的通用 CRT。

為了提供使用舊版 Microsoft C 執行階段標頭所編譯之物件檔案 (和程式庫) 的局部連結功能，我們提供 Visual Studio 2015 和更新版本的程式庫 legacy_stdio_definitions.lib。 此程式庫提供已從通用 CRT 移除之大部分函式和資料匯出的相容性符號。 legacy_stdio_definitions.lib 所提供的相容性符號集合就足以滿足大部分的相依性，包括 Windows SDK 所含程式庫中的所有相依性。 不過，因為無法提供相容性符號，所以已從通用 CRT 移除一些符號。 這些符號包括一些函式 (例如 \_\_iob\_func) 和資料匯出 (例如 \_\_imp\_\_\_iob、\_\_imp\_\_\_pctype、\_\_imp\_\_\_mb\_cur\_max)。

如果您有使用舊版 C 執行階段標頭所建置的靜態程式庫，則建議依此順序執行下列動作︰

1. 使用新版 Visual Studio 和通用 CRT 標頭重建靜態程式庫，以支援連結到通用 CRT。 這個方法是完整支援的 (因此而為最佳) 選項。

1. 如果您無法 (或不想要) 重建靜態程式庫，請嘗試連結到 legacy\_stdio\_definitions.lib。 如果它滿足您靜態程式庫的連結時間相依性，則您會想要完整測試二進位檔中所使用的靜態程式庫，確保未受到任何[對通用 CRT 進行的行為變更](visual-cpp-change-history-2003-2015.md#BK_CRT)的不良影響。

1. 如果 legacy\_stdio\_definitions.lib 不符合靜態程式庫的相依性，或程式庫因上述行為變更而未使用通用 CRT，則建議將靜態程式庫封裝成為與正確 Microsoft C 執行階段版本所連結的 DLL。 例如，如果使用 Visual Studio 2013 來建置靜態程式庫，則也要使用 Visual Studio 2013 和 Visual Studio 2013 C++ 程式庫來建置此 DLL。 透過將程式庫建置到 DLL，可以封裝為其與特定 Microsoft C 執行階段版本之相依性的實作詳細資料。 您需要小心 DLL 介面不會洩露所使用 C 執行階段的詳細資料；例如，跨 DLL 界限傳回 FILE*，或傳回 malloc 配置的指標並預期呼叫者釋放它。

在單一程序中使用多個 CRT 不會造成問題，也不會造成本身的問題 (事實上，大部分程序最後都會載入多個 CRT DLL；例如，Windows 作業系統元件將取決於 msvcrt.dll，CLR 則取決於其專屬的私用 CRT)。 因不同 CRT 的狀態而造成混亂時，就會產生問題。 例如，您不應該使用 msvcr110.dll!malloc 來配置記憶體並嘗試使用 msvcr120.dll!free 將該記憶體解除配置，而且您不應該嘗試使用 msvcr110!fopen 來開啟 FILE 並嘗試使用 msvcr120!fread 來讀取該 FILE。 只要您不要因不同 CRT 的狀態而造成混亂，就可以放心地在單一程序中載入多個 CRT。

如需詳細資訊，請參閱[將程式碼升級至通用 CRT](upgrade-your-code-to-the-universal-crt.md)。

## <a name="errors-due-to-project-settings"></a>因專案設定而造成的錯誤

若要開始升級程序，請在最新版 Visual Studio 中開啟較舊的專案/解決方案/工作區。 Visual Studio 將會根據舊專案設定來建立新的專案。 如果較舊專案具有硬式編碼到非標準位置的程式庫和 include 路徑，則在專案使用預設設定時，編譯器可能看不到這些路徑中的檔案。 如需詳細資訊，請參閱[連結器 OutputFile 設定](porting-guide-spy-increment.md#linker_output_settings)。

一般而言，現在正是正確組織專案程式碼以簡化專案維護並協助您最快速地編譯已升級程式碼的不錯時機。 如果您的原始程式碼組織良好，而且舊的專案是使用 Visual Studio 2010 或更新版本所編譯，則可以手動編輯新的專案檔案以支援在舊和新編譯器上編譯。 下列範例示範如何針對 Visual Studio 2015 和 Visual Studio 2017 進行編譯：

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019：無法解析的外部符號

針對無法解析的符號，您可能需要修復專案設定。

- 如果原始程式檔位於非預設位置，則要新增專案 include 目錄的路徑嗎？

- 如果外部定義於 .lib 檔案中，則您是否已在專案屬性中指定 lib 路徑，且位於該處的 .lib 檔案版本是否正確？

- 嘗試連結到使用不同 Visual Studio 版本所編譯的 .lib 檔案嗎？ 如果是的話，請參閱有關程式庫和工具組相依性的上一節。

- 呼叫位置上的引數類型實際符合函式的現有多載嗎？ 確認函式簽章以及呼叫此函式之程式碼中任何 typedef 的基礎類型都是您預期的類型。

若要疑難排解無法解析的符號錯誤，您可以嘗試使用 dumpbin.exe 來檢查二進位檔中定義的符號。 請嘗試下列的命令列，檢視程式庫中定義的符號：

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t 是原生類型)

(在 Microsoft Visual C++ 6.0 和更舊版本中，**wchar_t** 並未實作為內建類型，而是在 wchar.h 中宣告為 unsigned short 的 typedef。)C++ 標準要求 **wchar_t** 必須是內建類型。 使用 typedef 版本可能會造成可攜性問題。 如果您從舊版 Visual Studio 升級，並且因程式碼嘗試以隱含方式將 **wchar_t** 轉換成 **unsigned short**而遇到編譯器錯誤 C2664，建議您變更程式碼來修正錯誤，而不是設定 `/Zc:wchar_t-`。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>使用連結器選項 /NODEFAULTLIB、/ENTRY 和 /NOENTRY 升級

`/NODEFAULTLIB` 連結器選項 (或「略過所有預設程式庫」連結器屬性) 會告訴連結器不要在預設程式庫 (例如 CRT) 中自動連結。 這表示每個程式庫都必須個別列為輸入。 此程式庫清單提供於 [專案屬性]  對話方塊之 [連結器]  區段的 [其他相依性]  屬性中。

因為部分預設程式庫的名稱已變更，所以升級時，使用此選項的專案會出現問題。 因為每個程式庫都必須列在 [其他相依性]  屬性中或連結器命令列上，所以您必須更新程式庫清單以使用所有目前名稱。

下表顯示從 Visual Studio 2015 開始其內容經變更的程式庫。 若要升級，您需要將第二個資料行中新程式庫名稱新增到第一個資料行中的程式庫。 其中部分程式庫是匯入程式庫，但應該不會有任何影響。

|||
|-|-|
|如果您是使用︰|您需要使用這些程式庫：|
|LIBCMT.lib|libcmt.lib、libucrt.lib、libvcruntime.lib|
|libcmtd.lib|libcmtd.lib、libucrtd.lib、libvcruntimed.lib|
|msvcrt.lib|msvcrt.lib、ucrt.lib、vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib、ucrtd.lib、vcruntimed.lib|

如果您使用也會略過預設程式庫的 `/ENTRY` 選項或 `/NOENTRY` 選項，則也會出現相同問題。

## <a name="errors-due-to-improved-language-conformance"></a>因改善的語言一致性而造成的錯誤

多年來，Microsot C++ 編譯器持續改善其與 C++ 標準的一致性。 因為編譯器正確地標示先前忽略或明確允許的錯誤，所以使用舊版所編譯的程式碼可能無法在較新版 Visual Studio 中編譯。

例如，在 MSVC 的歷程記錄中，`/Zc:forScope` 為早期推出的參數。 它允許不一致的迴圈變數行為。 該參數現在已被取代，可能會在未來的版本中移除。 強烈建議您不要在升級程式碼時使用該參數。 如需詳細資訊，請參閱 [/Zc:forScope- 已被取代](porting-guide-spy-increment.md#deprecated_forscope)。

您在升級時可能會看到的其中一個常見編譯器錯誤範例，是將非 const 引數傳遞至 const 參數。 舊版編譯器不一定會將其標示為錯誤。 如需詳細資訊，請參閱[編譯器的更嚴格轉換](porting-guide-spy-increment.md#stricter_conversions)。

如需特定一致性改進的詳細資訊，請參閱 [Visual C++ 2003 - 2015 的變更歷程記錄](visual-cpp-change-history-2003-2015.md)和 [Visual Studio 中的 C++ 一致性改進](../overview/cpp-conformance-improvements.md)。

## <a name="errors-involving-stdinth-integral-types"></a>涉及 \<stdint.h> 整數類型的錯誤

\<stdint.h> 標頭定義在所有平台上都一定會有所指定長度的 typedef 和巨集，這點與內建整數類型不同。 例如 `uint32_t` 和 `int64_t` 就是範例。 \<stdint.h> 標頭新增於 Visual Studio 2010。 2010 之前所撰寫的程式碼可能會提供這些類型的私用定義，而這些定義不一定是與 \<stdint.h> 定義一致。

如果錯誤是 C2371，並涉及 `stdint` 類型，可能表示類型定義於程式庫或協力廠商程式庫檔案的標頭中。 升級時，您應該排除 \<stdint.h> 類型的所有自訂定義，但請先比較自訂定義與目前標準定義，確定未造成新的問題。

您可以按下 **F12** (**移至定義**)，來查看有疑義的類型在何處定義。

這裡的 [/showIncludes](../build/reference/showincludes-list-include-files.md) 編譯器選項十分有用。 在專案的 [屬性頁面]  對話方塊中，開啟 [C/C++]   > [進階]  頁面，然後將 [顯示 Include 檔]  設為 [是]  。 然後重建您的專案，並查看輸出視窗中的 `#include` 清單。 每個標頭都會縮排在包含它的標頭下方。

## <a name="errors-involving-crt-functions"></a>涉及 CRT 函式的錯誤

多年來，已對 C 執行階段進行許多變更。 已新增許多安全版本的函式，並已移除一些函式。 此外，如本文稍早所述，已在 Visual Studio 2015 中將 Microsoft 的 CRT 實作重構為新的二進位檔和相關聯的 .lib 檔案。

如果錯誤涉及 CRT 函式，請搜尋 [Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md) 或 [Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)，以查看這些文章是否包含任何其他資訊。 如果錯誤是「LNK2019 無法解析的外部」，請確定尚未移除函式。 否則，如果您確定函式仍然存在，而且呼叫程式碼正確，請確認您的專案是否使用 `/NODEFAULTLIB`。 如果是的話，則您需要更新程式庫清單，讓專案使用新的通用 (UCRT) 程式庫。 如需詳細資訊，請參閱上方的＜程式庫和相依性＞一節。

如果錯誤涉及 `printf` 或 `scanf`，請確定您未私自定義兩者其一不含 stdio.h。 若是如此，請移除私人定義或 legacy\_stdio\_definitions.lib 的連結。 您可於 [組態屬性]   > [連結器]   > [輸入]  下的 [屬性頁]  對話方塊中，於 [其他相依性]  屬性中設定此程式庫。 如果您連結到 Windows SDK 8.1 或較舊版，則請新增 legacy\_stdio\_definitions.lib。

如果錯誤涉及格式字串引數，則原因可能是編譯器在強制執行標準方面較為嚴格。 如需詳細資訊，請參閱變更歷程記錄。 因為這裡的任何錯誤都可能代表安全性風險，所以請密切注意它們。

## <a name="errors-due-to-changes-in-the-c-standard"></a>因 C++ 標準中的變更而造成的錯誤

C++ 標準本身的發展方式不一定具有回溯相容。 在 C++11 中引進移動語意、新關鍵字以及其他語言和標準程式庫功能可能會造成編譯器錯誤，甚至會造成不同的執行階段行為。

例如，舊 C++ 程式可能包含 iostream.h 標頭。 在 C++ 歷程記錄中，此標頭已在早期淘汰，並最終從 Visual Studio 完全移除。 在此情況下，您需要使用 \<iostream> 並重寫程式碼。 如需詳細資訊，請參閱[更新舊版 iostreams 程式碼](porting-guide-spy-increment.md#updating_iostreams_code)。

### <a name="c4838-narrowing-conversion-warning"></a>C4838：縮小轉換警告

C++ 標準現在指定從不帶正負號到帶正負號整數值的轉換視為縮小轉換。 在 Visual Studio 2015 之前，編譯器並不會引發此警告。 請檢查每個出現項目，確定縮小不會影響您程式碼的正確性。

## <a name="warnings-to-use-secure-crt-functions"></a>使用安全 CRT 函式的警告

多年來，已引進安全版本的 C 執行階段函式。 雖然舊的不安全版本仍然可用，但是建議將程式碼變更成使用安全版本。 編譯器會發出使用不安全版本的警告。 您可以選擇停用或忽略這些警告。 若要停用解決方案中所有專案的警告，請開啟 [檢視]   > [屬性管理員]  ，並選取您要停用此警告的所有專案，然後以滑鼠右鍵按一下選取的項目，再選擇 [屬性]  。 在 [組態屬性]   > [C/C++]   > [進階]  下的 [屬性頁]  對話方塊中，選取 [停用特定警告]  。 按一下下拉式箭頭，然後按一下 [編輯]  。 在文字方塊中輸入 4996 (請不要包括 'C' 前置詞)。如需詳細資訊，請參閱[移植以使用安全的 CRT](porting-guide-spy-increment.md#porting_to_secure_crt)。

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>因 Windows API 或已淘汰 SDK 中的變更而造成的錯誤

多年來，已新增 Windows API 和資料類型，有時也會進行變更或移除。 同時，也提供並移除其他不屬於核心作業系統的 SDK。 因此，較舊的程式可能會包含不再存在之 API 的呼叫。 它們也可能包含其他 Microsoft SDK 中不再支援之 API 的呼叫。 如果您看到涉及來自舊版 Microsoft SDK 之 Windows API 或 API 的錯誤，則 API 可能已遭移除，並/或已取代為更新且更安全的函式。

如需目前 API 集合以及特定 Windows API 之最低支援作業系統的詳細資訊，請參閱 [Microsoft API 與參考目錄](https://msdn.microsoft.com/library)，並瀏覽至有問題的 API。

### <a name="windows-version"></a>Windows 版本

升級直接或間接使用 Windows API 的程式時，您需要決定要支援的最小 Windows 版本。 在大部分情況下，Windows 7 是不錯的選擇。 如需詳細資訊，請參閱[標頭檔問題](porting-guide-spy-increment.md#header_file_problems)。 `WINVER` 巨集會定義您的程式應執行的最舊 Windows 版本。 如果您的 MFC 程式將 WINVER 設為 0x0501 (Windows XP)，則因為 MFC 不再支援 XP，所以會收到警告，即使編譯器本身具有 XP 模式也是一樣。

如需詳細資訊，請參閱[更新目標 Windows 版本](porting-guide-spy-increment.md#updating_winver)和[更多過時的標頭檔](porting-guide-spy-increment.md#outdated_header_files)。

## <a name="atl--mfc"></a>ATL/MFC

ATL 和 MFC 是相當穩定的 API，但偶而會進行變更。 如需詳細資訊，請參閱 [Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)、[Visual Studio 中 Visual C++ 的新功能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)和 [Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)。

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 已定義於 MSVCRTD.lib 中

MFC 應用程式中可能會發生此錯誤。 這指出 CRT 程式庫與 MFC 程式庫之間的順序問題。 必須先連結 MFC，才能提供 new 和 delete 運算子。 若要修正錯誤，請使用 `/NODEFAULTLIB` 參數來忽略這些預設程式庫：MSVCRTD.lib 與 mfcs140d.lib。 然後將這些相同的程式庫新增為其他相依性。

## <a name="32-vs-64-bit"></a>32 與 64 位元

如果您的原始程式碼是針對 32 位元系統所編譯，則可以選擇建立 64 位元版本，而不是新的 32 位元應用程式，或是包含新的 32 位元應用程式。 一般而言，您應該先以 32 位元模式編譯程式，然後嘗試 64 位元。 針對 64 位元進行編譯十分簡單，但在部分情況下，它可以顯示 32 位元組建所隱藏的 Bug。

此外，您應該注意下列項目可能發生的編譯時期和執行階段問題：指標大小、時間和大小值，以及 printf 和 scanf 函式中的格式規範。 如需詳細資訊，請參閱[針對 64 位元 x64 目標設定 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md) 和 [Visual C++ 64 位元移轉時常見的問題](../build/common-visual-cpp-64-bit-migration-issues.md)。 如需其他移轉提示，請參閱 [Programming Guide for 64-bit Windows](/windows/win32/WinProg64/programming-guide-for-64-bit-windows) (64 位元 Windows 程式設計指南)。

## <a name="unicode-vs-mbcsascii"></a>Unicode 與 MBCS/ASCII

標準化 Unicode 之前，許多程式都是使用多位元組字元集 (MBCS) 代表 ASCII 字元集中未包含的字元。 在舊的 MFC 專案中，MBCS 是預設設定，在您升級這類程式時，將會看到建議改為使用 Unicode 的警告。 如果您決定轉換成 Unicode 不符合開發成本，則可以選擇停用或忽略警告。 若要在解決方案中的所有專案停用此項目，請開啟 [檢視]   > [屬性管理員]  ，並選取您要停用此警告的所有專案，然後以滑鼠右鍵按一下選取的項目，再選擇 [屬性]  。 在 [屬性頁]  對話方塊中，選取 [組態屬性]   > [C/C++]   > [進階]  。 在 [停用特定警告]  屬性中，開啟下拉式箭頭並選擇 [編輯]  。 在文字方塊中輸入 4996 (請不要包括 'C' 前置詞)。選擇 [確定]  儲存屬性，然後選擇 [確定]  儲存變更。

如需詳細資訊，請參閱[從 MBCS 移植到 Unicode](porting-guide-spy-increment.md#porting_to_unicode)。 如需 MBCS 與Unicode 的一般資訊，請參閱 [Visual C++ 中的文字和字串](../text/text-and-strings-in-visual-cpp.md)和[國際化](../c-runtime-library/internationalization.md)。

## <a name="see-also"></a>另請參閱

[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)