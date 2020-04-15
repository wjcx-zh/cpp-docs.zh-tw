---
title: CD2DSizeF 類別
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369071"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 類別

D2D1_SIZE_F的包裝。

## <a name="syntax"></a>語法

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF:CD2DSizeF](#cd2dsizef)|已多載。 從`CD2DSizeF``D2D1_SIZE_F`物件構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|傳回**一個布林值**,指示運算式是否不包含有效資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF::運算元 CSize](#operator_csize)|轉換為`CD2DSizeF``CSize`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF:CD2DSizeF

從 CSize 物件建構 CD2DSizeF 物件。

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>參數

*大小*<br/>
來源大小

*殘雪*<br/>
源寬度

*cy*<br/>
來源高度

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::IsNull

返回一個布爾值,指示表達式是否不包含有效數據 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果寬度和高度為空,則為 TRUE;否則 FALSE。

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::運算元 CSize

將 CD2DSizeF 轉換為 CSize 物件。

```
operator CSize();
```

### <a name="return-value"></a>傳回值

D2D 大小的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
