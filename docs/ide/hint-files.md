---
title: "提示檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cpp.hint"
  - "vc.hint.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "停止檔案"
  - "cpp.hint"
  - "提示檔案"
  - "cpp.stop"
  - "類別檢視, 提示檔案"
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提示檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A *提示檔案* 可協助 Visual Studio 整合式的開發環境 (IDE) 解譯 Visual c + + 識別項，例如函式和巨集的名稱。 當您開啟的 Visual c + + 專案，在 IDE 的 *剖析系統* 會分析每個原始程式檔中的專案中的程式碼，並收集每個識別項的相關資訊。 然後 IDE 使用該資訊來支援功能，例如 **類別檢視** 瀏覽器和 **導覽列**。  
  
 剖析的系統中導入 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)], ，了解 C/c + + 語法，但可以錯誤解譯包含巨集的陳述式。 如果巨集造成原始程式碼所寫的語法不正確，可能會誤譯陳述式。 陳述式可能會變得語法正確時編譯的原始程式碼，並取代 preprocesser [巨集識別項](../preprocessor/hash-define-directive-c-cpp.md) 與其定義。 剖析系統的運作而不必建置專案，因為它使用提示檔案來解譯巨集。 因此，瀏覽這類功能 **類別檢視** 立即使用。  
  
 提示檔案包含使用者自訂 *提示*, ，其中有 C/c + + 巨集定義與相同的語法。 Visual c + + 包含內建提示的檔案，足以應付大部分的專案，但您可以建立您自己的提示檔案，以改善 Visual Studio 處理識別項的方式。  
  
> [!IMPORTANT]
>  如果您修改或新增提示檔案，您必須刪除.sdf 檔案及/或 VC.db 檔案在方案中，變更才會生效。  
  
## <a name="scenario"></a>情節  
 假設下列程式碼是在原始程式檔與檢查 **類別檢視** 瀏覽器。  `STDMETHOD` 巨集宣告方法，名為 `myMethod` 採用一個參數，並傳回指標 **HRESULT**。  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 下列巨集定義是在不同的標頭檔中。  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 剖析系統無法解譯原始碼，因為名為 STDMETHOD 函式宣告，與該宣告的語法不正確，因為它有兩個參數清單。 剖析系統不會開啟來探索的定義標頭檔 `STDMETHOD`, ，`STDMETHODCALLTYPE`, ，和 `HRESULT` 巨集。 因為無法解譯剖析系統 `STDMETHOD` 巨集，它會忽略整個陳述式，然後再繼續執行剖析。  
  
 剖析的系統未使用的標頭檔，因為您的專案可能相依於一或多個重要的標頭檔。 如果任何標頭檔變更時，剖析系統可能必須重新檢查所有標頭檔，在您的專案中的 IDE 效能變慢。 相反地，剖析系統會使用指定的處理方式的提示 `STDMETHOD`, ，`STDMETHODCALLTYPE`, ，和 `HRESULT` 巨集。  
  
 如何知道您需要提示？ 如果您需要一個提示，類型應該您建立及嗎？ 提示所需的一個符號是如果在識別項的檢視 **類別檢視** 不一致的檢視與 **編輯器**。 例如， **類別檢視** 可能會的顯示您所知道的類別成員存在，或成員的名稱不正確。 如需解決常見的問題的提示類型的詳細資訊，請參閱什麼巨集需要提示嗎？本主題稍後的章節。  
  
## <a name="architecture"></a>架構  
 提示檔案相關的實體目錄，非邏輯的目錄中 **方案總管] 中**。 您沒有將提示檔案新增至您的專案，使影響提示檔案。 它會剖析原始程式檔時，才剖析系統就會使用提示檔案。  
  
 每個提示檔案命名為 **cpp.hint**。 因此，許多目錄可以包含提示檔案，但只有一個提示檔案可能會發生在特定的目錄。  
  
 您的專案可能會受到零或多個提示檔案。 如果沒有提示檔案，剖析系統會使用錯誤復原技術來略過無法解讀原始程式碼。 否則，剖析系統會使用下列策略，才能找到且收集提示。  
  
