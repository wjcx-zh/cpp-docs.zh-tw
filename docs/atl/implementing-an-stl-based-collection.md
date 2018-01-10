---
title: "實作與 c + + 標準程式庫為基礎的集合 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5b80b55361a8f7bfa195b08d02feb94af0874bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-c-standard-library-based-collection"></a>實作與 c + + 標準程式庫為基礎的集合
ATL 提供`ICollectionOnSTLImpl`介面，讓您快速實作您的物件上的 c + + 標準程式庫為基礎的集合介面。 若要了解這個類別的運作方式，您會一起完成的簡單範例 （如下），使用這個類別來實作旨在 Automation 用戶端的唯讀集合。  
  
 範例程式碼取自[ATLCollections 範例](../visual-cpp-samples.md)。  
  
 若要完成此程序，您將能夠：  
  
-   [產生新的簡單物件](#vccongenerating_an_object)。  
  
-   [編輯 IDL 檔案](#vcconedit_the_idl)產生介面。  
  
-   [建立五個 typedef](#vcconstorage_and_exposure_typedefs)描述如何儲存集合的項目，以及如何公開給用戶端透過 COM 介面。  
  
-   [建立複本的兩個 typedef 原則類別](#vcconcopy_classes)。  
  
-   [建立列舉值和集合實作 typedef](#vcconenumeration_and_collection)。  
  
-   [編輯精靈產生 c + + 程式碼以使用集合 typedef](#vcconedit_the_generated_code)。  
  
-   [加入程式碼以在集合中填入](#vcconpopulate_the_collection)。  
  
##  <a name="vccongenerating_an_object"></a>產生新的簡單物件  
 建立新的專案，並確保應用程式設定屬性方塊已清除。 使用 ATL 加入類別 對話方塊，並新增簡單物件精靈 來產生簡單的物件呼叫`Words`。 請確定雙重介面呼叫`IWords`產生。 物件產生的類別將用來代表文字 （也就是字串） 的集合。  
  
##  <a name="vcconedit_the_idl"></a>編輯 IDL 檔案  
 現在，開啟 IDL 檔案，並加入三個屬性，則不必開啟`IWords`至唯讀集合的介面，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 這是標準格式以供使用 Automation 用戶端，請注意這項設計的唯讀集合介面。 這個介面定義中編號的註解對應至下列註解：  
  
1.  集合介面是雙重通常因為 Automation 用戶端會存取`_NewEnum`屬性透過**idispatch:: Invoke**。 不過，Automation 用戶端可以存取透過 vtable，其餘的方法，因此雙重介面會更好的分配介面。  
  
2.  如果雙重介面或 dispinterface，用以將不會延伸在執行階段 (也就是您將不會提供額外的方法或屬性，透過**idispatch:: Invoke**)，您應該套用**nonextensible**屬性您的定義。 此屬性可讓 Automation 用戶端可以執行編譯時期的完整程式碼驗證。 在此情況下，不應該擴充介面。  
  
3.  正確的 DISPID 是很重要，如果您想要能夠使用這個屬性的 Automation 用戶端。 (請注意，是在只有一個底線**DISPID_NEWENUM**。)  
  
4.  您可以提供任何值作為的 DISPID**項目**屬性。 不過，**項目**通常會使用**DISPID_VALUE**以容易集合的預設屬性。 這可讓 Automation 用戶端，但不命名它明確參考的屬性。  
  
5.  使用傳回值的資料類型**項目**屬性是儲存在集合中，就相當重要的 COM 用戶端項目的類型。 此介面會傳回字串，因此您應該改用標準的 COM 字串類型`BSTR`。 您可以將資料儲存在不同的格式在內部不久，您會看到。  
  
6.  所使用的 DISPID 值**計數**是完全任意的屬性。 此屬性沒有標準 DISPID。  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a>儲存體與曝光建立 Typedef  
 集合介面定義之後，您需要決定如何將儲存資料，以及如何將資料公開透過列舉值。  
  
 數字的 typedef，您可以加入最上方的標頭檔，為您新建立的類別可以提供這些問題的答案：  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 在此情況下，您會將資料儲存為**std:: vector**的**std:: string**s。 **std:: vector**是行為如同 managed 陣列的 c + + 標準程式庫容器類別。 **std:: string**是 c + + 標準程式庫的字串類別。 這些類別讓您更容易使用的字串集合。  
  
 由於 Visual Basic 支援這個介面的成功很重要時，所傳回的列舉值`_NewEnum`屬性必須支援**IEnumVARIANT**介面。 這是 Visual Basic 所了解的唯一列舉程式介面。  
  
##  <a name="vcconcopy_classes"></a>為複製原則類別建立 Typedef  
 目前已建立 typedef 提供您需要進一步建立複製的類別將列舉值和集合所使用之 typedef 的所有資訊：  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 在此範例中，您可以使用自訂`GenericCopy`VCUE_Copy.h 和從 VCUE_CopyString.h 中定義的類別[ATLCollections](../visual-cpp-samples.md)範例。 您可以使用這個類別中的其他程式碼，但您可能需要進一步的特製化定義`GenericCopy`以支援您自己的集合中所使用的資料類型。 如需詳細資訊，請參閱[ATL 複製原則類別](../atl/atl-copy-policy-classes.md)。  
  
##  <a name="vcconenumeration_and_collection"></a>列舉型別和集合建立 Typedef  
 現在所有的範本參數特製化所需`CComEnumOnSTL`和`ICollectionOnSTLImpl`typedef 的表單已提供這種情況下的類別。 若要簡化使用特製化，建立兩個的多個 typedef 如下所示：  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 現在`CollectionType`同義的特製化`ICollectionOnSTLImpl`實作`IWords`先前定義介面，並提供支援的列舉值**IEnumVARIANT**。  
  
##  <a name="vcconedit_the_generated_code"></a>編輯精靈產生的程式碼  
 現在您必須衍生`CWords`所代表的介面實作`CollectionType`typedef 而不是`IWords`，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a>加入程式碼以填入集合  
 唯一會保持為填入之資料的向量。 在這個簡單的範例中，您可以加入幾個字至集合中之類別的建構函式：  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 現在，您可以使用您選擇的用戶端來測試程式碼。  
  
## <a name="see-also"></a>請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections 範例](../visual-cpp-samples.md)   
 [ATL 複製原則類別](../atl/atl-copy-policy-classes.md)

