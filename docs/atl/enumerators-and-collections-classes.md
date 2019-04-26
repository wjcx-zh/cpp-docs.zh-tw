---
title: 列舉值和集合類別 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerators, ATL classes
ms.assetid: fcd093b2-98bf-444d-94ab-9a55520a5051
ms.openlocfilehash: 6de81a7b0ddd77471669b19c4be1145c776d2902
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198118"
---
# <a name="enumerators-and-collections-classes"></a>列舉值和集合類別

下列類別會提供 COM 集合和列舉型別的支援：

- [CComEnum](../atl/reference/ccomenum-class.md)定義 COM 列舉值物件的陣列為基礎。

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)提供要列舉的項目儲存在陣列中的 COM 列舉值介面的實作。

- [CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)定義 COM 列舉值物件，根據C++標準程式庫集合。

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)提供要列舉的項目會儲存在 COM 列舉程式介面的實作C++標準程式庫相容的容器。

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)提供的實作`Count`， `Item`，和`_NewEnum`集合介面的屬性。

## <a name="related-articles"></a>相關文章

[ATL 集合和列舉程式](../atl/atl-collections-and-enumerators.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)