### <a name="search-order"></a>搜尋順序  
 剖析系統會依下列順序搜尋提示檔案目錄。  
  
-   Visual c + + 包含安裝套件的目錄 (**vcpackages**)。 此目錄包含內建提示檔案，例如描述常用的系統檔案中的符號 **windows.h**。 因此，您的專案會自動繼承大部分的所需的提示。  
  
-   包含原始程式檔本身的目錄路徑的原始程式檔的根目錄中。 在一般的 Visual c + + 專案中，目錄的根目錄會包含方案或專案檔。  
  
     此規則的例外是如果 *停止檔案* 原始程式檔的路徑。 停止檔案提供其他控制搜尋順序，是任何檔案，名為 **cpp.stop**。 而不是從根目錄開始，剖析系統會搜尋包含停止檔案至目錄，其中包含原始程式檔的目錄。 在典型的專案，您不需要停止檔案。  
  
### <a name="hint-gathering"></a>提示蒐集  
 提示檔案包含零或多個 *提示*。 提示是定義，或刪除就像 C/c + + 巨集。 也就是 `#define` 前置處理器指示詞會建立或重新定義的提示，而 `#undef` 指示詞會刪除提示。  
  
 剖析系統每個提示檔案中開啟稍早所述的搜尋順序，每個檔案的提示累積成一組 *有效提示*, ，然後使用有效的提示來解譯您的程式碼中的識別項。  
  
 剖析系統會使用下列規則來累積提示。  
  
-   如果新的提示會指定未定義的名稱，新的提示就會將名稱加入至有效的提示。  
  
-   如果新的提示指定已定義的名稱，新的提示重新定義現有的提示。  
  
-   如果是新的提示 `#undef` 指示詞指定現有的有效提示時，新的提示會刪除現有的提示。  
  
 第一個規則表示有效的提示都繼承自先前開啟的提示檔案。 最後兩個規則表示稍後在搜尋順序中發生的提示，可以覆寫先前發生的提示。 例如，您可以覆寫任何先前的提示您建立提示檔案中包含原始程式檔的目錄。  
  
 描述如何蒐集提示，請參閱 `Example` 本主題稍後的章節。  
  
