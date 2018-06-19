---
title: CAnimationVariableChangeHandler 類別 |Microsoft 文件
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
ms.openlocfilehash: 2e35fc33b26fa6bead73458a46d7c4edee1cf136
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350988"
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
 這個事件處理常式為建立並傳遞給`IUIAnimationVariable::SetVariableChangeHandler`方法，當您呼叫`CAnimationVariable::EnableValueChangedEvent`或`CAnimationBaseObject::EnableValueChangedEvent`（可讓封裝在動畫物件中的所有動畫變數的這個事件）。  
  
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
 `storyboard`  
 建立動畫變數分鏡腳本。  
  
 `variable`  
 已更新動畫變數。  
  
 `newValue`  
 新值。  
  
 `previousValue`  
 先前的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 儲存路由事件的動畫控制器的指標。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>參數  
 `pAnimationController`  
 動畫控制器，將會收到事件指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
