---
title: CD2DSizeU 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: f6b0bc12933100c6f2401f4f4cb9e1fae52dda65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396245"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 類別

D2D1_SIZE_U 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|多載。 建構`CD2DSizeU`物件從`D2D1_SIZE_U`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|傳回**布林**值，指出運算式是否包含任何有效的資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|將轉換`CD2DSizeU`至`CSize`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

建構 CD2DSizeU 物件從 CSize 物件。

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
  CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>參數

*size*<br/>
來源大小

*cx*<br/>
來源寬度

*cy*<br/>
來源高度

##  <a name="isnull"></a>  CD2DSizeU::IsNull

傳回布林值，指出運算式是否包含任何有效的資料 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果是空的; 的寬度和高度，則為 TRUE。否則為 FALSE。

##  <a name="operator_csize"></a>  CD2DSizeU::operator CSize

將 CD2DSizeU 轉換 CSize 物件。

```
operator CSize();
```

### <a name="return-value"></a>傳回值

目前的 D2D 大小值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
