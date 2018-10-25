---
title: CD2DSizeF 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5af0ea66ba143935689486d7b7afa3cfaf8cd033
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071267"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 類別

D2D1_SIZE_F 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|多載。 建構`CD2DSizeF`物件從`D2D1_SIZE_F`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|傳回**布林**值，指出運算式是否包含任何有效的資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|將轉換`CD2DSizeF`至`CSize`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

建構 CD2DSizeF 物件從 CSize 物件。

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
  CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>參數

*size*<br/>
來源大小

*cx*<br/>
來源寬度

*cy*<br/>
來源高度

##  <a name="isnull"></a>  CD2DSizeF::IsNull

傳回布林值，指出運算式是否包含任何有效的資料 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果是空的; 的寬度和高度，則為 TRUE。否則為 FALSE。

##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize

將 CD2DSizeF 轉換 CSize 物件。

```
operator CSize();
```

### <a name="return-value"></a>傳回值

目前的 D2D 大小值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
