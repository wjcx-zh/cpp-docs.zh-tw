---
title: ATL 集合類別
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- collection classes
ms.assetid: eff95de6-78ef-4212-9d7d-1dacbdd4cc58
ms.openlocfilehash: fe795e54274e1d32dddb7310446bfa5aea22091a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492467"
---
# <a name="collection-classes"></a>集合類別

下列類別提供陣列、清單、對應和特性方法的支援, 以協助進行比較和元素存取。

- [CAtlArray](../atl/reference/catlarray-class.md)這個類別會實作為陣列物件。

- [CAtlList](../atl/reference/catllist-class.md)這個類別會提供建立和管理清單物件的方法。

- [CAtlMap](../atl/reference/catlmap-class.md)這個類別會提供建立和管理地圖物件的方法。

- [CAutoPtrArray](../atl/reference/cautoptrarray-class.md)這個類別會在建立智慧型指標的陣列時提供有用的方法。

- [CAutoPtrElementTraits](../atl/reference/cautoptrelementtraits-class.md)這個類別會提供方法、靜態函式和 typedef, 在建立智慧型指標的集合時很有用。

- [CAutoPtrList](../atl/reference/cautoptrlist-class.md)這個類別會在建立智慧型指標的清單時提供有用的方法。

- [CAutoVectorPtrElementTraits](../atl/reference/cautovectorptrelementtraits-class.md)當使用向量 new 和 delete 運算子建立智慧型指標的集合時, 這個類別會提供有用的方法、靜態函式和 typedef。

- [CComQIPtrElementTraits](../atl/reference/ccomqiptrelementtraits-class.md)這個類別會在建立 COM 介面指標的集合時, 提供有用的方法、靜態函式和 typedef。

- [CComSafeArray](../atl/reference/ccomsafearray-class.md)這個類別是[SAFEARRAY 資料類型](/windows/win32/api/oaidl/ns-oaidl-tagsafearray)結構的包裝函式。

- [CComSafeArrayBound](../atl/reference/ccomsafearraybound-class.md)這個類別是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-tagsafearraybound)結構的包裝函式。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)這個類別會儲存**IUnknown**指標, 而且是設計用來做為[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)樣板類別的參數。

- [CDefaultCharTraits](../atl/reference/cdefaultchartraits-class.md)這個類別提供兩個靜態函式, 用來轉換大寫和小寫之間的字元。

- [CDefaultCompareTraits](../atl/reference/cdefaultcomparetraits-class.md)這個類別會提供預設的元素比較函式。

- [CDefaultElementTraits](../atl/reference/cdefaultelementtraits-class.md)這個類別會提供集合類別的預設方法和函式。

- [CDefaultHashTraits](../atl/reference/cdefaulthashtraits-class.md)這個類別會提供用來計算雜湊值的靜態函式。

- [CElementTraits](../atl/reference/celementtraits-class.md)集合類別會使用這個類別來提供用於移動、複製、比較和雜湊作業的方法和函數。

- [CElementTraitsBase](../atl/reference/celementtraitsbase-class.md)這個類別會提供集合類別的預設複製和移動方法。

- [CHeapPtrElementTraits](../atl/reference/cheapptrelementtraits-class.md)在建立堆積指標的集合時, 這個類別提供有用的方法、靜態函數和 typedef。

- [CHeapPtrList](../atl/reference/cheapptrlist-class.md)這個類別會在建立堆積指標清單時提供有用的方法。

- [CInterfaceArray](../atl/reference/cinterfacearray-class.md)這個類別會在建立 COM 介面指標的陣列時提供有用的方法。

- [CInterfaceList](../atl/reference/cinterfacelist-class.md)這個類別會在建立 COM 介面指標的清單時, 提供有用的方法。

- [CPrimitiveElementTraits](../atl/reference/cprimitiveelementtraits-class.md)這個類別會針對由基本資料類型組成的集合類別, 提供預設的方法和函式。

- [CRBMap](../atl/reference/crbmap-class.md)此類別代表使用紅色-黑色二進位樹狀結構的對應結構。

- [CRBMultiMap](../atl/reference/crbmultimap-class.md)此類別代表一個對應結構, 允許每個索引鍵與一個以上的值建立關聯, 並使用紅色-黑色二進位樹狀目錄。

- [CRBTree](../atl/reference/crbtree-class.md)此類別提供建立和使用紅色-黑色樹狀結構的方法。

- [CSimpleArray](../atl/reference/csimplearray-class.md)這個類別提供管理簡單陣列的方法。

- [CSimpleArrayEqualHelper](../atl/reference/csimplearrayequalhelper-class.md)這個類別是[CSimpleArray](../atl/reference/csimplearray-class.md)類別的 helper。

- [CSimpleArrayEqualHelperFalse](../atl/reference/csimplearrayequalhelperfalse-class.md)這個類別是[CSimpleArray](../atl/reference/csimplearray-class.md)類別的 helper。

- [CSimpleMap](../atl/reference/csimplemap-class.md)這個類別會提供簡單對應陣列的支援。

- [CSimpleMapEqualHelper](../atl/reference/csimplemapequalhelper-class.md)這個類別是[CSimpleMap](../atl/reference/csimplemap-class.md)類別的 helper。

- [CSimpleMapEqualHelperFalse](../atl/reference/csimplemapequalhelperfalse-class.md)這個類別是[CSimpleMap](../atl/reference/csimplemap-class.md)類別的 helper。

- [CStringElementTraits](../atl/reference/cstringelementtraits-class.md)這個類別會提供用來儲存`CString`物件之集合類別所使用的靜態函式。

- [CStringElementTraitsI](../atl/reference/cstringelementtraitsi-class.md)這個類別會提供與集合類別物件中所儲存之字串相關的靜態函式。 它類似于[CStringElementTraits](../atl/reference/cstringelementtraits-class.md), 但會執行不區分大小寫的比較。

- [CStringRefElementTraits](../atl/reference/cstringrefelementtraits-class.md)這個類別會提供與集合類別物件中所儲存之字串相關的靜態函式。 字串物件會以參考的形式處理。

## <a name="related-articles"></a>相關文章

[ATL 集合類別](../atl/atl-collection-classes.md)

## <a name="see-also"></a>另請參閱

[類別總覽](../atl/atl-class-overview.md)<br/>
[集合類別](../atl/atl-collection-classes.md)
