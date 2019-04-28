---
title: ATL 集合和列舉值類別
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252321"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和列舉值類別

ATL 提供下列的類別，可協助您實作集合和列舉程式。

|類別|描述|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合介面實作|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|列舉值介面實作 (假設資料儲存在C++標準程式庫相容容器)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|列舉值介面實作 （假設儲存在陣列中的資料）|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|列舉值物件的實作 (使用`IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|列舉值物件的實作 (使用`CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|複製原則類別|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|複製原則類別|
|[CAdapt](../atl/reference/cadapt-class.md)|配接器類別 (隱藏**運算子 &** 允許`CComPtr`， `CComQIPtr`，並`CComBSTR`儲存在C++標準程式庫容器)|

## <a name="see-also"></a>另請參閱

[集合和列舉程式](../atl/atl-collections-and-enumerators.md)
