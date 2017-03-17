---
title: "CAnimationVariableChangeHandler 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler class
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 46c4eb9210b69c527375b12100ab7cc22fef0176
ms.lasthandoff: 02/24/2017

---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 類別
實作回呼，當動畫變數的值變更時由動畫 API 呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|建構 `CAnimationVariableChangeHandler` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|建立的執行個體`CAnimationVariableChangeHandler`物件。|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|當動畫變數的值已變更時呼叫。 (覆寫 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。)|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|  
  
## <a name="remarks"></a>備註  
 此事件處理常式會建立並傳遞至`IUIAnimationVariable::SetVariableChangeHandler`方法中，當您呼叫`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（這可讓封裝在動畫物件的所有動畫變數的這個事件）。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged  
 當動畫變數的值已變更時呼叫。  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>參數  
 `storyboard`  
 腳本動畫變數。  
  
 `variable`  
 已更新動畫變數。  
  
 `newValue`  
 新值。  
  
 `previousValue`  
 先前的值。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController  
 儲存路由事件的動畫控制器的指標。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>參數  
 `pAnimationController`  
 動畫控制器，將會收到事件指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

