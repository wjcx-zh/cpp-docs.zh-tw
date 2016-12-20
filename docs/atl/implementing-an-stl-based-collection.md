---
title: "Implementing an STL-Based Collection | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICollectionOnSTLImpl interface"
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing an STL-Based Collection
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 提供 `ICollectionOnSTLImpl` 介面可讓您快速地實作標準樣板程式庫 \(STL\) \(STL\) \-在您的物件架構集合介面。  若要了解這個類別的運作方式，使用這個類別會實作唯讀集合以為目標的 Automation 用戶端的您透過簡單範例 \(請參閱下\) 將工作。  
  
 範例程式碼是從 [ATLCollections 範例](../top/visual-cpp-samples.md)。  
  
 若要完成這個程序，您預期:  
  
-   [產生新的簡單物件](#vccongenerating_an_object)。  
  
-   產生之介面的[編譯 IDL 檔案](#vcconedit_the_idl) 。  
  
-   描述如何儲存項目集合，以及它們如何的[建立五個 typedef](#vcconstorage_and_exposure_typedefs) 要公開給用戶端透過 COM 介面。  
  
-   [建立複製原則類別的兩個 typedef](#vcconcopy_classes)。  
  
-   [建立列舉值和集合實作的 typedef](#vcconenumeration_and_collection)。  
  
-   [編輯精靈產生的 C\+\+ 程式碼使用集合 typedef](#vcconedit_the_generated_code)。  
  
-   [加入程式碼以填入集合。](#vcconpopulate_the_collection)。  
  
##  <a name="vccongenerating_an_object"></a> 產生新的簡單物件  
 建立新的專案，以確定清除應用程式設定中的屬性方塊。  使用 ATL 加入類別對話方塊和加入簡單物件精靈產生呼叫 `Words`簡單的物件。  確定呼叫 `IWords` 的雙重介面產生。  產生之類別的物件將用來表示文字 \(例如字串\) 的集合。  
  
##  <a name="vcconedit_the_idl"></a> 編譯 IDL 檔案  
 現在，請開啟 IDL 檔案並加入必要的三個屬性將 `IWords` 唯讀集合介面，如下所示:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/CPP/implementing-an-stl-based-collection_1.idl)]  
  
 這是設計的唯讀集合介面的標準格式會設想 Automation 用戶端。  在這個介面定義的編號註解對應於下方註解:  
  
1.  因為 Automation 用戶端透過 **IDispatch::Invoke**，存取 `_NewEnum` 屬性集合介面通常是重複的。  不過，自動化用戶端可以透過 vtable 存取其餘的方法，如此，雙重介面最好分配介面。  
  
2.  如果為雙重介面或分配介面不是擴充在執行階段 \(也就是您將不會傳遞 **IDispatch::Invoke**提供額外的方法或屬性\)，您應該套用 **nonextensible** 屬性加入至您的定義。  這個屬性可讓 Automation 用戶端執行完整的程式碼驗證在編譯時期。  在這個案例中，介面不應該是擴充的。  
  
3.  如果想要自動化用戶端可以使用這個屬性，正確的 DISPID 是很重要的。  \(請注意只有在 **DISPID\_NEWENUM**的一個底線字元\)。  
  
4.  您可以提供所有值做為 **項目** 屬性的 DISPID。  不過， **項目** 通常會使用 **DISPID\_VALUE** 成為預設屬性集合。  這可讓 Automation 用戶端參考屬性，而不需明確將它命名為。  
  
5.  用來 **項目** 屬性之傳回值的資料型別是儲存在集合中之項目的型別，因為 COM 用戶端而言。  介面會傳回字串，因此，您應該使用標準 COM 資料型別， `BSTR`。  簡而言之，因為您將會看到您在不同的格式可以內部儲存資料。  
  
6.  用來 **計數** 屬性的 DISPID 的值完全沒有限制。  這個屬性沒有標準的 DISPID。  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> 建立儲存和公開的 Typedefs  
 一旦集合介面定義，您必須決定要如何儲存資料時，資料，以及如何透過列舉值公開。  
  
 一些 typedef 的形式，這些問題的答案可提供，您可以在標頭檔頂端附近剛建立的類別將:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/CPP/implementing-an-stl-based-collection_2.h)]  
  
 在這個案例中，您會將資料儲存為 **std::string**s. **std::vector** 。  **std::vector** 是像 Managed 陣列的 STL 容器類別。  **std::string** 就是 Standard C\+\+ 程式庫字串類別。  這些類別可讓您輕鬆地使用字串的集合搭配使用。  
  
 因為 Visual Basic 支援這個介面的成功很重要， `_NewEnum` 屬性所傳回的列舉值 **IEnumVARIANT** 必須支援介面。  這是 Visual Basic 了解的單一的列舉值介面。  
  
##  <a name="vcconcopy_classes"></a> 建立複製原則類別的 Typedefs  
 建立您到目前為止的 typedef 也提供您建立複製類別的進一步 typedef 也會由列舉值和集合所使用的所有資訊:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/CPP/implementing-an-stl-based-collection_3.h)]  
  
 在此範例中，您於 VCUE\_Copy.h 和 VCUE\_CopyString.h 可以使用在中定義的自訂 `GenericCopy` 類別從 [ATLCollections](../top/visual-cpp-samples.md) 範例。  您可以使用這個類別會以其他程式碼，不過，您可能需要定義 `GenericCopy` 的進一步特製化支援中集合的資料型別。  如需詳細資訊，請參閱 [ATL 複製原則類別](../atl/atl-copy-policy-classes.md)。  
  
##  <a name="vcconenumeration_and_collection"></a> 建立列舉型別和集合的 Typedefs  
 以 typedef 的形式，出現在所有必要樣板的參數特製化這種情況的 `CComEnumOnSTL` 和 `ICollectionOnSTLImpl` 類別提供。  為了簡化使用特製化，請另外再建立兩個 typedef 如下所示:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/CPP/implementing-an-stl-based-collection_4.h)]  
  
 現在 `CollectionType` 是實作先前定義的介面 `IWords``ICollectionOnSTLImpl` 的特製化上一個同義資料表並提供支援 **IEnumVARIANT**的列舉值。  
  
##  <a name="vcconedit_the_generated_code"></a> 編輯精靈產生的程式碼  
 現在您必須從 `CollectionType` typedef 表示的介面實作衍生自 `CWords` 而不是 `IWords`，如下所示:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/CPP/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> 加入程式碼以填入集合。  
 最後剩下的是填入資料的向量。  在這個簡單範例中，您可以將一些文字加入至建構函式的集合類別 \(Collection Class\):  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/CPP/implementing-an-stl-based-collection_6.h)]  
  
 現在，您可以測試以您所選擇的用戶端程式碼。  
  
## 請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections 範例](../top/visual-cpp-samples.md)   
 [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md)