---
title: CHwndRenderTarget 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: d1669d89183cd971e1afe0f05a1bad040f6b07df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752697"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 類別

ID2D1HwndRender目標包裝器。

## <a name="syntax"></a>語法

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHwndRender目標::CHwndRender目標](#chwndrendertarget)|從 HWND 構造 CHwndRenderTarget 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHwndRender目標::附加](#attach)|將現有渲染目標介面附加到物件|
|[CHwndRender目標::檢查視窗狀態](#checkwindowstate)|指示是否已佔用與此渲染目標關聯的 HWND。|
|[CHwndRender目標::創建](#create)|建立與視窗關聯的渲染目標|
|[CHwndRenderTarget::D埃塔奇](#detach)|從物件分離成成目標介面|
|[CHwndRender目標::GetHwnd](#gethwnd)|返回與此渲染目標關聯的 HWND。|
|[CHwndRender目標::獲取HwndRender目標](#gethwndrendertarget)|返回 ID2D1HwndRenderTarget 介面。|
|[CHwndRender目標::重新創建](#recreate)|重新建立與視窗關聯的渲染目標|
|[CHwndRender目標::調整大小](#resize)|將成成目標的大小變更為指定的圖元大小|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CHwndRender目標::操作員 ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|返回 ID2D1HwndRenderTarget 介面。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|指向 ID2D1HwndRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CRender 目標](../../mfc/reference/crendertarget-class.md)

[CHwndRender目標](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRender目標::附加

將現有渲染目標介面附加到物件

```cpp
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*p 目標*<br/>
現有渲染目標介面。 無法為 NULL

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRender目標::檢查視窗狀態

指示是否已佔用與此渲染目標關聯的 HWND。

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>傳回值

指示是否鎖定與此渲染目標關聯的 HWND 的值。

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRender目標::CHwndRender目標

從 HWND 構造 CHwndRenderTarget 物件。

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>參數

*霍恩德*<br/>
與此渲染目標關聯的 HWND

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRender目標::創建

建立與視窗關聯的渲染目標

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
與此渲染目標關聯的 HWND

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::D埃塔奇

從物件分離成成目標介面

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的渲染目標介面的指標。

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRender目標::GetHwnd

返回與此渲染目標關聯的 HWND。

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>傳回值

與此渲染目標關聯的HWND。

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRender目標::獲取HwndRender目標

返回 ID2D1HwndRenderTarget 介面。

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1HwndRenderTarget 介面或 NULL 的指標。

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

指向 ID2D1HwndRenderTarget 物件的指標。

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRender目標::操作員 ID2D1HwndRenderTarget*

返回 ID2D1HwndRenderTarget 介面。

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1HwndRenderTarget 介面或 NULL 的指標。

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRender目標::重新創建

重新建立與視窗關聯的渲染目標

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
與此渲染目標關聯的 HWND

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRender目標::調整大小

將成成目標的大小變更為指定的圖元大小

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>參數

*size*<br/>
以裝置像素為單位的渲染目標的新大小

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
