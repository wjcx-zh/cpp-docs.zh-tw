---
title: CD2DSizeU 類別
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359298"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 類別

D2D1_SIZE_U的包裝。

## <a name="syntax"></a>語法

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU:CD2DSizeU](#cd2dsizeu)|已多載。 從`CD2DSizeU``D2D1_SIZE_U`物件構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU:: IsNull](#isnull)|傳回**一個布林值**,指示運算式是否不包含有效資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU::運算元 CSize](#operator_csize)|轉換為`CD2DSizeU``CSize`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU:CD2DSizeU

從 CSize 物件建構 CD2DSizeU 物件。

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>參數

*大小*<br/>
來源大小

*殘雪*<br/>
源寬度

*cy*<br/>
來源高度

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeU:: IsNull

返回一個布爾值,指示表達式是否不包含有效數據 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果寬度和高度為空,則為 TRUE;否則 FALSE。

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU::運算元 CSize

將 CD2DSizeU 轉換為 CSize 物件。

```
operator CSize();
```

### <a name="return-value"></a>傳回值

D2D 大小的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
