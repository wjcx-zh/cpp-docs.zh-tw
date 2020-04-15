---
title: CAnimationTimerEventHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: 72b6e5d8d9d4823795a1fb053c5f2374cb80fba4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320005"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler 類別

實作回呼，當發生計時事件時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫計時器事件處理程式::建立實體](#createinstance)|建立回檔實體`CAnimationTimerEventHandler`。|
|[動畫計時器事件處理程式::在發佈更新](#onpostupdate)|處理動畫更新完成後發生的事件。 (覆寫 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。)|
|[動畫計時器事件處理程式::打開預更新](#onpreupdate)|處理動畫更新開始之前發生的事件。 (覆寫 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。)|
|[動畫計時器事件處理程式::開啟渲染速度](#onrenderingtooslow)|處理動畫渲染幀速率低於最低理想幀速率時發生的事件。 (覆寫 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。)|
|[動畫計時器事件處理程式::設定動畫控制器](#setanimationcontroller)|存儲指向動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

此事件處理程式被建立並傳遞給 IUIAnimationTimer::當您調用 C動畫控制器::啟用動畫TimerEventHandler時,設置TimerEventHandler。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>動畫計時器事件處理程式::建立實體

創建 CAnimationTimer 事件處理程式回調的實體。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

*ppTimerEventHandler*

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>動畫計時器事件處理程式::在發佈更新

處理動畫更新完成後發生的事件。

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>動畫計時器事件處理程式::打開預更新

處理動畫更新開始之前發生的事件。

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>動畫計時器事件處理程式::開啟渲染速度

處理動畫渲染幀速率低於最低理想幀速率時發生的事件。

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>參數

*Fps*

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>動畫計時器事件處理程式::設定動畫控制器

存儲指向動畫控制器的指標以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
