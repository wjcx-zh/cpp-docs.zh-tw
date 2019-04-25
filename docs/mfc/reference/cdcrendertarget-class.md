---
title: CDCRenderTarget 類別
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 70169d2b89d9ea657898f7a96dea27556023d4e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168169"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 類別

ID2D1DCRenderTarget 包裝函式。

## <a name="syntax"></a>語法

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|建構 CDCRenderTarget 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|將現有的轉譯目標物件的介面|
|[CDCRenderTarget::BindDC](#binddc)|繫結至它問題繪製命令的裝置內容的呈現目標|
|[CDCRenderTarget::Create](#create)|建立 CDCRenderTarget。|
|[CDCRenderTarget::Detach](#detach)|中斷連結物件的轉譯目標介面|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|傳回 ID2D1DCRenderTarget 介面|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|傳回 ID2D1DCRenderTarget 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|ID2D1DCRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

將現有的轉譯目標物件的介面

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*pTarget*<br/>
現有的轉譯目標介面。 不能是 NULL

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

繫結至它問題繪製命令的裝置內容的呈現目標

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*dc*<br/>
呈現目標問題繪製命令的裝置內容

*rect*<br/>
維度的轉譯目標繫結至裝置內容 (HDC) 的控制代碼

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

建構 CDCRenderTarget 物件。

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

建立 CDCRenderTarget。

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>參數

*props*<br/>
轉譯模式、 像素格式，遠端選項、 DPI 的詳細資訊，以及硬體呈現所需的最小的 DirectX 支援。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="detach"></a>  CDCRenderTarget::Detach

中斷連結物件的轉譯目標介面

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

卸離的指標轉譯目標的介面。

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

傳回 ID2D1DCRenderTarget 介面

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1DCRenderTarget 介面的指標。

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

ID2D1DCRenderTarget 物件的指標。

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget*

傳回 ID2D1DCRenderTarget 介面

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1DCRenderTarget 介面的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