### <a name="syntax"></a>語法  
 建立和刪除的前置處理器指示詞，來建立和刪除巨集與相同的語法與提示。 事實上，剖析系統會使用 C/c + + 前置處理器評估之提示。 如需有關前置處理器指示詞的詳細資訊，請參閱 [#define 指示詞 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md) 和 [#undef 指示詞 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)。  
  
 唯一不尋常的語法項目是 `@<`, ，`@=`, ，和 `@>` 取代字串。 這些是只能搭配的提示檔案特定的取代字串 *對應* 巨集。 對應是一組資料、 函數或事件與其他資料、 函數或事件處理常式的巨集。 例如， `MFC` 使用對應來建立 [訊息對應](../mfc/reference/message-maps-mfc.md), ，和 `ATL` 使用對應來建立 [物件對應](../atl/reference/object-map-macros.md)。 提示檔案特定的取代字串表示、 中級、 左右對應的項目。 只對應巨集的名稱很重要。 因此，每個取代字串會刻意隱藏巨集的實作。  
  
 提示會使用下列語法。  
  
|語法|意義|  
|------------|-------------|  
|`#define` *提示名稱* *取代字串*<br /><br /> `#define` *提示名稱* `(` *參數*, ，...`)`*取代字串*|Preprocesser 指示詞定義新的提示，或重新定義現有的提示。 之後在指示詞，前置處理器會取代每個 *提示名稱* 來源的程式碼中 *取代字串*。<br /><br /> 第二種語法形式會定義類似函式的提示。 如果在原始碼，就會發生類似函式的提示，前置處理器首先會取代每個 *參數* 中 *取代字串* 使用對應的引數中的原始程式碼，然後按一下 [取代 *提示名稱* 與 *取代字串*。|  
|`@<`|提示檔案特定 *取代字串* ，表示一組地圖元素的開頭。|  
|`@=`|提示檔案特定 *取代字串* ，指出中繼對應項目。 地圖可以擁有多個地圖元素。|  
|`@>`|提示檔案特定 *取代字串* ，表示一組地圖元素的結尾。|  
|`#undef` *提示名稱*|前置處理器指示詞會刪除現有的提示。 此提示的名稱由 *提示名稱* 識別項。|  
|`//` *註解*|單行註解。|  
|`/*` *註解* `*/`|多行註解。|  
  
## <a name="what-macros-require-a-hint"></a>什麼巨集需要提示嗎？  
 剖析系統可能會影響特定類型的巨集。 本章節描述可能會造成問題，巨集的類型以及可解決此問題，您可以建立提示的類型。  
  
### <a name="disruptive-macros"></a>干擾性的巨集  
 一些巨集，會導致錯誤解譯來源程式碼、 剖析的系統，但可以忽略不損害您的瀏覽經驗。 例如，原始程式碼註釋語言 ([SAL](../c-runtime-library/sal-annotations.md)) 巨集解析 c + + 屬性可協助您尋找程式設計錯誤。 如果您想要忽略 SAL 註釋，當您瀏覽程式碼，您可能要建立提示檔案，會隱藏註解。  
  
 在下列的來源程式碼、 參數型別為 `FormatWindowClassName()` 函式是 `PXSTR`, ，且參數名稱為 `szBuffer`。 不過，剖析的系統錯誤 `_Pre_notnull_` 和 `_Post_z_` SAL 註釋的參數類型或參數名稱。  
  
 **原始程式碼︰**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **策略︰** Null 定義  
  
 在此情況下的策略是在處理時，它們不存在的 SAL 註釋。 若要這樣做，請指定提示的取代字串會是 null。 因此，剖析系統會忽略註解，而 **類別檢視** 瀏覽器不會顯示它們。 （visual c + + 包含隱藏 SAL 註釋的內建提示檔案）。  
  
 **提示檔案︰**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>隱藏的 C/c + + 語言項目  
 剖析系統 misinterprets 原始程式碼的一般原因是，如果巨集將會隱藏 C/c + + [標點符號](../cpp/punctuators-cpp.md) 或 [關鍵字](../cpp/keywords-cpp.md) 語彙基元。 也就是巨集可能包含一半的標點符號，一如 `<>`, ，`[]`, ，`{}`, ，和 `()`。  
  
 在下列的來源程式碼、 `START_NAMESPACE` 巨集會隱藏未配對的左大括號 (`{`)。  
  
 **原始程式碼︰**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **策略︰** 直接複製  
  
 如果巨集的語意 （semantics） 非常重要的瀏覽經驗，建立完全相同的巨集的提示。 剖析系統會解析成提示檔案中定義的巨集。  
  
 請注意，是否原始程式檔中的巨集包含其他巨集，這些巨集解譯已組有效的提示時，才。  
  
 **提示檔案︰**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>對應  
 對應巨集，以指定起始的項目、 結束的項目和零個或多個中繼項目所組成。 剖析系統 misinterprets 對應，因為每個對應巨集隱藏 C/c + + 語言項目，而且完整的 C/c + + 陳述式的語法分散在許多不同的巨集。  
  
 下列的原始程式碼定義 `BEGIN_CATEGORY_MAP`, ，`IMPLEMENTED_CATEGORY`, ，和 `END_CATEGORY_MAP` 巨集。  
  
 **原始程式碼︰**  
  
```  
#define BEGIN_CATEGORY_MAP(x)\  
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\  
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {  
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },  
#define END_CATEGORY_MAP()\  
   { _ATL_CATMAP_ENTRY_END, NULL } };\  
   return( pMap ); }  
```  
  
 **策略︰** 識別對應項目  
  
 指定提示開始、 中間 （如果有的話） 和 end 對應的項目。 使用特殊的對應取代字串 `@<`, ，`@=`, ，和 `@>`。 如需詳細資訊，請參閱 `Syntax` 本主題。  
  
 **提示檔案︰**  
  
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
 複合巨集包含一或多個混淆剖析系統巨集的類型。  
  
 包含下列原始程式碼 `START_NAMESPACE` 巨集，指定命名空間範圍的開始日期，而 `BEGIN_CATEGORY_MAP` 巨集，指定對應的開始。  
  
 **原始程式碼︰**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **策略︰** 直接複製  
  
 建立提示 `START_NAMESPACE` 和 `BEGIN_CATEGORY_MAP` 巨集，然後再建立提示 `NSandMAP` 巨集，如先前所示的原始碼相同。 或者，如果複合巨集包含只具有干擾性的巨集和空格，您可以定義其取代字串會是 null 定義的提示。  
  
 在此範例中，假設 `START_NAMESPACE` 已經有提示，如本主題中所述 `Concealed C/C++ Language Elements` 子標題。 並假設 `BEGIN_CATEGORY_MAP` 在稍早所述，有提示 `Maps`。  
  
 **提示檔案︰**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>很不方便的巨集  
 一些巨集可以解譯剖析的系統，但原始碼很難閱讀，因為巨集會太長或太複雜。 為了方便閱讀，您可以提供簡化的巨集顯示的提示。  
  
 **原始程式碼︰**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **策略︰** 簡化  
  
 建立會顯示簡單的巨集定義的提示。  
  
 **提示檔案︰**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>範例  
 下列範例說明如何提示就會累積從提示檔案。 停止檔案不會在此範例中使用。  
  
 下圖顯示一些 Visual c + + 專案中的實體目錄。 提示檔案位於 `vcpackages`, ，`Debug`, ，`A1`, ，和 `A2` 目錄。  
  
### <a name="hint-file-directories"></a>提示檔案目錄  
 ![一般和專案 &#45; 特定提示檔案目錄。](../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>目錄和提示檔案內容  
 下列清單會顯示此專案包含提示檔案，並提示檔案的內容中的目錄。 只有部分中的許多提示 `vcpackages` 列出目錄提示檔案。  
  
-   vcpackages  
  
    ```  
    // vcpackages (partial list)  
    #define _In_  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    ```  
  
-   偵錯  
  
    ```  
    // Debug  
    #undef _In_  
    #define OBRACE {  
    #define CBRACE }  
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {  
    #define END_NAMESPACE }  
    ```  
  
-   A1  
  
    ```  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {  
    ```  
  
-   A2  
  
    ```  
    // A2  
    #undef OBRACE  
    #undef CBRACE  
    ```  
  
### <a name="effective-hints"></a>有效的提示  
 下表列出此專案中的來源檔案的有效提示。  
  
-   原始程式檔︰ A1_A2_B.cpp  
  
-   有效的提示︰  
  
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
  
 下列的資訊適用於先前的清單。  
  
-   有效的提示會從 `vcpackages`, ，`Debug`, ，`A1`, ，和 `A2` 目錄。  
  
-    **#Undef** 指示詞 `Debug` 提示檔案移除 `#define _In_` 提示在 `vcpackages` 目錄提示檔案。  
  
-   提示檔案中的 `A1` 目錄重新定義 `START_NAMESPACE`。  
  
-    `#undef` 提示在 `A2` 目錄中移除的提示 `OBRACE` 和 `CBRACE` 中 `Debug` 目錄提示檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual c + + 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [建立和控制環境視窗](../Topic/Creating%20and%20Controlling%20Environment%20Windows.md)   
 [#define 指示詞 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef 指示詞 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)   
 [SAL 註釋](../c-runtime-library/sal-annotations.md)   
 [訊息對應](../mfc/reference/message-maps-mfc.md)   
 [訊息對應巨集](../atl/reference/message-map-macros-atl.md)   
 [物件對應巨集](../atl/reference/object-map-macros.md)