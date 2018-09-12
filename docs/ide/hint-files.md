---
title: 提示檔案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca97238310c42b9a537baa4056563b25c20c617
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895223"
---
# <a name="hint-files"></a>提示檔案

「提示檔案」可協助 Visual Studio 整合式開發環境 (IDE) 解譯 Visual C++ 識別項，例如函式和巨集的名稱。 當您開啟 Visual C++ 專案時，IDE 的「剖析系統」會分析專案之每個原始程式檔中的程式碼，並收集每個識別項的相關資訊。 然後，IDE 會使用該資訊來支援 [類別檢視] 瀏覽器和**導覽列**等功能。

剖析系統是在 Visual C++ 2010 中引進，其理解 C/C++ 語法，但可能會誤譯包含巨集的陳述式。 如果巨集導致以不正確的語法撰寫原始程式碼，則可能會誤譯陳述式。 當原始程式碼經過編譯且前置處理器將[巨集識別項](../preprocessor/hash-define-directive-c-cpp.md)取代成其定義時，陳述式的語法可能會變得正確。 剖析系統不需要建置專案即可運作，因為它會使用提示檔案來解譯巨集。 因此，[類別檢視] 等瀏覽功能可立即使用。

提示檔案包含使用者可自訂的「提示」，其語法與 C/C++ 巨集定義相同。 Visual C++ 包含的內建提示檔案對於大多數專案便已足夠，但您可以建立自己的提示檔案，以改善 Visual Studio 處理識別項的方式。

> [!IMPORTANT]
> 如果您修改或新增提示檔案，您必須刪除方案中的 .sdf 檔案及 (或) VC.db 檔案，變更才會生效。

## <a name="scenario"></a>情節

假設下列程式碼位於您可以使用 [類別檢視] 瀏覽器檢查的原始程式檔中。 `STDMETHOD` 巨集宣告名為 `myMethod` 的方法，該方法接受一個參數，並將指標傳回至 **HRESULT**。

```cpp
// Source code file.
STDMETHOD(myMethod)(int parameter1);
```

下列巨集定義位於不同的標頭檔中。

```cpp
// Header file.
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall
#define HRESULT void*  
```

剖析系統無法解譯原始程式碼，因為似乎宣告了名為 `STDMETHOD` 的函式，由於該宣告具有兩個參數清單，因此語法不正確。 剖析系統不會開啟標頭檔來探索 `STDMETHOD`、`STDMETHODCALLTYPE` 和 `HRESULT` 巨集的定義。 由於剖析系統無法解譯 `STDMETHOD` 巨集，因此會忽略整個陳述式，然後繼續剖析。

剖析系統不會使用標頭檔，因為您的專案可能相依於一或多個重要的標頭檔。 如有任何標頭檔變更，剖析系統可能必須重新檢查專案中的所有標頭檔，導致 IDE 的效能變慢。 相反地，剖析系統會使用指定如何處理 `STDMETHOD`、`STDMETHODCALLTYPE` 和 `HRESULT` 巨集的提示。

如何知道您需要提示？ 如果您需要提示，應該建立哪種提示？ 需要提示的一個徵兆是，如果 [類別檢視] 中的識別項檢視與**編輯器**中的檢視不一致。 例如，[類別檢視] 可能不會顯示您已知的類別成員存在，或成員的名稱不正確。 如需解決常見問題之提示類型的詳細資訊，請參閱本主題稍後的＜哪些巨集需要提示？＞一節。

## <a name="architecture"></a>架構

提示檔案屬於實體目錄，而不是 [方案總管] 中描述的邏輯目錄。 您不需要將提示檔案新增至專案，才能讓提示檔案生效。 剖析系統只有在剖析原始程式檔時，才會使用提示檔案。

每個提示檔案都會命名為 **cpp.hint**。 因此，多個目錄可能包含一個提示檔案，但每個特定目錄中只能有一個提示檔案。

