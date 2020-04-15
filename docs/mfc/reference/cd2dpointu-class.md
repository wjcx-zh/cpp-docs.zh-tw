---
title: CD2DPointU 類別
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 8c6db55f1dde1fd054a1f75590f5969c097b2f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369148"
---
# <a name="cd2dpointu-class"></a>CD2DPointU 類別

`D2D1_POINT_2U`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DPointU:CD2DPointU](#cd2dpointu)|已多載。 從物件`D2D1_POINT_2U``CD2DPointU`物件 建構 。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DPointU::運算符 CPoint](#operator_cpoint)|轉換為`CD2DPointU``CPoint`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dpointucd2dpointu"></a><a name="cd2dpointu"></a>CD2DPointU:CD2DPointU

從 CPoint 物件構造 CD2DPointU 物件。

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>參數

*pt*<br/>
源點

*Ux*<br/>
來源 X

*uY*<br/>
源 Y

## <a name="cd2dpointuoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointU::運算符 CPoint

將 CD2DPointU 轉換為 CPoint 物件。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

D2D 點的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
