---
title: CAnimationStoryboardEventHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364993"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler 類別

實作回呼，當腳本的狀態變更或更新腳本時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫故事板事件處理程式::動畫故事板事件處理程式](#canimationstoryboardeventhandler)|建構 `CAnimationStoryboardEventHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫故事板事件處理常式:建立實體](#createinstance)|建立回檔實體`CAnimationStoryboardEventHandler`。|
|[C動畫故事板事件處理程式::在故事板狀態更改](#onstoryboardstatuschanged)|處理`OnStoryboardStatusChanged`情節提要的狀態變更時發生的事件(`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`覆寫 . )|
|[C動畫故事板事件處理程式::在故事板上更新](#onstoryboardupdated)|處理`OnStoryboardUpdated`更新情節提要時發生的事件(`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`覆蓋 .)|
|[動畫故事板事件處理程式::設定動畫控制器](#setanimationcontroller)|存儲指向動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

當您呼叫`CAnimationController::EnableStoryboardEventHandler`時,將建立`IUIAnimationStoryboard::SetStoryboardEventHandler`此事件處理程式並傳遞給方法。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>動畫故事板事件處理程式::動畫故事板事件處理程式

建構 CAnimationStoryboard 事件處理程式物件。

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>動畫故事板事件處理常式:建立實體

創建 CAnimationStoryboard 事件處理程序回調的實例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

*普漢德勒*

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>C動畫故事板事件處理程式::在故事板狀態更改

處理故事板狀態更改事件,這些事件發生在情節提要的狀態更改時

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*文稿*<br/>
指向狀態已更改的情節提要的指標。

*新狀態*<br/>
指定新的情節提要狀態。

*前一個狀態*<br/>
指定以前的情節提要狀態。

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>C動畫故事板事件處理程式::在故事板上更新

處理更新情節提要時發生的更新事件

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>參數

*文稿*<br/>
指向故事板的指標,已更新。

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>動畫故事板事件處理程式::設定動畫控制器

存儲指向動畫控制器的指標以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
