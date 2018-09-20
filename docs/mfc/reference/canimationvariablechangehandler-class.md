---
title: CAnimationVariableChangeHandler 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23521a9ee9706787df0568547fe3419fe7e4fae5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424595"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 類別

實作回呼，當動畫變數的值變更時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|建構 `CAnimationVariableChangeHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|建立的執行個體`CAnimationVariableChangeHandler`物件。|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|當動畫變數的值已變更時呼叫。 (覆寫 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。)|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|

## <a name="remarks"></a>備註

建立並傳遞至這個事件處理常式`IUIAnimationVariable::SetVariableChangeHandler`方法中，當您呼叫`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（這可讓此封裝在動畫物件的所有動畫變數的事件）。

## <a name="inheritance-hierarchy"></a>繼承階層

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged

當動畫變數的值已變更時呼叫。

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>參數

*分鏡腳本*<br/>
分鏡腳本，以動畫顯示的變數。

*變數*<br/>
已更新動畫變數。

*newValue*<br/>
新值。

*previousValue*<br/>
先前的值。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController

儲存路由事件的動畫控制器的指標。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器，會收到的事件指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
