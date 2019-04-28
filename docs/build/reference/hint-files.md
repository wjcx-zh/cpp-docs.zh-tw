---
title: 提示檔案
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: 3d8b3be76fea454ed3b3dd3fd2a44174f34c065c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291880"
---
# <a name="hint-files"></a>提示檔案

「提示檔案」包含巨集，可能會另外造成 C++ 瀏覽資料庫剖析器跳過程式碼區域。 當您開啟 Visual C++ 專案時，剖析器會分析專案內每個來源檔案中的程式碼，以及建置含有所有識別項資訊的資料庫。 IDE 會使用該資訊來支援程式碼瀏覽功能，例如 [類別檢視] 瀏覽器和 [導覽列] 等功能。

C++ 瀏覽資料庫剖析器為模糊剖析器，可在短時間內剖析大量程式碼。 他速度快的其中一個原因是它會跳過區塊的內容。 比方說，它僅會記錄函式的位置及參數，並略過其內容。 某些巨集會導致用來判斷區塊起訖位置的啟發學習法發生問題。 而這些問題會造成不正確地記錄程式碼區域。

這些跳過的區域會以不同方式呈現：

- [類別檢視]、[前往] 及 [導覽列] 中遺漏的類型及函式

- [導覽列] 中的錯誤範圍

- 對已定義函式之 [建立宣告/定義] 的建議

提示檔案包含使用者可自訂的提示，其語法與 C/C++ 巨集定義相同。 Visual C++ 包含足夠供大部分專案使用的內建提示檔案。 不過，您可建立自己的提示檔案，來專門為您的專案改進剖析器。

> [!IMPORTANT]
> 若您修改或新增提示檔案，則必須採取額外的步驟才能讓變更生效：
> - 在 Visual Studio 2017 15.6 版以前的版本中：刪除所有變更之解決方案中的 .sdf 檔案及 (或) VC.db 檔案。
> - 在 Visual Studio 2017 15.6 到 15.9 版中：新增提示檔案後，關閉再重新開啟解決方案。

## <a name="scenario"></a>情節

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

若沒有提示檔案，`Function` 就不會在 [類別檢視]、[前往] 或 [導覽列] 中顯示。 新增具有此巨集定義的提示檔案後，剖析器現在可了解及取代 `NOEXCEPT` 巨集，讓其能夠正確地剖析函式：

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>造成干擾的巨集

中斷剖析器的巨集有兩種：

- 封裝會修飾函式之關鍵字的巨集

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   對於這些類型的巨集，提示檔案中僅需要其巨集名稱：

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- 包含不對稱括弧的巨集

   ```cpp
   #define BEGIN {
   ```

   對於這些類型的巨集，提示檔案中需要同時有該巨集的名稱及其內容：

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>編輯器支援

從 Visual Studio 2017 15.8 版起，皆包含可找出干擾性巨集的數個功能：

- 醒目提示區域內剖析器所跳過的巨集。

- 您可使用快速動作建立包含醒目提示巨集的提示檔案，如果有現有的提示檔案，也可將巨集新增到該提示檔案。

![醒目提示的巨集。](media/hint-squiggle-and-actions.png "提示波浪線及快速動作")

在執行其中一個快速動作後，剖析器就會重新剖析提示檔案所影響的檔案。

根據預設，會將問題巨集醒目提示為建議。 醒目提示可變更為更顯眼的樣式，例如紅色或綠色波浪線。 使用 [工具] > [選項] > [文字編輯器] > [C/C++] > [檢視] 下 [程式碼波浪線] 區段中的 [已跳過瀏覽區域中的巨集] 選項。

![[已跳過瀏覽區域中的巨集] 選項。](media/skipped-regions-squiggle-option.png "已跳過區域波浪線選項。")

## <a name="display-browsing-database-errors"></a>顯示瀏覽資料庫錯誤

[專案] > [顯示瀏覽資料庫錯誤] 功能表命令，會在 [錯誤清單] 中顯示無法剖析的所有區域。 此命令用來簡化建置初始提示檔案的過程。 不過，剖析器無法判斷錯誤是否為干擾性巨集所致，因此您必須評估每個錯誤。 執行 [顯示瀏覽資料庫錯誤] 命令，然後巡覽至各個錯誤，以在編輯器中載入受影響的檔案。 檔案載入後，若區域內有巨集，就會予以醒目提示。 您可叫用快速動作將其新增至提示檔案。 更新提示檔案後，就會自動更新錯誤清單。 或者，若您要手動修改提示檔案，可使用 [重新掃描解決方案] 命令來觸發更新。

## <a name="architecture"></a>架構

提示檔案與實體目錄相關，而非顯示於 [方案總管] 中的邏輯目錄。 您不必將提示檔案新增至專案，就能讓提示檔案生效。 剖析系統只有在剖析原始程式檔時，才會使用提示檔案。

每個提示檔案都會命名為 **cpp.hint**。 多個目錄可能包含一個提示檔案，但特定目錄中只能有一個提示檔案。

零或多個提示檔案都會影響您的專案。 如果沒有提示檔案，剖析系統會使用錯誤復原技術來忽略無法解讀的原始程式碼。 否則，剖析系統會使用下列策略來尋找及收集提示。

### <a name="search-order"></a>搜尋順序

剖析系統會依下列順序搜尋目錄中的提示檔案。

- 包含 Visual C++ 安裝套件的目錄 (**vcpackages**)。 此目錄包含描述常用系統檔案中符號的內建提示檔案，例如 **windows.h**。 因此，您的專案會自動繼承所需的大部分提示。

