---
title: 實現基於C++標準庫集合
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319445"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>實現基於C++標準庫集合

ATL`ICollectionOnSTLImpl`提供 該介面,使您能夠在物件上快速實現基於標準庫的C++集合介面。 要瞭解此類的工作原理,您將通過一個簡單的示例(下圖)來使用此類來實現針對自動化用戶端的唯讀集合。

範例代碼來自[ATLCollections 範例](../overview/visual-cpp-samples.md)。

要完成此過程,您將:

- [產生新的簡單物件](#vccongenerating_an_object)。

- 編輯產生的介面的[IDL 檔](#vcconedit_the_idl)。

- [創建五個類型def,](#vcconstorage_and_exposure_typedefs)描述集合項的儲存方式,以及如何透過 COM 介面向用戶端公開它們。

- [為複製策略類創建兩個類型def。](#vcconcopy_classes)

- [為枚舉器與集合建立類型定義](#vcconenumeration_and_collection)。

- [編輯精靈生成的C++代碼以使用集合類型def。](#vcconedit_the_generated_code)

- [新增代碼以填充集合](#vcconpopulate_the_collection)。

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>產生新的簡單物件

建立新項目,確保清除"應用程式設置下的屬性"框。 使用 ATL 添加類對話方塊和添加簡單物件精靈`Words`生成名為的簡單物件。 確保生成調用`IWords`的雙介面。 生成的類的物件將用於表示單詞集合(即字串)。

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>編輯 IDL 檔案

現在,打開 IDL 檔並添加`IWords`轉換為唯讀集合介面所需的三個屬性,如下所示:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

這是專為使用自動化用戶端設計的唯讀集合介面的標準表單。 此介面定義的編號註解對應於以下註解:

1. 集合介面通常是雙,因為自動化用戶端通過`_NewEnum``IDispatch::Invoke`訪問屬性。 但是,自動化用戶端可以通過 vtable 訪問剩餘的方法,因此雙介面比介面更可取。

1. 如果雙介面或 dispinterface 不會在執行時擴展(也就是說,您`IDispatch::Invoke`不會通過 )提供額外的方法或屬性,則應將**無鄰**屬性應用於定義。 此屬性使自動化用戶端能夠在編譯時執行完整的代碼驗證。 在這種情況下,不應擴展介面。

1. 如果希望自動化用戶端能夠使用此屬性,則正確的 DISPID 非常重要。 (請注意,DISPID_NEWENUM中只有一個下劃線。

1. 您可以提供任何值作為`Item`屬性的 DISPID。 但是,`Item`通常使用DISPID_VALUE使其成為集合的默認屬性。 這允許自動化用戶端引用該屬性而不顯式命名它。

1. 就 COM 用戶端而言`Item`,用於 屬性返回值的數據類型是存儲在集合中的項的類型。 介面返回字串,因此應使用標準 COM 字串類型 BSTR。 您可以在內部以不同格式儲存數據,稍後您將看到。

1. 用於`Count`屬性的DISPID的值是完全任意的。 此屬性沒有標準 DISPID。

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>為儲存與曝光建立類型定義

定義集合介面后,您需要決定如何存儲數據,以及如何通過枚舉器公開數據。

這些問題的解答可以以多個 typedef 的形式提供,您可以在新建立的類別標頭檔案頂部附近新增:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

在這種情況下,您將將數據存儲為**std::vector**的**std::string**s。 **std::vector**是一個C++標準庫容器類,它類似於託管陣列。 **std::字串**是C++標準庫的字串類。 這些類便於處理字串集合。

由於 Visual Basic 支援對於此介面的成功至關重要,因此`_NewEnum`屬性返回的 枚`IEnumVARIANT`舉器必須支援 該介面。 這是 Visual Basic 理解的唯一枚舉器介面。

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>為複製策略類別建立類型定義

到目前為止,您建立的 typedef 提供了為枚舉器和集合將使用的複製類建立進一步類型定義所需的所有資訊:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

在此示例中,可以使用 VCUE_Copy.h`GenericCopy`和 VCUE_CopyString.h 中從[ATLCollections](../overview/visual-cpp-samples.md)範例中定義的自訂類。 可以在其他代碼中使用此類,但可能需要定義`GenericCopy`進 一步的專門化以支援在您自己的集合中使用的數據類型。 有關詳細資訊,請參閱[ATL 複製策略類](../atl/atl-copy-policy-classes.md)。

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>為枚舉和收集建立類型定義

現在,以 typedefs`CComEnumOnSTL`的形式`ICollectionOnSTLImpl`提供了 專門化和 類所需的所有範本參數。 為了簡化專業化化的使用,請再創建兩個類型定義,如下所示:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

現在`CollectionType`是實現前面定義的`ICollectionOnSTLImpl``IWords`介面並提供`IEnumVARIANT`支援 的枚舉器的專門化的同義詞。

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>編輯精靈產生的代碼

現在,必須派生`CWords`自類型def`CollectionType`表示的 介面`IWords`實現,而不是如下所示:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>新增代碼以填充集合

剩下的唯一一件事是用數據填充向量。 在這個簡單範例中,您可以向類的建構函數中的集合添加幾個單詞:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

現在,您可以使用您選擇的用戶端測試代碼。

## <a name="see-also"></a>另請參閱

[集合和列舉程式](../atl/atl-collections-and-enumerators.md)<br/>
[ATL集合範例](../overview/visual-cpp-samples.md)<br/>
[ATL 複製原則類別](../atl/atl-copy-policy-classes.md)