零或多個提示檔案都會影響您的專案。 如果沒有提示檔案，剖析系統會使用錯誤復原技術來忽略無法解讀的原始程式碼。 否則，剖析系統會使用下列策略來尋找及收集提示。

### <a name="search-order"></a>搜尋順序

剖析系統會依下列順序搜尋目錄中的提示檔案。

- 包含 Visual C++ 安裝套件的目錄 (**vcpackages**)。 此目錄包含描述常用系統檔案中符號的內建提示檔案，例如 **windows.h**。 因此，您的專案會自動繼承所需的大部分提示。

- 從原始程式檔根目錄到包含原始程式檔本身之目錄的路徑。 在一般 Visual C++ 專案中，根目錄會包含方案或專案檔。

   此規則的例外是，如果「停止檔案」位於原始程式檔的路徑中。 停止檔案可讓您進一步控制搜尋順序，而且是名為 **cpp.stop** 的任何檔案。 剖析系統會搜尋包含停止檔案的目錄到包含原始程式檔的目錄，而不需要從根目錄開始。 在一般專案中，您不需要停止檔案。

### <a name="hint-gathering"></a>提示收集

一個提示檔案包含零或多個「提示」。 如同 C/C++ 巨集，您可以定義或刪除提示。 也就是說，`#define` 前置處理器指示詞會建立或重新定義提示，而 `#undef` 指示詞會刪除提示。

剖析系統會依稍早所述的搜尋順序開啟每個提示檔案，將每個檔案的提示累積成一組「有效提示」，然後使用有效提示來解譯您程式碼中的識別項。

剖析系統使用下列規則來累積提示。

- 如果新提示指定尚未定義的名稱，新提示會將該名稱新增至有效提示。

- 如果新提示指定已定義的名稱，新提示會重新定義現有的提示。

- 如果新提示是指定現有有效提示的 `#undef` 指示詞，新提示會刪除現有的提示。

第一項規則表示有效提示繼承自先前開啟的提示檔案。 後兩項規則表示出現在搜尋順序後面的提示，可以覆寫出現在前面的提示。 例如，如果您在包含原始程式檔的目錄中建立提示檔案，您可以覆寫任何先前的提示。

如需如何收集提示的描述，請參閱本主題稍後的 `Example`一節。

### <a name="syntax"></a>語法