- 從原始程式檔根目錄到包含原始程式檔本身之目錄的路徑。 在一般 Visual C++ 專案中，根目錄會包含方案或專案檔。

   此規則的例外是，如果「停止檔案」位於原始程式檔的路徑中。 停止檔案是任何名為 **cpp.stop** 的檔案。 停止檔案可讓您進一步控制搜尋順序。 剖析系統會搜尋包含停止檔案的目錄到包含原始程式檔的目錄，而不需要從根目錄開始。 在一般專案中，您不需要停止檔案。

### <a name="hint-gathering"></a>提示收集

一個提示檔案包含零或多個「提示」。 如同 C/C++ 巨集，您可以定義或刪除提示。 也就是說，`#define` 前置處理器指示詞會建立或重新定義提示，而 `#undef` 指示詞會刪除提示。

剖析系統會以上述的搜尋順序開啟各提示檔案。 其會將每個檔案的提示累積成一組「有效提示」，然後使用該有效提示解譯您程式碼中的識別項。

剖析系統會使用這些規則來累積提示：

- 如果新提示指定尚未定義的名稱，則新提示會將該名稱新增至有效提示。

- 如果新提示指定已定義的名稱，新提示會重新定義現有的提示。

- 如果新提示是指定現有有效提示的 `#undef` 指示詞，新提示會刪除現有的提示。

第一項規則表示有效提示繼承自先前開啟的提示檔案。 後兩項規則表示在搜尋順序後面的提示，可以覆寫前面的提示。 例如，如果您在包含原始程式檔的目錄中建立提示檔案，您可以覆寫任何先前的提示。

如需如何收集提示的描述，請參閱[範例](#example)一節。

### <a name="syntax"></a>語法

您用來建立及刪除提示的語法，與前置處理器指示詞用來建立及刪除巨集的語法相同。 事實上，剖析系統會使用 C/C++ 前置處理器來評估提示。 如需前置處理器指示詞的詳細資訊，請參閱 [#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) 和 [#undef 指示詞 (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)。

唯一不尋常的語法項目是 `@<`、`@=` 和 `@>` 取代字串。 這些提示檔案專用的取代字串僅能在「對應」巨集中使用。 對應是將資料、函式或事件關聯到其他資料、函式或事件處理常式的一組巨集。 例如，`MFC` 使用對應來建立[訊息對應](../../mfc/reference/message-maps-mfc.md)，而 `ATL` 使用對應來建立[物件對應](../../atl/reference/object-map-macros.md)。 提示檔案專用的取代字串會標記對應的開始、中間和結束元素。 唯一重要的是對應巨集的名稱。 因此，每個取代字串會刻意隱藏巨集的實作。

提示會使用此語法：

|語法|意義|
|------------|-------------|
|`#define` *hint-name* *replacement-string*<br /><br /> `#define` *hint-name* `(` *parameter*, ...`)`*replacement-string*|定義新提示或重新定義現有提示的前置處理器指示詞。 在指示詞後面，前置處理器會將原始程式碼中出現的每個 *hint-name* 取代成 *replacement-string*。<br /><br /> 第二個語法形式會定義類似函式的提示。 如果原始程式碼中出現類似函式的提示，前置處理器會先將 *replacement-string* 中出現的每個 *parameter* 取代成原始程式碼中的對應引數，再將 *hint-name* 取代成 *replacement-string*。|
|`@<`|提示檔案特定的 *replacement-string*，表示一組對應項目的開頭。|
|`@=`|提示檔案特定的 *replacement-string*，表示中間對應項目。 一個對應可以有多個對應項目。|
|`@>`|提示檔案特定的 *replacement-string*，表示一組對應項目的結尾。|
|`#undef` *hint-name*|刪除現有提示的前置處理器指示詞。 提示的名稱是由 *hint-name* 識別項提供。|
|`//` *comment*|單行註解。|
|`/*` *comment* `*/`|多行註解。|

## <a name="example"></a>範例

此範例說明如何從提示檔案累積提示。 此範例不會使用停止檔案。

此圖說明 Visual C++ 專案中的一些實體目錄。 提示檔案位於 `vcpackages`、`Debug`、`A1` 和 `A2` 目錄。

### <a name="hint-file-directories"></a>提示檔案目錄

![一般和專案專屬提示檔案目錄。](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>目錄和提示檔案內容

這個清單顯示此專案中包含提示檔案的目錄，以及這些提示檔案的內容。 僅列出 `vcpackages` 目錄提示檔案中，許多提示的一部分：

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- 偵錯

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>有效提示

此表列出這個專案中來源檔案的有效提示：

- 原始程式檔：A1_A2_B.cpp

- 有效提示：

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

這些注意事項適用於上述清單：

- 有效提示來自於 `vcpackages`、`Debug`、`A1` 和 `A2` 目錄。

- `Debug` 提示檔案中的 **#undef** 指示詞已移除 `vcpackages` 目錄提示檔案中的 `#define _In_` 提示。

- `A1` 目錄中的提示檔案會重新定義 `START_NAMESPACE`。

- `A2` 目錄中的 `#undef` 提示已移除 `Debug` 目錄提示檔案中的 `OBRACE` 和 `CBRACE` 提示。

## <a name="see-also"></a>另請參閱

[為 Visual C++ 專案建立的檔案類型](file-types-created-for-visual-cpp-projects.md)<br>
[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef 指示詞 (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[SAL 註釋](../../c-runtime-library/sal-annotations.md)<br>

