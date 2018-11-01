---
title: CAnimationManagerEventHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: 497b6e0f5bdeb817eccb0bb42f66763a97da2af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445730"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler 類別

實作回呼，當動畫管理員的狀態變更時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|建構 `CAnimationManagerEventHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|建立的執行個體`CAnimationManagerEventHandler`物件。|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|當動畫管理員的狀態已變更時呼叫。 (覆寫 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|

## <a name="remarks"></a>備註

這個事件處理常式會建立並傳遞給 IUIAnimationManager::SetManagerEventHandler 方法，當您呼叫 CAnimationController::EnableAnimationManagerEvent。

## <a name="inheritance-hierarchy"></a>繼承階層

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler

必須有 Visual Studio 2010 SP1。

建構 CAnimationManagerEventHandler 物件。

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance

必須有 Visual Studio 2010 SP1。

建立 CAnimationManagerEventHandler 物件的執行個體。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

*ppManagerEventHandler*<br/>
輸出。 如果方法成功，它會包含處理狀態更新為動畫管理員的 COM 物件的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged

必須有 Visual Studio 2010 SP1。

當動畫管理員的狀態已變更時呼叫。

```
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*newStatus*<br/>
新的狀態。

*previousStatus*<br/>
先前的狀態。

### <a name="return-value"></a>傳回值

目前的實作一定會傳回 S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

必須有 Visual Studio 2010 SP1。

儲存路由事件的動畫控制器的指標。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
