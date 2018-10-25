---
title: CAnimationController 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
dev_langs:
- C++
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9f17eea48e01d12df103382483b352e5dce46b7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080555"
---
# <a name="canimationcontroller-class"></a>CAnimationController 類別

實作動畫控制器，提供用來建立和管理動畫的中央介面。

## <a name="syntax"></a>語法

```
class CAnimationController : public CObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|建構動畫控制器。|
|[CAnimationController:: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|解構函式。 當動畫控制器物件正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|將動畫物件加入至動畫控制器所屬的群組。|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|加入到群組的主要畫面格。|
|[CAnimationController::AnimateGroup](#animategroup)|準備要執行動畫的群組，並選擇性地將其排程。|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|多載。 由架構呼叫以已排程動畫時，清除群組。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|多載。 建立隨轉換而改變的主要畫面格，將它加入指定的群組。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|設定或釋放動畫管理員的狀態變更時要呼叫的處理常式。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|設定或釋放計時事件的處理常式和計時更新處理常式。|
|[Canimationcontroller:: Enableprioritycomparisonhandler](#enableprioritycomparisonhandler)|設定或釋放給呼叫以判斷是否已排程的分鏡腳本可以取消、 結束、 修剪或壓縮的優先順序比較處理常式。|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|設定或釋放分鏡腳本的狀態和更新事件的處理常式。|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|多載。 尋找分鏡腳本動畫群組。|
|[CAnimationController::FindAnimationObject](#findanimationobject)|找出包含指定的動畫變數的動畫物件。|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|傳回識別啟動分鏡腳本的主要畫面格。|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供封裝 IUIAnimationManager 物件的存取權。|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供封裝 IUIAnimationTimer 物件的存取權。|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|IUIAnimationTransitionFactory 介面或如果無法建立轉換程式庫的 NULL 指標。|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供封裝 IUIAnimationTransitionLibrary 物件的存取權。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|會告知是否至少一個群組已播放的動畫。|
|[CAnimationController::IsValid](#isvalid)|會告訴動畫控制器是否有效。|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|當動畫變數的整數值變更時由架構呼叫。|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由架構呼叫以回應從動畫管理員 StatusChanged 事件。|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|在動畫更新完成之後，由架構呼叫。|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|動畫更新開始之前，由架構呼叫。|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|當動畫轉譯畫面播放速率低於最小的理想畫面播放速率時由架構呼叫。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|當動畫變數的值變更時由架構呼叫。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|由架構呼叫正確之前已排程的動畫。|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|分鏡腳本的狀態變更時由架構呼叫。|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|已更新的分鏡腳本時由架構呼叫。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|動畫控制器中移除所有動畫群組。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|動畫控制器中移除具有指定識別碼的動畫群組。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|移除動畫控制器中的動畫物件。|
|[CAnimationController::RemoveTransitions](#removetransitions)|動畫物件屬於指定的群組中移除轉換。|
|[CAnimationController::ScheduleGroup](#schedulegroup)|排程的動畫。|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|建立動畫控制器和一個視窗之間的關聯性。|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|動畫管理員，來更新所有動畫變數的值，會指示。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|多載。 Helper 會清除群組。|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|針對指定的群組動畫只排程時，由架構呼叫。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|表示啟動分鏡腳本的主要畫面格。|
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定動畫控制站是否為有效。 如果目前的作業系統不支援 Windows 動畫 API，這個成員設定為 FALSE。|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|屬於此動畫控制器動畫群組清單。|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|儲存動畫管理員 COM 物件的指標。|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|儲存動畫計時器 COM 物件的指標。|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|動畫管理員的狀態已變更，或張貼更新事件發生時重新自動繪製相關 CWnd 物件的指標。 可以是 NULL。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|儲存轉換 Factory COM 物件的指標。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|儲存轉換程式庫的 COM 物件的指標。|

## <a name="remarks"></a>備註

CAnimationController 類別是管理動畫的索引鍵類別。 您可能會在應用程式中建立的動畫控制器的一或多個執行個體，選擇性地連接到使用 CAnimationController::SetRelatedWnd CWnd 物件的 動畫控制器的執行個體。 此連線才能 WM_PAINT 訊息自動傳送給相關的視窗動畫管理員的狀態已變更或已更新動畫計時器時。 如果您未啟用此關聯性，您必須重繪以手動方式顯示動畫的視窗。 針對此目的 CAnimationController 從衍生類別並覆寫 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate 即可失效時所需的一或多個 windows。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>  CAnimationController:: ~ CAnimationController

解構函式。 當動畫控制器物件正在被終結時呼叫。

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject

將動畫物件加入至動畫控制器所屬的群組。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>參數

*pObject*<br/>
動畫物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則其中新增 pObject 的現有或新的動畫群組指標如果 pObject 已新增至群組屬於另一個動畫控制器，則為 NULL。

### <a name="remarks"></a>備註

呼叫這個方法，以動畫物件新增至動畫控制器。 物件會新增至群組，以根據物件的 GroupID （請參閱 CAnimationBaseObject::SetID）。 動畫控制器將會建立新的群組，它是否與指定 GroupID 所加入的第一個物件。 只有一張動畫控制器，可以加入動畫物件。 如果您需要將物件加入至另一個控制器，請先呼叫 RemoveAnimationObject。 如果您呼叫具有新的 GroupID SetID 早已加入到群組的物件時，物件會從舊的群組中移除並加入另一個群組，並提供指定的識別碼。

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

加入到群組的主要畫面格。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

*pKeyframe*<br/>
主要畫面格指標。

### <a name="return-value"></a>傳回值

如果函式成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

通常您不需要呼叫這個方法，請改用 CAnimationController::CreateKeyframe，這會建立，並會建立主要畫面格自動新增至群組。

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

準備要執行動畫的群組，並選擇性地將其排程。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*bScheduleNow*<br/>
指定是否要執行立即的動畫。

### <a name="return-value"></a>傳回值

如果已成功排程而執行動畫，則為 TRUE。

### <a name="remarks"></a>備註

這個方法會實際建立分鏡腳本、 新增動畫變數、 套用轉換及設定主要畫面格。 可以延遲排程，如果您將 bScheduleNow 設為 FALSE。 在此情況下指定的群組會保留已設定動畫的分鏡腳本。 此時，您可以設定在分鏡腳本和動畫變數的事件。 當您實際上需要執行的動畫呼叫 CAnimationController::ScheduleGroup。

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

建構動畫控制器。

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

由架構呼叫以已排程動畫時，清除群組。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*pGroup*<br/>
若要清除的動畫群組指標。

### <a name="remarks"></a>備註

這個方法會移除所有的轉換和主要畫面格從指定的群組，因為它們也不適用於已排程的動畫之後。

##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe

建立隨轉換而改變的主要畫面格，將它加入指定的群組。

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定主要畫面格建立對象的群組識別碼。

*pTransition*<br/>
轉換指標。 這項轉換之後，主要畫面格就會插入分鏡腳本中。

*pKeyframe*<br/>
這個主要畫面格的基底主要畫面格指標。

*offset*<br/>
pKeyframe 指定的基底主要畫面格位移，以秒為單位。

### <a name="return-value"></a>傳回值

函式成功後，新建立的主要畫面格指標。

### <a name="remarks"></a>備註

您可以儲存傳回的指標，讓其他的主要畫面格以新建立的主要畫面格為基礎 (請參閱第二個多載)。 即可開始主要畫面格的轉換，請參閱 CBaseTransition::SetKeyframes。 您不需要刪除以這種方式建立的主要畫面格，因為動畫群組會自動刪除它們。 根據其他主要畫面格和轉換建立主要畫面格時要小心，避免循環參照。

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

設定或釋放動畫管理員的狀態變更時要呼叫的處理常式。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否要設定或釋放處理常式。

### <a name="return-value"></a>傳回值

如果處理常式已順利設定或發行，則為 TRUE。

### <a name="remarks"></a>備註

當處理常式的設定 （啟用） Windows 動畫動畫管理員的狀態變更時，就會呼叫 OnAnimationManagerStatusChanged。

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

設定或釋放計時事件的處理常式和計時更新處理常式。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否要設定或釋放處理常式。

*idleBehavior*<br/>
指定閒置計時器更新處理常式的行為。

### <a name="return-value"></a>傳回值

如果處理常式已順利設定或釋放;，則為 TRUE。如果此值為 FALSE 的方法針對第二次呼叫未釋放的處理常式的第一次，或任何其他錯誤。

### <a name="remarks"></a>備註

當處理常式設定 （啟用） Windows 動畫 API 呼叫 OnAnimationTimerPreUpdate，OnAnimationTimerPostUpdate，OnRenderingTooSlow 方法。 您必須啟用動畫計時器，以允許 Windows 動畫 API 更新分鏡腳本。 否則，您必須呼叫 CAnimationController::UpdateAnimationManager，若要引導動畫管理員來更新所有動畫變數的值。

##  <a name="enableprioritycomparisonhandler"></a>  Canimationcontroller:: Enableprioritycomparisonhandler

設定或釋放給呼叫以判斷是否已排程的分鏡腳本可以取消、 結束、 修剪或壓縮的優先順序比較處理常式。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>參數

*dwHandlerType*<br/>
UI_ANIMATION_PHT_ 的組合加上旗標 （請參閱 < 備註 >），以指定哪些設定或釋放的處理常式。

### <a name="return-value"></a>傳回值

如果處理常式已順利設定或發行，則為 TRUE。

### <a name="remarks"></a>備註

當處理常式的設定 （啟用） Windows 動畫會呼叫下列虛擬方法，根據 dwHandlerType: OnHasPriorityCancel、 OnHasPriorityConclude、 OnHasPriorityTrim、 OnHasPriorityCompress。 dwHandler 可以是下列旗標的組合： UI_ANIMATION_PHT_NONE-發行所有的處理常式 UI_ANIMATION_PHT_CANCEL-設定取消設定 Conclude 比較處理常式 UI_ANIMATION_PHT_COMPRESS 比較處理常式 UI_ANIMATION_PHT_CONCLUDE--設定Compress 比較處理常式 UI_ANIMATION_PHT_TRIM-設定修剪比較處理常式 UI_ANIMATION_PHT_CANCEL_REMOVE-移除取消比較處理常式 UI_ANIMATION_PHT_CONCLUDE_REMOVE-移除 Conclude 比較處理常式 UI_ANIMATION_PHT_COMPRESS_移除-移除壓縮比較處理常式 UI_ANIMATION_PHT_TRIM_REMOVE-移除修剪比較處理常式

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

設定或釋放分鏡腳本的狀態和更新事件的處理常式。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

*bEnable*<br/>
指定是否要設定或釋放處理常式。

### <a name="return-value"></a>傳回值

如果已成功設定或釋放; 處理常式，則為 TRUE。如果現在找到指定的動畫群組或尚未初始化為指定群組的動畫，而且其內部的分鏡腳本是 NULL，則為 FALSE。

### <a name="remarks"></a>備註

當處理常式的設定 （啟用） 的 Windows 動畫 API 呼叫 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虛擬方法。 處理常式之後，必須設定 CAnimationController::Animate 已呼叫指定的動畫群組，因為它會建立封裝的 IUIAnimationStoryboard 物件。

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

尋找針對動畫群組其群組的識別碼。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*pStoryboard*<br/>
分鏡腳本指標。

### <a name="return-value"></a>傳回值

動畫群組或如果找不到具有指定識別碼群組為 NULL 指標。

### <a name="remarks"></a>備註

使用這個方法在執行階段尋找動畫群組。 建立群組，並加入至動畫群組的內部清單，當特定 GroupID 的第一個動畫物件新增至動畫控制器。

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

找出包含指定的動畫變數的動畫物件。

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>參數

*pVariable*<br/>
動畫變數的指標。

*ppObject*<br/>
輸出。 包含與動畫的物件或 NULL 指標。

*ppGroup*<br/>
輸出。 包含動畫的群組，包含動畫的物件，則為 NULL 指標。

### <a name="return-value"></a>傳回值

如果找不到物件，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

呼叫的事件處理常式時，您需要尋找從內送的動畫變數的動畫物件。

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

表示啟動分鏡腳本的主要畫面格。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

傳回識別啟動分鏡腳本的主要畫面格。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>傳回值

基底主要畫面格，用來識別啟動分鏡腳本的指標。

### <a name="remarks"></a>備註

取得這個主要畫面格為基礎的分鏡腳本啟動時執行的時間中的任何其他主要畫面格或轉換。

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

提供封裝 IUIAnimationManager 物件的存取權。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>傳回值

IUIAnimationManager 介面或 NULL，如果動畫管理員建立失敗的指標。

### <a name="remarks"></a>備註

如果目前的作業系統不支援 Windows 動畫 API，這個方法會傳回 NULL，並在那之後 CAnimationController::IsValid 上的所有後續呼叫會傳回 FALSE。 您可能需要存取 IUIAnimationManager 才能夠呼叫它不會包裝由動畫控制器的介面方法。

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

提供封裝 IUIAnimationTimer 物件的存取權。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>傳回值

IUIAnimationTimer 介面或 NULL，如果建立動畫計時器的失敗的指標。

### <a name="remarks"></a>備註

如果目前的作業系統不支援 Windows 動畫 API，這個方法會傳回 NULL，並在那之後 CAnimationController::IsValid 上的所有後續呼叫會傳回 FALSE。

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

IUIAnimationTransitionFactory 介面或如果無法建立轉換程式庫的 NULL 指標。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>傳回值

IUIAnimationTransitionFactory 或 NULL，如果轉換處理站建立失敗的指標。

### <a name="remarks"></a>備註

如果目前的作業系統不支援 Windows 動畫 API，這個方法會傳回 NULL，並在那之後 CAnimationController::IsValid 上的所有後續呼叫會傳回 FALSE。

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

提供封裝 IUIAnimationTransitionLibrary 物件的存取權。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>傳回值

IUIAnimationTransitionLibrary 介面或如果無法建立轉換程式庫的 NULL 指標。

### <a name="remarks"></a>備註

如果目前的作業系統不支援 Windows 動畫 API，這個方法會傳回 NULL，並在那之後 CAnimationController::IsValid 上的所有後續呼叫會傳回 FALSE。

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

會告知是否至少一個群組已播放的動畫。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>傳回值

如果沒有進行此動畫控制站; 中的動畫，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

檢查動畫管理員的狀態並傳回 TRUE，如果狀態是 UI_ANIMATION_MANAGER_BUSY。

##  <a name="isvalid"></a>  CAnimationController::IsValid

會告訴動畫控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果動畫控制器有效，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳回 FALSE，只有當 Windows 動畫 API 不支援目前的 OS 和動畫管理員建立失敗，因為其未註冊。 您需要呼叫 GetUIAnimationManager 初始化 COM 程式庫，讓此旗標的設定之後，至少一次。

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

指定動畫控制站是否為有效。 如果目前的作業系統不支援 Windows 動畫 API，這個成員設定為 FALSE。

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

屬於此動畫控制器動畫群組清單。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

儲存動畫管理員 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

儲存動畫計時器 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

動畫管理員的狀態已變更，或張貼更新事件發生時重新自動繪製相關 CWnd 物件的指標。 可以是 NULL。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

儲存轉換 Factory COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

儲存轉換程式庫的 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

針對指定的群組動畫只排程時，由架構呼叫。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
已排程的動畫 」 群組指標。

### <a name="remarks"></a>備註

預設實作會移除指定的群組中的主要畫面格，並從屬於指定的群組動畫變數轉換。 可以是任何額外的動作，動畫排程時，才在衍生類別中覆寫。

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

當動畫變數的整數值變更時由架構呼叫。

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
已變更其值會保留動畫物件的動畫群組的指標。

*pObject*<br/>
包含已變更其值的動畫變數的動畫物件的指標。

*變數*<br/>
動畫變數的指標。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定先前的值。

### <a name="remarks"></a>備註

如果您讓使用 EnableIntegerValueChangedEvent 呼叫特定的動畫變數或動畫物件的動畫變數的事件，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

由架構呼叫以回應從動畫管理員 StatusChanged 事件。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*newStatus*<br/>
新動畫管理員的狀態。

*previousStatus*<br/>
上一個動畫管理員的狀態。

### <a name="remarks"></a>備註

如果您啟用 EnableAnimationManagerEvent 動畫管理員事件，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如果它已設定 SetRelatedWnd 的預設實作會更新相關的視窗。

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

在動畫更新完成之後，由架構呼叫。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>備註

如果您啟用使用 EnableAnimationTimerEventHandler 的計時器事件處理常式，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

動畫更新開始之前，由架構呼叫。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>備註

如果您啟用使用 EnableAnimationTimerEventHandler 的計時器事件處理常式，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

當動畫轉譯畫面播放速率低於最小的理想畫面播放速率時由架構呼叫。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>參數

*fps*<br/>
每秒畫面格數中目前的畫面播放速率。

### <a name="remarks"></a>備註

如果您啟用使用 EnableAnimationTimerEventHandler 的計時器事件處理常式，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 藉由呼叫 IUIAnimationTimer::SetFrameRateThreshold 指定最小的理想畫面播放速率。

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

當動畫變數的值變更時由架構呼叫。

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
已變更其值會保留動畫物件的動畫群組的指標。

*pObject*<br/>
包含已變更其值的動畫變數的動畫物件的指標。

*變數*<br/>
動畫變數的指標。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定先前的值。

### <a name="remarks"></a>備註

如果您讓使用 EnableValueChangedEvent 呼叫特定的動畫變數或動畫物件的動畫變數的事件，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

由架構呼叫正確之前已排程的動畫。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
即將開始其動畫的動畫群組指標。

### <a name="remarks"></a>備註

這個呼叫會路由傳送至相關的 CWnd，並可以在動畫啟動指定的群組之前，執行任何額外的動作的衍生類別中覆寫。

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*pGroupScheduled*<br/>
擁有目前排程的分鏡腳本的群組。

*pGroupNew*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CANCEL 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 閱讀 Windows 動畫 API 文件，如需詳細資訊[衝突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*pGroupScheduled*<br/>
擁有目前排程的分鏡腳本的群組。

*pGroupNew*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_COMPRESS 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 閱讀 Windows 動畫 API 文件，如需詳細資訊[衝突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*pGroupScheduled*<br/>
擁有目前排程的分鏡腳本的群組。

*pGroupNew*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CONCLUDE 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 閱讀 Windows 動畫 API 文件，如需詳細資訊[衝突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*pGroupScheduled*<br/>
擁有目前排程的分鏡腳本的群組。

*pGroupNew*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_TRIM 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 閱讀 Windows 動畫 API 文件，如需詳細資訊[衝突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

分鏡腳本的狀態變更時由架構呼叫。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
已變更其狀態擁有的分鏡腳本動畫群組的指標。

*newStatus*<br/>
指定新的狀態。

*previousStatus*<br/>
指定先前的狀態。

### <a name="remarks"></a>備註

如果您啟用使用 CAnimationController::EnableStoryboardEventHandler 的分鏡腳本事件，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

已更新的分鏡腳本時由架構呼叫。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
擁有的分鏡腳本的群組指標。

### <a name="remarks"></a>備註

如果您啟用使用 CAnimationController::EnableStoryboardEventHandler 的分鏡腳本事件，會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

動畫控制器中移除所有動畫群組。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>備註

所有群組都會刪除，他們的指標，如果儲存在應用程式層級必須都會失效。 如果正在刪除群組 CAnimationGroup::m_bAutodestroyAnimationObjects 為 TRUE 時，將會刪除隸屬於該群組的所有動畫物件;否則其父代動畫控制器的參考將設為 NULL，而且可以加入另一個控制站。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

動畫控制器中移除具有指定識別碼的動畫群組。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定動畫群組識別碼。

### <a name="remarks"></a>備註

這個方法的動畫群組移除群組的內部清單，並將它刪除，因此如果您儲存的指標，該動畫群組時，它必須失效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects 為 TRUE 時，將會刪除隸屬於該群組的所有動畫物件;否則其父代動畫控制器的參考將設為 NULL，而且可以加入另一個控制站。

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

移除動畫控制器中的動畫物件。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>參數

*pObject*<br/>
動畫物件的指標。

*bNoDelete*<br/>
如果此參數為 TRUE 時移除將不被刪除的物件。

### <a name="remarks"></a>備註

移除動畫控制器和動畫群組動畫物件。 如果特定物件應該不會顯示動畫，或如果您需要將物件移至另一個動畫控制器，請呼叫此函式。 在最後一個案例 bNoDelete 必須是 TRUE。

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

動畫物件屬於指定的群組中移除轉換。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

### <a name="remarks"></a>備註

群組及其動畫物件執行迴圈，並針對每個動畫物件呼叫 ClearTransitions(FALSE)。 動畫已排定之後，這個方法是由架構呼叫。

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

排程的動畫。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定動畫來排定的群組識別碼。

*time*<br/>
指定排程的時間。

### <a name="return-value"></a>傳回值

如果已成功排程動畫，則為 TRUE。 如果尚未建立分鏡腳本，或發生其他錯誤，則為 FALSE。

### <a name="remarks"></a>備註

您必須設定為 FALSE 的先前 ScheduleGroup 參數 bScheduleNow 呼叫 AnimateGroup。 您可以指定所需的動畫時間取自 IUIAnimationTimer::GetTime。 如果時間參數是 0.0 時，為目前排定的動畫。

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

建立動畫控制器和一個視窗之間的關聯性。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
若要設定的視窗物件的指標。

### <a name="remarks"></a>備註

如果設定相關的 CWnd 物件，則動畫控制器可以自動進行更新 （傳送 WM_PAINT 訊息） 的動畫管理員狀態已變更或計時器後更新事件發生時。

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

動畫管理員，來更新所有動畫變數的值，會指示。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>備註

呼叫這個方法會將前移動畫管理員，為目前時間，視變更的分鏡腳本的狀態和更新任何動畫變數適當插補值。 在內部這個方法會呼叫 IUIAnimationTimer::GetTime(timeNow) IUIAnimationManager::Update(timeNow)。 若要自訂此行為在衍生類別中的，這個方法會覆寫。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
