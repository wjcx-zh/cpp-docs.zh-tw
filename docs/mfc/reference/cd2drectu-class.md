---
title: CD2DRectU 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369102"
---
# <a name="cd2drectu-class"></a>CD2DRectU 類別

`D2D1_RECT_U`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|已多載。 從`CD2DRectU``D2D1_RECT_U`物件構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DRectU:: IsNull](#isnull)|傳回**一個布林值**,指示運算式是否不包含有效資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DRectU::操作員CRect](#operator_crect)|轉換為`CD2DRectU``CRect`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU

從 CRect 物件建構 CD2DRectU 物件。

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>參數

*矩形*<br/>
來源矩形

*u 左*<br/>
源左座標

*uTop*<br/>
來源頂端座標

*uRight*<br/>
源右座標

*u巴斯特*<br/>
來源底部座標

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU:: IsNull

返回一個布爾值,指示表達式是否不包含有效數據 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果矩形的頂部、左側、底部和右側值都等於 0,則為 TRUE;否則 FALSE。

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::操作員CRect

將 CD2DRectU 轉換為 CRect 物件。

```
operator CRect();
```

### <a name="return-value"></a>傳回值

D2D 矩形的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
