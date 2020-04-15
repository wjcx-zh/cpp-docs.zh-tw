---
title: CD2DRectF 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369114"
---
# <a name="cd2drectf-class"></a>CD2DRectF 類別

`D2D1_RECT_F`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DrectF:CD2DrectF](#cd2drectf)|已多載。 從`CD2DRectF``D2D1_RECT_F`物件構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DrectF::IsNull](#isnull)|傳回**一個布林值**,指示運算式是否不包含有效資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DRectF::運算子 CRect](#operator_crect)|轉換為`CD2DRectF``CRect`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DrectF:CD2DrectF

從 CRect 物件建構 CD2DRectF 物件。

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>參數

*矩形*<br/>
來源矩形

*f左*<br/>
源左座標

*fTop*<br/>
來源頂端座標

*恐懼*<br/>
源右座標

*fBottom*<br/>
來源底部座標

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DrectF::IsNull

返回一個布爾值,指示表達式是否不包含有效數據 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果矩形的頂部、左側、底部和右側值都等於 0,則為 TRUE;否則 FALSE。

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::運算子 CRect

將 CD2DRectF 轉換為 CRect 物件。

```
operator CRect();
```

### <a name="return-value"></a>傳回值

D2D 矩形的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
