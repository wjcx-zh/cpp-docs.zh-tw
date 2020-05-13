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
ms.openlocfilehash: 58bb37e9de40f4bc711b417eab107aa55b8ff0e8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750113"
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
|[動畫管理員事件處理常式:動畫管理員事件處理程式](#canimationmanagereventhandler)|建構 `CAnimationManagerEventHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 動畫管理員事件處理程式:建立實體](#createinstance)|創建`CAnimationManagerEventHandler`物件的實例。|
|[C動畫管理員操作器::在管理員狀態更改](#onmanagerstatuschanged)|當動畫管理器的狀態已更改時調用。 (覆寫 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。)|
|[C動畫管理員處理程式::設定動畫控制器](#setanimationcontroller)|存儲指向動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

此事件處理程式創建並傳遞給 IUIAnimationManager::setManagerEventHandler 方法,當您調用 C動畫控制器::啟用動畫管理器事件時。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>動畫管理員事件處理常式:動畫管理員事件處理程式

必須有 Visual Studio 2010 SP1。

建構 CAnimationManager 事件處理程式物件。

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>C 動畫管理員事件處理程式:建立實體

必須有 Visual Studio 2010 SP1。

創建 CAnimationManager 事件處理程式物件的實例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

*ppManagerEventHandler*<br/>
輸出。 如果該方法成功,它包含指向 COM 物件的指標,該指標將處理動畫管理器的狀態更新。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>C動畫管理員操作器::在管理員狀態更改

必須有 Visual Studio 2010 SP1。

當動畫管理器的狀態已更改時調用。

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*新狀態*<br/>
新狀態。

*前一個狀態*<br/>
上一個狀態。

### <a name="return-value"></a>傳回值

當前實現始終返回S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>C動畫管理員處理程式::設定動畫控制器

必須有 Visual Studio 2010 SP1。

存儲指向動畫控制器的指標以路由事件。

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
