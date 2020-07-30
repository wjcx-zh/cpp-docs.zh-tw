---
title: CComObjectRoot 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 98868e67fd14899a75f86837034ba540d22039e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224236"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 類別

此[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的 typedef 是在伺服器的預設執行緒模型上範本化。

## <a name="syntax"></a>語法

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>備註

`CComObjectRoot`是 **`typedef`** 伺服器預設執行緒模型上的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)範本化。 因此， [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)會參考[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。

`CComObjectRootEx`處理非匯總和匯總物件的物件參考計數管理。 如果您的物件未進行匯總，它會保存物件參考計數，如果您的物件正在進行匯總，則會保存外部未知的指標。 對於匯總的物件， `CComObjectRootEx` 方法可以用來處理內建物件所要建立的失敗，以及在釋放內部介面或刪除內建物件時，保護外部物件的刪除。

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