建立及刪除提示的語法，與用來建立及刪除巨集的前置處理器指示詞語法相同。 事實上，剖析系統會使用 C/C++ 前置處理器來評估提示。 如需前置處理器指示詞的詳細資訊，請參閱 [#define 指示詞 (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) 和 [#undef 指示詞 (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)。

唯一不尋常的語法項目是 `@<`、`@=` 和 `@>` 取代字串。 這些是提示檔案特定的取代字串，只能搭配「對應」巨集使用。 對應是將資料、函式或事件關聯到其他資料、函式或事件處理常式的一組巨集。 例如，`MFC` 使用對應來建立[訊息對應](../mfc/reference/message-maps-mfc.md)，而 `ATL` 使用對應來建立[物件對應](../atl/reference/object-map-macros.md)。 提示檔案特定的取代字串表示對應的開始、中間和結束項目。 唯一重要的是對應巨集的名稱。 因此，每個取代字串會刻意隱藏巨集的實作。

提示使用下列語法。

|語法|意義|
|------------|-------------|
|`#define` *hint-name* *replacement-string*<br /><br /> `#define` *hint-name* `(` *parameter*, ...`)`*replacement-string*|定義新提示或重新定義現有提示的前置處理器指示詞。 在指示詞後面，前置處理器會將原始程式碼中出現的每個 *hint-name* 取代成 *replacement-string*。<br /><br /> 第二個語法形式會定義類似函式的提示。 如果原始程式碼中出現類似函式的提示，前置處理器會先將 *replacement-string* 中出現的每個 *parameter* 取代成原始程式碼中的對應引數，再將 *hint-name* 取代成 *replacement-string*。|
|`@<`|提示檔案特定的 *replacement-string*，表示一組對應項目的開頭。|
|`@=`|提示檔案特定的 *replacement-string*，表示中間對應項目。 一個對應可以有多個對應項目。|
|`@>`|提示檔案特定的 *replacement-string*，表示一組對應項目的結尾。|
|`#undef` *hint-name*|刪除現有提示的前置處理器指示詞。 提示的名稱是由 *hint-name* 識別項提供。|
|`//` *comment*|單行註解。|
|`/*` comment `*/`|多行註解。|

## <a name="what-macros-require-a-hint"></a>哪些巨集需要提示？

某些巨集類型可能會干擾剖析系統。 本節描述可能造成問題的巨集類型，以及您可以建立來解決該問題的提示類型。

### <a name="disruptive-macros"></a>造成干擾的巨集

某些巨集會導致剖析系統誤譯原始程式碼，但可以忽略而不影響您的瀏覽體驗。 例如，原始程式碼註釋語言 ([SAL](../c-runtime-library/sal-annotations.md)) 巨集會解析為 C++ 屬性，以協助您找出程式設計 Bug。 如果您想要在瀏覽程式碼時忽略 SAL 註釋，可能需要建立隱藏註釋的提示檔案。

在下列原始程式碼中，`FormatWindowClassName()` 函式的參數類型為 `PXSTR`，而參數名稱為 `szBuffer`。 不過，剖析系統將 `_Pre_notnull_` 和 `_Post_z_` SAL 註釋誤認為參數類型或參數名稱。

**原始程式碼：**  

```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  

**策略：** Null 定義

此情況的策略是將 SAL 註釋視為不存在。 若要這樣做，請指定取代字串為 Null 的提示。 如此一來，剖析系統就會忽略註釋，而且 [類別檢視] 瀏覽器不會顯示這些註釋 (Visual C++ 包含隱藏 SAL 註釋的內建提示檔案)。  

**提示檔案：**  

```  
#define _Pre_notnull_
```  

### <a name="concealed-cc-language-elements"></a>隱藏的 C/C++ 語言項目

剖析系統誤譯原始程式碼的典型原因是，如果巨集隱藏 C/C++ [標點符號](../cpp/punctuators-cpp.md)或[關鍵字](../cpp/keywords-cpp.md)語彙基元。 也就是說，巨集可能包含成對標點符號的一半，例如 `<>`、`[]`、`{}` 和 `()`。

在下列原始程式碼中，`START_NAMESPACE` 巨集會隱藏不成對的左大括弧 (`{`)。

**原始程式碼：**  

```  
#define START_NAMESPACE namespace MyProject {
```  

**策略：** 直接複製

如果巨集的語意對瀏覽體驗很重要，請建立相當於巨集的提示。 剖析系統會將巨集解析為提示檔案中的定義。

請注意，如果原始程式檔中的巨集包含其他巨集，這些巨集只有在已位於一組有效提示時才會解譯。

**提示檔案：**  

```  
#define START_NAMESPACE namespace MyProject {
```  

### <a name="maps"></a>地圖

對應是由指定一個開始項目、一個結束項目及零或多個中間項目的巨集所組成。 剖析系統誤譯對應的原因，是因為每個對應巨集隱藏 C/C++ 語言項目，並將完整的 C/C++ 陳述式語法分散到許多不同的巨集。

下列原始程式碼會定義 `BEGIN_CATEGORY_MAP`、`IMPLEMENTED_CATEGORY` 和 `END_CATEGORY_MAP` 巨集。

**原始程式碼：**  

```  
#define BEGIN_CATEGORY_MAP(x)\
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },
#define END_CATEGORY_MAP()\
   { _ATL_CATMAP_ENTRY_END, NULL } };\
   return( pMap ); }
