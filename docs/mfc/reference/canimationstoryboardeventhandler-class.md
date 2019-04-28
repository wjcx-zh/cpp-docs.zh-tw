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
ms.openlocfilehash: d12f38491cf3aafca41756ce97e1cad44deb67d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338255"
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
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|建構 `CAnimationStoryboardEventHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|建立的執行個體`CAnimationStoryboardEventHandler`回呼。|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|會處理`OnStoryboardStatusChanged`分鏡腳本的狀態變更時，會發生的事件 (會覆寫`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`。)|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|會處理`OnStoryboardUpdated`分鏡腳本更新時，會發生的事件 (會覆寫`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`。)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|

## <a name="remarks"></a>備註

建立並傳遞至這個事件處理常式`IUIAnimationStoryboard::SetStoryboardEventHandler`方法中，當您呼叫`CAnimationController::EnableStoryboardEventHandler`。

## <a name="inheritance-hierarchy"></a>繼承階層

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="canimationstoryboardeventhandler"></a>  CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

建構 CAnimationStoryboardEventHandler 物件。

```
CAnimationStoryboardEventHandler();
```

##  <a name="createinstance"></a>  CAnimationStoryboardEventHandler::CreateInstance

建立 CAnimationStoryboardEventHandler 回呼的執行個體。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

*ppHandler*

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="onstoryboardstatuschanged"></a>  CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

處理 OnStoryboardStatusChanged 事件，分鏡腳本的狀態變更時，會發生

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*storyboard*<br/>
分鏡腳本的狀態已變更的指標。

*newStatus*<br/>
指定新分鏡腳本的狀態。

*previousStatus*<br/>
指定前一個分鏡腳本的狀態。

### <a name="return-value"></a>傳回值

如果方法成功，則為 S_OK否則 E_FAIL。

##  <a name="onstoryboardupdated"></a>  CAnimationStoryboardEventHandler::OnStoryboardUpdated

處理更新分鏡腳本時，就會發生的 OnStoryboardUpdated 事件

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>參數

*storyboard*<br/>
分鏡腳本，指標已更新。

### <a name="return-value"></a>傳回值

如果方法成功，則為 S_OK否則 E_FAIL。

##  <a name="setanimationcontroller"></a>  CAnimationStoryboardEventHandler::SetAnimationController

儲存路由事件的動畫控制器的指標。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
