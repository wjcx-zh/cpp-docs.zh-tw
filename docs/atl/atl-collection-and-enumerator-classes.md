---
title: ATL 集合和列舉值類別
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265401"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和列舉值類別

ATL 提供下列的類別，可協助您實作集合和列舉程式。

|類別|描述|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合介面實作|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|列舉值介面實作 （假設 c + + 標準程式庫相容的容器中儲存的資料）|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|列舉值介面實作 （假設儲存在陣列中的資料）|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|列舉值物件的實作 (使用`IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|列舉值物件的實作 (使用`CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|複製原則類別|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|複製原則類別|
|[CAdapt](../atl/reference/cadapt-class.md)|配接器類別 (隱藏**運算子 &** 允許`CComPtr`， `CComQIPtr`，和`CComBSTR`儲存在 c + + 標準程式庫容器)|

## <a name="see-also"></a>另請參閱

[集合和列舉程式](../atl/atl-collections-and-enumerators.md)
