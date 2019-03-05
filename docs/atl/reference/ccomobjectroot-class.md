---
title: CComObjectRoot 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 9a9ffa1813fb15297d209894050b6bcce6802df2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298642"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 類別

此 typedef [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)樣板化預設的執行緒模型的伺服器上。

## <a name="syntax"></a>語法

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>備註

`CComObjectRoot` 已`typedef`的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)樣板化預設的執行緒模型的伺服器上。 因此[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)參考任何[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或是[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。

`CComObjectRootEx` 處理非彙總與彙總物件的物件參考計數管理。 如果您的物件不正在彙總，而且存放的外部未知的指標，如果您的物件正在彙總，它就會保留物件參考計數。 對於彙總的物件，`CComObjectRootEx`方法可以用來處理失敗，內部物件的建構，並刪除保護以防止刪除內部介面發行時則外部物件或內部的物件。

## <a name="requirements"></a>需求

**標頭：** atlcom.h

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
