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
ms.openlocfilehash: dec940d2f5e68f0531fc917df447b5a1a5cb8189
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755052"
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
|[動畫變數素轉換處理程式::c動畫變數在轉換處理程式](#canimationvariableintegerchangehandler)|建構 `CAnimationVariableIntegerChangeHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫可轉換處理程式:建立實體](#createinstance)|建立回檔實體`CAnimationVariableIntegerChangeHandler`。|
|[動畫可轉換到變數轉換處理程式::oninteger值已變更](#onintegervaluechanged)|當動畫變數的值已更改時調用。 (覆寫 `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`。)|
|[動畫可轉換處理程式::設定動畫控制器](#setanimationcontroller)|存儲指向動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

此事件處理程式被建立並傳遞給 IUIAnimationvariable::設定可變IntegerChangeHandler方法,當您調用 CAnimationvariable::啟用 IntegerValueChangeevent 或 CAnimationBaseObject:啟用 IntegerValueChangeEvent(它啟用此事件,用於封裝在動畫物件中的所有動畫變數)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[MFC 類別](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>動畫變數素轉換處理程式::c動畫變數在轉換處理程式

建構一個 CAnimation 可變IntegerChangeHandler物件。

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>動畫可轉換處理程式:建立實體

創建 CAnimation 可變Integer ChangeHandler回檔的實例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

*普漢德勒*

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>動畫可轉換到變數轉換處理程式::oninteger值已變更

當動畫變數的值已更改時調用。

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>參數

*文稿*<br/>
為變數設置動畫的情節提要。

*變數*<br/>
已更新的動畫變數。

*newValue*<br/>
新的舍入值。

*前一個值*<br/>
上一個舍入的值。

### <a name="return-value"></a>傳回值

如果方法成功,S_OK;否則E_FAIL。

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>動畫可轉換處理程式::設定動畫控制器

存儲指向動畫控制器的指標以路由事件。

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
