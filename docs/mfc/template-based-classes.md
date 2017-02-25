---
title: "樣板架構類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 類別"
  - "陣列 [C++], 指標"
  - "陣列 [C++], 樣板架構"
  - "CArray 類別, 樣板架構類別"
  - "CList 類別, 樣板架構類別"
  - "集合類別, 樣板架構"
  - "集合, 具類型指標"
  - "CTypedPtrArray 類別, 樣板架構類別"
  - "CTypedPtrList 類別, 樣板架構類別"
  - "CTypedPtrMap 類別, 樣板架構類別"
  - "MFC 集合類別, 樣板架構"
  - "指標, 具類型的集合"
  - "簡單陣列集合類別"
  - "簡單清單集合類別"
  - "簡單樣板架構集合"
  - "樣板架構集合類別"
  - "具類型指標"
  - "具類型指標, 的集合"
  - "類型安全的集合"
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 樣板架構類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 3.0 版的型別安全樣板架構集合類別和之後。  使用這些範本建立型別安全集合較為方便，並說明比使用以範本無法更有效地提供型別安全集合類別。  
  
 MFC 預先定義樣板架構集合兩個分類:  
  
-   [簡單的陣列、清單和對應類別](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [陣列、具型別指標清單和對應](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 簡單的集合類別都是從類別衍生自 `CObject`，，因此繼承序列化、動態建立 `CObject`和其他屬性。  具型別指標集合類別要求您指定衍生自—必須是 MFC 預先定義的其中一個非樣板指標集合，例如 `CPtrList` 或 `CPtrArray`的類別。  您的新集合類別從指定的基底類別和新類別的成員函式使用封裝呼叫繼承的基底類別成員強制實施型別安全。  
  
 如需 C\+\+ 樣板的詳細資訊，請參閱《 *C\+\+ 語言參考》中的*[範本](../cpp/templates-cpp.md) 。  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 使用簡單陣列、清單和導覽範本  
 若要使用簡單的集合範本，您需要知道要使用何種資料在這些集合可以儲存，以及參數中的宣告集合。  
  
###  <a name="_core_simple_array_and_list_usage"></a> 簡單的陣列和清單使用方式  
 簡單的陣列和清單類別， [CArray](../mfc/reference/carray-class.md) 和 [CList](../mfc/reference/clist-class.md)，並採用兩個參數: *型別* 和 `ARG_TYPE`。  這些類別可以儲存任何資料型別，您可以在 *型別* 參數指定:  
  
-   基本 C\+\+ 資料型別，例如 `int`、 `char`和 **float**  
  
-   C\+\+ 結構和類別  
  
-   您定義的其他型別。  
  
 為了方便和效率，您可以使用 `ARG_TYPE` 參數指定函式引數的型別。  通常，您會為您在 *型別* 參數命名的型別的參考指定 `ARG_TYPE` 。  例如：  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/CPP/template-based-classes_1.cpp)]  
  
 第一個範例會宣告陣列， `myArray`集合，包含 `int`。  第二個範例宣告清單集合，則為 `myList`，儲存 `CPerson` 物件。  集合類別的某些成員函式採用型別由 `ARG_TYPE` 樣板參數指定的引數。  例如，類別的 `CArray`**Add** 成員函式採用 `ARG_TYPE` 引數:  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/CPP/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a> 簡單的導覽使用方式  
 簡單的對應類別， [CMap](../mfc/reference/cmap-class.md)，接受四個參數: *KEY*、 `ARG_KEY`，以及 `ARG_VALUE`*值*。  類似陣列和清單類別，對應類別可以儲存任何資料型別。  不同於陣列和清單，索引和訂單資料儲存，對應組合索引鍵和值:您在對應中的值會透過指定的值相關聯的索引鍵。  機碼參數指定使用的索引鍵資料型別存取對應中儲存的資料。  如果 *KEY 的* 型別為結構或類別， `ARG_KEY` 參數通常是 *KEY*指定之型別的參考。  *值* 參數會指定在對應中的項目型別。  如果 `ARG_VALUE` 的型別為結構或類別， `ARG_VALUE` 參數通常是對 *值*所指定之型別的參考。  例如：  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/CPP/template-based-classes_3.cpp)]  
  
 第一個範例儲存 `MY_STRUCT` 值，由 `int` 索引鍵存取它們，並以傳址方式傳回存取的 `MY_STRUCT` 項目。  第二個範例儲存 `CPerson` 值，由 `CString` 索引鍵存取以及存取的項目會傳回參考。  這個範例也可能表示簡單的通訊錄，您依照姓氏搜尋人。  
  
 由於金鑰參數屬於型別 `CString` ，並 *KEY\_TYPE* 參數屬於型別 `LPCSTR`，索引鍵對應於函式儲存為型別 `CString` 項目，但是參考 \(例如 `SetAt` 透過 `LPCSTR`型別指標。  例如：  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/CPP/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 使用輸入指標集合範本  
 若要使用輸入指標集合範本，您需要知道要使用何種資料在這些集合可以儲存，以及參數中的宣告集合。  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 輸入指標陣列和清單使用方式  
 輸入指標陣列和清單類別， [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) 和 [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，並採用兩個參數: `BASE_CLASS` 的 *型別*。  這些類別可以儲存任何資料型別，您可以在 *型別* 參數指定。  這些項目會儲存指標的其中一個非樣板集合類別衍生;您可以在 `BASE_CLASS`指定基底類別。  對於陣列，請使用 `CObArray` 或 `CPtrArray`。  如需清單，請使用 `CObList` 或 `CPtrList`。  
  
 實際上，在中，當您宣告集合以時， `CObList`假設，新類別不僅會繼承其基底類別的成員，不過，它也宣告的 Automation 其他型別安全成員函式和運算子可封裝呼叫提供型別安全給基底類別成員。  這些套件會處理所有必要的型別轉換。  例如：  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/CPP/template-based-classes_5.cpp)]  
  
 第一個範例宣告輸入指標陣列，則為 `myArray`，衍生自 `CObArray`。  陣列來儲存並傳回指標至 `CPerson` 物件 \(其中 `CPerson` 是衍生自 `CObject`的類別\)。  您可以呼叫任何 `CObArray` 成員函式，或者呼叫新的型別安全的 `GetAt` 和 `ElementAt` 函式或使用型別安全 **\[\]** 運算子。  
  
 第二個範例宣告輸入指標清單，則為 `myList`，衍生自 `CPtrList`。  清單中儲存並將指標傳回 `MY_STRUCT` 物件。  根據 `CPtrList` 的類別會儲存從 `CObject`無法取得的物件之指標使用。  `CTypedPtrList` 有一些型別安全成員函式: `GetHead`、 `GetTail`、 `RemoveHead`、 `RemoveTail`、 `GetNext`、 `GetPrev`和 `GetAt`。  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a> 輸入指標對應使用方式  
 輸入指標對應類別， [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，採用三個參數: `BASE_CLASS`、 *KEY*和 *值*。  `BASE_CLASS` 參數指定衍生新類別的類別: `CMapPtrToWord`， `CMapPtrToPtr`， `CMapStringToPtr`， `CMapWordToPtr`， `CMapStringToOb`，依此類推。  *KEY* 類似於 `CMap`型別:它指定搜尋中使用的金鑰類型。  *值* 是類似 *值* 在 `CMap`:它會指定在對應儲存物件的型別。  例如：  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/CPP/template-based-classes_6.cpp)]  
  
 第一個範例是根據 **CMapPtrToPt**的對應 r —它使用 `CString` 索引鍵對應至 `MY_STRUCT`的指標。  您可以呼叫型別安全的 `Lookup` 成員函式搜尋儲存的指標。  您可以使用 **\[\]** 運算子搜尋儲存的指標和加入，如果找不到。  請改用型別安全的 `GetNextAssoc` 函式，您可以逐一查看對應。  您也可以呼叫類別 `CMapPtrToPtr`的其他成員函式。  
  
 第二個範例是根據 **CMapStringToO**的對應 b —它使用字串索引鍵對應至預存指標到 `CMyObject` 物件。  您可以使用前面段落中所描述的相同型別安全的成員，或者您可以呼叫類別 `CMapStringToOb`的成員。  
  
> [!NOTE]
>  如果您為 *值* 參數指定 **class** 或 `struct` 型別，而不是指標或參考型別，類別或結構必須具有複製建構函式。  
  
 如需詳細資訊，請參閱 [如何將型別安全集合](../mfc/how-to-make-a-type-safe-collection.md)。  
  
## 請參閱  
 [集合](../mfc/collections.md)