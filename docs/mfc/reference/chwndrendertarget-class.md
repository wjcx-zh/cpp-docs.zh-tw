---
title: CHwndRenderTarget 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbbc8a6aa76cb5ebd6efe8f7bba231ad342067f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434984"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 類別

ID2D1HwndRenderTarget 包裝函式。

## <a name="syntax"></a>語法

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|建構 CHwndRenderTarget 物件從 HWND。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|將現有的轉譯目標物件的介面|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|指出是否要阻擋此呈現目標相關聯的 HWND。|
|[CHwndRenderTarget::Create](#create)|建立與視窗相關聯的呈現目標|
|[CHwndRenderTarget::Detach](#detach)|中斷連結物件的轉譯目標介面|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|傳回與此相關的 HWND 呈現目標。|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|傳回 ID2D1HwndRenderTarget 介面。|
|[CHwndRenderTarget::ReCreate](#recreate)|重新建立與視窗相關聯的呈現目標|
|[CHwndRenderTarget::Resize](#resize)|呈現目標的大小變更為指定的像素大小|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|傳回 ID2D1HwndRenderTarget 介面。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|ID2D1HwndRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

將現有的轉譯目標物件的介面

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*pTarget*<br/>
現有的轉譯目標介面。 不能是 NULL

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

指出是否要阻擋此呈現目標相關聯的 HWND。

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>傳回值

值，指出是否要與此相關的 HWND 轉譯目標會阻擋。

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

建構 CHwndRenderTarget 物件從 HWND。

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>參數

*hwnd*<br/>
與此相關的 HWND 呈現目標

##  <a name="create"></a>  CHwndRenderTarget::Create

建立與視窗相關聯的呈現目標

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
與此相關的 HWND 呈現目標

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

中斷連結物件的轉譯目標介面

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

卸離的指標轉譯目標的介面。

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

傳回與此相關的 HWND 呈現目標。

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>傳回值

與此相關的 HWND 呈現目標。

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

傳回 ID2D1HwndRenderTarget 介面。

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1HwndRenderTarget 介面的指標。

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

ID2D1HwndRenderTarget 物件的指標。

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *

傳回 ID2D1HwndRenderTarget 介面。

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1HwndRenderTarget 介面的指標。

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

重新建立與視窗相關聯的呈現目標

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
與此相關的 HWND 呈現目標

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="resize"></a>  CHwndRenderTarget::Resize

呈現目標的大小變更為指定的像素大小

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>參數

*size*<br/>
裝置的像素的呈現目標的新的大小

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
