---
title: IUnknown 實作類別 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42c42b43fdc04978fabe36b0ea64f39b9a5d333f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098481"
---
# <a name="iunknown-implementation-classes"></a>IUnknown 實作類別

下列類別會實作`IUnknown`及相關方法：

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理參考計數的彙總及非彙總的物件。 可讓您指定執行緒模型。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)管理參考計數的彙總及非彙總的物件。 使用預設的執行緒模型的伺服器。

- [CComAggObject](../atl/reference/ccomaggobject-class.md)實作`IUnknown`彙總的物件。

- [CComObject](../atl/reference/ccomobject-class.md)實作`IUnknown`非彙總的物件。

- [CComPolyObject](../atl/reference/ccompolyobject-class.md)實作`IUnknown`彙總與非彙總物件。 使用`CComPolyObject`就不需要同時`CComAggObject`和`CComObject`在模組中。 單一`CComPolyObject`物件會處理彙總及非彙總的情況。

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md)實作`IUnknown`非彙總的物件，而不需修改模組鎖定計數。

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md)實作`IUnknown`撕下介面。

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md)實作`IUnknown`「 快取 」 的分割介面。

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md)實作`IUnknown`內部彙總或分割介面的物件。

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md)管理將不會刪除該模組，以確保您的物件的參考計數。

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md)會建立暫存的 COM 物件，使用架構實作`IUnknown`。

## <a name="related-articles"></a>相關文章

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)<br/>
[彙總和 Class Factory 巨集](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[COM 對應巨集](../atl/reference/com-map-macros.md)<br/>
[COM 對應全域函式](../atl/reference/com-map-global-functions.md)

