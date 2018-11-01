---
title: CAnimationVariableIntegerChangeHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: 66d740d7042ed2e19b6fe3a87345d7abb096f12c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449630"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler 類別

實作回呼，當動畫變數的值變更時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|建構 `CAnimationVariableIntegerChangeHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|建立的執行個體`CAnimationVariableIntegerChangeHandler`回呼。|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|當動畫變數的值已變更時呼叫。 (覆寫 `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`。)|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|

## <a name="remarks"></a>備註

這個事件處理常式會建立並傳遞給 IUIAnimationVariable::SetVariableIntegerChangeHandler 方法，當您呼叫 CAnimationVariable::EnableIntegerValueChangedEvent 或 CAnimationBaseObject::EnableIntegerValueChangedEvent （可啟用此事件的所有封裝在動畫物件的動畫變數）。

## <a name="inheritance-hierarchy"></a>繼承階層

[MFC 類別](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="canimationvariableintegerchangehandler"></a>  CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

建構 CAnimationVariableIntegerChangeHandler 物件。

```
CAnimationVariableIntegerChangeHandler ();
```

##  <a name="createinstance"></a>  CAnimationVariableIntegerChangeHandler::CreateInstance

建立 CAnimationVariableIntegerChangeHandler 回呼的執行個體。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

*ppHandler*

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="onintegervaluechanged"></a>  CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

當動畫變數的值已變更時呼叫。

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>參數

*分鏡腳本*<br/>
分鏡腳本，以動畫顯示的變數。

*變數*<br/>
已更新動畫變數。

*newValue*<br/>
新的捨入的值。

*previousValue*<br/>
先前的捨入的值。

### <a name="return-value"></a>傳回值

如果方法成功，則為 S_OK否則 E_FAIL。

##  <a name="setanimationcontroller"></a>  CAnimationVariableIntegerChangeHandler::SetAnimationController

儲存路由事件的動畫控制器的指標。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
