---
title: 列舉值和集合類別 (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.enum
helpviewer_keywords:
- enumerators, ATL classes
ms.assetid: fcd093b2-98bf-444d-94ab-9a55520a5051
ms.openlocfilehash: 28c741ec40b6d350dd5c5b1e777bd05ec083ad47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538019"
---
# <a name="enumerators-and-collections-classes"></a>列舉值和集合類別

下列類別會提供 COM 集合和列舉型別的支援：

- [CComEnum](../atl/reference/ccomenum-class.md)定義 COM 列舉值物件的陣列為基礎。

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)提供要列舉的項目儲存在陣列中的 COM 列舉值介面的實作。

- [CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)定義 COM 列舉值物件根據 c + + 標準程式庫集合。

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)提供 c + + 標準程式庫相容的容器中儲存所列舉之項目的 COM 列舉程式介面的實作。

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)提供的實作`Count`， `Item`，和`_NewEnum`集合介面的屬性。

## <a name="related-articles"></a>相關文章

[ATL 集合和列舉程式](../atl/atl-collections-and-enumerators.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)

