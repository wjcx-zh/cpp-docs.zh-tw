---
title: "CAnimationStoryboardEventHandler 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler
dev_langs:
- C++
helpviewer_keywords:
- CAnimationStoryboardEventHandler class
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 18
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bda8b0c941fd833bf821b563f4ca59cab9598cb8
ms.lasthandoff: 02/24/2017

---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler 類別
實作回呼，當腳本的狀態變更或更新腳本時由動畫 API 呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|建構 `CAnimationStoryboardEventHandler` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|建立的執行個體`CAnimationStoryboardEventHandler`回呼。|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|處理`OnStoryboardStatusChanged`腳本的狀態變更時，會發生的事件 (覆寫`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`。)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|處理`OnStoryboardUpdated`更新腳本時，會發生的事件 (覆寫`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`。)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|儲存路由事件的動畫控制器的指標。|  
  
## <a name="remarks"></a>備註  
 此事件處理常式會建立並傳遞至`IUIAnimationStoryboard::SetStoryboardEventHandler`方法中，當您呼叫`CAnimationController::EnableStoryboardEventHandler`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-namecanimationstoryboardeventhandlera--canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler  
 建構 CAnimationStoryboardEventHandler 物件。  
  
```  
CAnimationStoryboardEventHandler();
```  
  
##  <a name="a-namecreateinstancea--canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance  
 建立 CAnimationStoryboardEventHandler 回呼的執行個體。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationStoryboardEventHandler** ppHandler);
```  
  
### <a name="parameters"></a>參數  
 `pAnimationController`  
 動畫控制器，將會收到事件指標。  
  
 `ppHandler`  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="a-nameonstoryboardstatuschangeda--canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged  
 處理 OnStoryboardStatusChanged 事件，分鏡腳本的狀態變更時，會發生  
  
```  
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>參數  
 `storyboard`  
 分鏡腳本的狀態已變更指標。  
  
 `newStatus`  
 指定新腳本的狀態。  
  
 `previousStatus`  
 指定上一個分鏡腳本的狀態。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果方法成功。否則 E_FAIL。  
  
##  <a name="a-nameonstoryboardupdateda--canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated  
 處理更新腳本時，會發生的 OnStoryboardUpdated 事件  
  
```  
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```  
  
### <a name="parameters"></a>參數  
 `storyboard`  
 分鏡腳本，指標的已更新。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果方法成功。否則 E_FAIL。  
  
##  <a name="a-namesetanimationcontrollera--canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController  
 儲存路由事件的動畫控制器的指標。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>參數  
 `pAnimationController`  
 動畫控制器，將會收到事件指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

