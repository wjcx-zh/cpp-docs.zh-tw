---
title: 實作與 c + + 標準程式庫為基礎的集合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5163e05004d6376ab37023c71ae668ec9f367c10
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852558"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>實作與 c + + 標準程式庫為基礎的集合
ATL 提供`ICollectionOnSTLImpl`介面，可讓您快速實作您的物件上的 c + + 標準程式庫為基礎的集合介面。 若要了解這個類別的運作方式，您也可以簡單範例 （如下所示），使用這個類別來實作唯讀集合，旨在自動化用戶端。  
  
 範例程式碼取自[ATLCollections 範例](../visual-cpp-samples.md)。  
  
 若要完成此程序，您將會：  
  
-   [產生新的簡單物件](#vccongenerating_an_object)。  
  
-   [編輯 IDL 檔案](#vcconedit_the_idl)產生的介面。  
  
-   [建立五個 typedef](#vcconstorage_and_exposure_typedefs)描述如何儲存集合項目，以及如何公開給用戶端透過 COM 介面。  
  
-   [建立兩個 typedef 複製原則類別](#vcconcopy_classes)。  
  
-   [建立列舉值和集合實作的 typedef](#vcconenumeration_and_collection)。  
  
-   [編輯精靈產生 c + + 程式碼以使用集合 typedef](#vcconedit_the_generated_code)。  
  
-   [新增要填入集合的程式碼](#vcconpopulate_the_collection)。  
  
##  <a name="vccongenerating_an_object"></a> 產生新的簡單物件  
 建立新的專案，並確保應用程式設定 下的 屬性 方塊已清除。 使用 ATL 加入類別 對話方塊中，並新增簡單物件精靈 來產生簡單的物件呼叫`Words`。 請確定雙重介面呼叫`IWords`產生。 產生類別的物件將用來代表文字 （也就是字串） 的集合中。  
  
##  <a name="vcconedit_the_idl"></a> 編輯 IDL 檔案  
 現在，開啟 IDL 檔案，並加入三個屬性，則不必開啟`IWords`至唯讀集合的介面，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 這是標準格式以供設計時記住的 Automation 用戶端的唯讀集合介面。 編號的註解，此介面定義中對應至下列的註解：  
  
1.  因為自動化用戶端存取，集合介面是通常雙重`_NewEnum`屬性，透過`IDispatch::Invoke`。 不過，自動化用戶端可以存取透過 vtable，其餘的方法，因此最好分配介面是使用雙重介面。  
  
2.  如果雙重介面或 dispinterface 將不會擴充在執行階段 (也就是您將不會提供額外的方法或屬性，透過`IDispatch::Invoke`)，您應該套用**nonextensible**屬性設定為您的定義。 這個屬性可讓自動化用戶端執行完整的程式碼在編譯時期的驗證。 在此情況下，不應該擴充介面。  
  
3.  正確的 DISPID 是很重要，如果您想要能夠使用這個屬性的 Automation 用戶端。 （請注意在 DISPID_NEWENUM 是只有一個底線）。  
  
4.  您可以提供任何值的 DISPID 作為`Item`屬性。 不過，`Item`通常會使用 DISPID_VALUE 讓集合的預設屬性。 這可讓自動化用戶端，而不需要明確地將它命名為參考屬性。  
  
5.  使用傳回值的資料類型`Item`屬性是儲存在集合中，只要 COM 用戶端所關注的項目類型。 此介面會傳回字串，因此您應該使用標準 COM 字串的型別，BSTR。 您可以將資料儲存在不同的格式在內部短時間內，您會看到。  
  
6.  做為的 DISPID 值`Count`是完全任意的屬性。 沒有任何標準的 DISPID，這個屬性。  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> 建立儲存體和暴露的 Typedef  
 集合介面定義之後，您需要決定如何將儲存資料，以及如何將資料公開透過列舉值。  
  
 數字的 typedef，您可以新增標頭檔的頂端附近，為您新建立的類別可以提供這些問題的答案：  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 在此情況下，您會將資料儲存為**std:: vector**的**std:: string**s。 **std:: vector**是行為類似 managed 陣列的 c + + 標準程式庫容器類別。 **std:: string**是 c + + 標準程式庫的字串類別。 這些類別，讓您輕鬆地使用字串的集合。  
  
 由於 Visual Basic 支援這個介面是否成功很重要時，所傳回的列舉值`_NewEnum`屬性必須支援`IEnumVARIANT`介面。 這是 Visual Basic 所了解的唯一列舉值介面。  
  
##  <a name="vcconcopy_classes"></a> 複製原則類別建立 Typedef  
 您到目前為止已建立的 typedef 會提供您需要進一步建立將使用的列舉值和集合的複本類別的 typedef 的所有資訊：  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 在此範例中，您可以使用自訂`GenericCopy`VCUE_Copy.h 和從 VCUE_CopyString.h 中定義的類別[ATLCollections](../visual-cpp-samples.md)範例。 您可以使用這個類別中其他程式碼，但您可能需要進一步定義的特製化`GenericCopy`以支援您自己的集合中所使用的資料類型。 如需詳細資訊，請參閱 < [ATL 複製原則類別](../atl/atl-copy-policy-classes.md)。  
  
##  <a name="vcconenumeration_and_collection"></a> 列舉型別與集合建立 Typedef  
 現在所有範本所需的參數來特製化`CComEnumOnSTL`和`ICollectionOnSTLImpl`typedef 的形式提供這種情況下的類別。 若要簡化的特製化使用，建立兩個更多的 typedef，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 現在`CollectionType`的特製化同義`ICollectionOnSTLImpl`可實`IWords`介面稍早定義，並提供列舉支援的`IEnumVARIANT`。  
  
##  <a name="vcconedit_the_generated_code"></a> 編輯精靈所產生的程式碼  
 現在您必須衍生`CWords`所代表的介面實作`CollectionType`typedef 而不是`IWords`，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> 新增要填入集合的程式碼  
 唯一剩餘的事項是填入資料的向量。 在此簡單範例中，您就可以在類別建構函式集合中新增幾個字：  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 現在，您可以使用您選擇的用戶端來測試程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections 範例](../visual-cpp-samples.md)   
 [ATL 複製原則類別](../atl/atl-copy-policy-classes.md)