```  

**策略：** 識別對應項目

為對應的開始、中間 (如果有) 和結束項目指定提示。 使用特殊對應取代字串 `@<`、`@=` 和 `@>`。 如需詳細資訊，請參閱本主題中的`Syntax`一節。

**提示檔案：**  

```  
// Start of the map.
#define BEGIN_CATEGORY_MAP(x) @<
// Intermediate map element.
#define IMPLEMENTED_CATEGORY( catid ) @=
// Intermediate map element.
#define REQUIRED_CATEGORY( catid ) @=
// End of the map.
#define END_CATEGORY_MAP() @>
```  

### <a name="composite-macros"></a>複合巨集

複合巨集包含使剖析系統混淆的一或多種巨集類型。

下列原始程式碼包含指定命名空間範圍開頭的 `START_NAMESPACE` 巨集，以及指定對應開頭的 `BEGIN_CATEGORY_MAP` 巨集。

**原始程式碼：**  

```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```  

**策略：** 直接複製

建立 `START_NAMESPACE` 和 `BEGIN_CATEGORY_MAP` 巨集的提示，然後建立 `NSandMAP` 巨集的提示，如同稍早的原始程式碼所示。 或者，如果複合巨集只包含造成干擾的巨集和空白字元，您可以定義取代字串為 Null 定義的提示。

在此範例中，假設 `START_NAMESPACE` 已有提示，如本主題中的 `Concealed C/C++ Language Elements`子標題所述。 另外假設 `BEGIN_CATEGORY_MAP` 具有 `Maps`中稍早所述的提示。

**提示檔案：**  

```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```  

### <a name="inconvenient-macros"></a>不便的巨集

某些巨集可以透過剖析系統解譯，但由於巨集很長或很複雜，因此原始程式碼難以閱讀。 為了可讀性，您可以提供簡化巨集顯示的提示。

**原始程式碼：**  

```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  

**策略：** 簡化

建立顯示更簡單巨集定義的提示。

**提示檔案：**  

```  
#define STDMETHOD(methodName) void* methodName
```  

## <a name="example"></a>範例

下列範例說明如何從提示檔案累積提示。 此範例不會使用停止檔案。

下圖描述 Visual C++ 專案中的一些實體目錄。 提示檔案位於 `vcpackages`、`Debug`、`A1` 和 `A2` 目錄。

### <a name="hint-file-directories"></a>提示檔案目錄

![一般和專案專屬提示檔案目錄。](../ide/media/hintfile.png "HintFile")  

### <a name="directories-and-hint-file-contents"></a>目錄和提示檔案內容

下列清單顯示此專案中包含提示檔案的目錄，以及這些提示檔案的內容。 只會列出 `vcpackages` 目錄提示檔案中許多提示的一部分。

- vcpackages

    ```  
    // vcpackages (partial list)  
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)  
    ```  

- 偵錯

    ```  
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```  

- A1

    ```  
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```  

- A2

    ```  
    // A2
    #undef OBRACE
    #undef CBRACE
    ```  

### <a name="effective-hints"></a>有效提示

下表列出此專案中原始程式檔的有效提示。

- 原始程式檔：A1_A2_B.cpp

- 有效提示：

    ```  
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

下列注意事項適用於上述清單。

- 有效提示來自於 `vcpackages`、`Debug`、`A1` 和 `A2` 目錄。

- `Debug` 提示檔案中的 **#undef** 指示詞已移除 `vcpackages` 目錄提示檔案中的 `#define _In_` 提示。

- `A1` 目錄中的提示檔案會重新定義 `START_NAMESPACE`。

- `A2` 目錄中的 `#undef` 提示已移除 `Debug` 目錄提示檔案中的 `OBRACE` 和 `CBRACE` 提示。

## <a name="see-also"></a>另請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)    
[#define 指示詞 (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)   
[#undef 指示詞 (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)   
[SAL 註釋](../c-runtime-library/sal-annotations.md)   
[訊息對應](../mfc/reference/message-maps-mfc.md)   
[訊息對應巨集](../atl/reference/message-map-macros-atl.md)   
[物件對應巨集](../atl/reference/object-map-macros.md)