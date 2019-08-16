---
title: CAnimationController 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507643"
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
|[CAnimationController::CAnimationController](#canimationcontroller)|構造動畫控制器。|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|解構函式。 在終結動畫控制器物件時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|將動畫物件加入至屬於動畫控制器的群組。|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|將主要畫面格新增至群組。|
|[CAnimationController::AnimateGroup](#animategroup)|準備群組以執行動畫並選擇性地進行排程。|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|多載。 由架構呼叫, 以在已排程動畫時清除群組。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|多載。 建立隨轉換而改變的主要畫面格，將它加入指定的群組。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|設定或釋放在動畫管理員的狀態變更時所要呼叫的處理常式。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|設定或釋放計時事件的處理常式, 以及計時更新的處理常式。|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|設定或釋放要呼叫的優先順序比較處理常式, 以判斷是否可以取消、結束、修剪或壓縮已排程的分鏡腳本。|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|設定或發行分鏡腳本狀態和更新事件的處理常式。|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|多載。 依其分鏡腳本尋找動畫群組。|
|[CAnimationController::FindAnimationObject](#findanimationobject)|尋找包含指定之動畫變數的動畫物件。|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|傳回可識別分鏡腳本起點的主要畫面格。|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供對封裝的 IUIAnimationManager 物件的存取。|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供對封裝的 IUIAnimationTimer 物件的存取。|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|IUIAnimationTransitionFactory 介面的指標, 如果建立轉換程式庫失敗, 則為 Null。|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供對封裝的 IUIAnimationTransitionLibrary 物件的存取。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|告知是否至少有一個群組現正播放動畫。|
|[CAnimationController::IsValid](#isvalid)|告訴動畫控制器是否有效。|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|當動畫變數的整數值已變更時由架構呼叫。|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由架構呼叫, 以回應動畫管理員的 StatusChanged 事件。|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|在動畫更新完成之後由架構呼叫。|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|在動畫更新開始之前, 由架構呼叫。|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|當動畫的轉譯畫面播放速率低於最小的預期畫面播放速率時, 由架構呼叫。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|當動畫變數的值變更時由架構呼叫。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|在排程動畫之前由架構呼叫。|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由架構呼叫來解決排程衝突。|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|當分鏡腳本狀態變更時由架構呼叫。|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|當腳本已更新時由架構呼叫。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|從動畫控制器移除所有的動畫群組。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|從動畫控制器移除具有指定之識別碼的動畫群組。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|從動畫控制器移除動畫物件。|
|[CAnimationController::RemoveTransitions](#removetransitions)|從屬於指定群組的動畫物件中移除轉換。|
|[CAnimationController::ScheduleGroup](#schedulegroup)|排定動畫。|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|建立動畫控制器和視窗之間的關聯性。|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|指示動畫管理員更新所有動畫變數的值。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|多載。 清除群組的協助程式。|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|當指定群組的動畫剛排程時, 由架構呼叫。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|說明|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|表示分鏡腳本開頭的主要畫面格。|
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定動畫控制器是否有效。 如果目前的作業系統不支援 Windows 動畫 API, 此成員會設定為 FALSE。|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|屬於此動畫控制器的動畫群組清單。|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|儲存動畫管理員 COM 物件的指標。|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|儲存動畫計時器 COM 物件的指標。|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|相關 CWnd 物件的指標, 可在動畫管理員的狀態變更時自動重新繪製, 或發生 post update 事件。 可以是 Null。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|儲存轉換 Factory COM 物件的指標。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|儲存轉換程式庫 COM 物件的指標。|

## <a name="remarks"></a>備註

CAnimationController 類別是管理動畫的索引鍵類別。 您可以在應用程式中建立動畫控制器的一個或多個實例, 並選擇性地使用 CAnimationController:: SetRelatedWnd 將動畫控制器的實例連接到 CWnd 物件。 當動畫管理員狀態已變更或動畫計時器已更新時, 需要此連接才能自動將 WM_PAINT 訊息傳送到相關視窗。 如果您未啟用此關聯性, 則必須重繪以手動方式顯示動畫的視窗。 基於此目的, 您可以從 CAnimationController 衍生類別, 並覆寫 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate, 並在必要時讓一或多個視窗失效。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

解構函式。 在終結動畫控制器物件時呼叫。

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>CAnimationController:: AddAnimationObject

將動畫物件加入至屬於動畫控制器的群組。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>參數

*pObject*<br/>
動畫物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功, 則為已加入 pObject 的現有或新的動畫群組的指標;如果 pObject 已經加入至屬於另一個動畫控制器的群組, 則為 Null。

### <a name="remarks"></a>備註

呼叫這個方法, 將動畫物件新增至動畫控制器。 系統會根據物件的 GroupID, 將物件新增至群組 (請參閱 CAnimationBaseObject:: SetID)。 如果它是以指定的 GroupID 新增的第一個物件, 則動畫控制器會建立新的群組。 動畫物件只能加入至一個動畫控制器。 如果您需要將物件新增至另一個控制器, 請先呼叫 RemoveAnimationObject。 如果您針對已新增至群組的物件, 使用新的 GroupID 呼叫 SetID, 則會從舊的群組移除該物件, 並將其新增至具有指定識別碼的另一個群組。

##  <a name="addkeyframetogroup"></a>CAnimationController:: AddKeyframeToGroup

將主要畫面格新增至群組。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

*pKeyframe*<br/>
主要畫面格的指標。

### <a name="return-value"></a>傳回值

如果函式成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您通常不需要呼叫此方法, 請改用 CAnimationController:: CreateKeyframe, 這會自動建立並將建立的主要畫面格新增至群組。

##  <a name="animategroup"></a>CAnimationController:: AnimateGroup

準備群組以執行動畫並選擇性地進行排程。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*bScheduleNow*<br/>
指定是否要立即執行動畫。

### <a name="return-value"></a>傳回值

如果已成功排程和執行動畫, 則為 TRUE。

### <a name="remarks"></a>備註

這個方法會執行實際工作, 以建立分鏡腳本、新增動畫變數、套用轉換和設定主要畫面格。 如果您將 bScheduleNow 設定為 FALSE, 可能會延遲排程。 在此情況下, 指定的群組將會保存已設定動畫的分鏡腳本。 此時, 您可以設定分鏡腳本和動畫變數的事件。 當您實際需要執行動畫時, 請呼叫 CAnimationController:: ScheduleGroup。

##  <a name="canimationcontroller"></a>CAnimationController:: CAnimationController

構造動畫控制器。

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>CAnimationController:: CleanUpGroup

由架構呼叫, 以在已排程動畫時清除群組。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*pGroup*<br/>
要清除之動畫群組的指標。

### <a name="remarks"></a>備註

這個方法會從指定的群組中移除所有的轉換和主要畫面格, 因為它們在排程動畫之後並不相關。

##  <a name="createkeyframe"></a>CAnimationController:: CreateKeyframe

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

設定或釋放在動畫管理員的狀態變更時所要呼叫的處理常式。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否要設定或發行處理常式。

### <a name="return-value"></a>傳回值

如果已成功設定或發行處理常式, 則為 TRUE。

### <a name="remarks"></a>備註

當處理常式已設定 (已啟用) 時, Windows 動畫會在動畫管理員的狀態變更時呼叫 OnAnimationManagerStatusChanged。

##  <a name="enableanimationtimereventhandler"></a>CAnimationController:: EnableAnimationTimerEventHandler

設定或釋放計時事件的處理常式, 以及計時更新的處理常式。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否要設定或釋放處理常式。

*idleBehavior*<br/>
指定計時器更新處理常式的閒置行為。

### <a name="return-value"></a>傳回值

如果已成功設定或發行處理常式, 則為 TRUE;如果第二次呼叫此方法, 而不先釋放處理常式, 或發生任何其他錯誤, 則為 FALSE。

### <a name="remarks"></a>備註

當處理常式已設定 (已啟用) 時, Windows 動畫 API 會呼叫 OnAnimationTimerPreUpdate、OnAnimationTimerPostUpdate、OnRenderingTooSlow 方法。 您必須啟用動畫計時器, 才能允許 Windows 動畫 API 更新分鏡腳本。 否則, 您必須呼叫 CAnimationController:: UpdateAnimationManager, 以指示動畫管理員更新所有動畫變數的值。

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

設定或釋放要呼叫的優先順序比較處理常式, 以判斷是否可以取消、結束、修剪或壓縮已排程的分鏡腳本。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>參數

*dwHandlerType*<br/>
UI_ANIMATION_PHT_ 旗標的組合 (請參閱備註), 其指定要設定或發行的處理常式。

### <a name="return-value"></a>傳回值

如果已成功設定或發行處理常式, 則為 TRUE。

### <a name="remarks"></a>備註

當處理常式已設定 (已啟用) 時, Windows 動畫會呼叫下列虛擬方法, 視 dwHandlerType 而定:OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler 可以是下列旗標的組合:UI_ANIMATION_PHT_NONE-釋放所有處理常式 UI_ANIMATION_PHT_CANCEL-設定取消比較處理常式 UI_ANIMATION_PHT_CONCLUDE-設定結束比較處理常式 UI_ANIMATION_PHT_COMPRESS-設定壓縮比較處理常式 UI_ANIMATION_PHT_TRIM-set修剪比較處理常式 UI_ANIMATION_PHT_CANCEL_REMOVE-移除取消比較處理常式 UI_ANIMATION_PHT_CONCLUDE_REMOVE-移除結束比較處理常式 UI_ANIMATION_PHT_COMPRESS_REMOVE-移除壓縮比較處理常式 UI_ANIMATION_PHT_TRIM_REMOVE-移除修剪比較處理常式

##  <a name="enablestoryboardeventhandler"></a>CAnimationController:: EnableStoryboardEventHandler

設定或發行分鏡腳本狀態和更新事件的處理常式。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

*bEnable*<br/>
指定是否要設定或發行處理常式。

### <a name="return-value"></a>傳回值

如果已成功設定或發行處理常式, 則為 TRUE;如果現在找到指定的動畫群組, 或尚未起始指定群組的動畫, 且其內部分鏡腳本為 Null, 則為 FALSE。

### <a name="remarks"></a>備註

當處理常式已設定 (已啟用) 時, Windows 動畫 API 會呼叫 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虛擬方法。 已針對指定的動畫群組呼叫 CAnimationController:: 動畫之後, 必須設定處理常式, 因為它會建立封裝的 IUIAnimationStoryboard 物件。

##  <a name="findanimationgroup"></a>CAnimationController:: FindAnimationGroup

依群組識別碼尋找動畫群組。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定 GroupID。

*pStoryboard*<br/>
分鏡腳本的指標。

### <a name="return-value"></a>傳回值

動畫群組的指標, 如果找不到具有指定識別碼的群組, 則為 Null。

### <a name="remarks"></a>備註

使用此方法可在執行時間尋找動畫群組。 當具有特定 GroupID 的第一個動畫物件新增至動畫控制器時, 會建立一個群組, 並將其新增至動畫群組的內部清單。

##  <a name="findanimationobject"></a>CAnimationController:: FindAnimationObject

尋找包含指定之動畫變數的動畫物件。

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
輸出. 包含動畫物件的指標或 Null。

*ppGroup*<br/>
輸出. 包含含有動畫物件之動畫群組的指標, 或為 Null。

### <a name="return-value"></a>傳回值

如果找到物件, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當需要從傳入的動畫變數尋找動畫物件時, 從事件處理常式呼叫。

##  <a name="g_keyframestoryboardstart"></a>CAnimationController:: gkeyframeStoryboardStart

表示分鏡腳本開頭的主要畫面格。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>CAnimationController:: GetKeyframeStoryboardStart

傳回可識別分鏡腳本起點的主要畫面格。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>傳回值

基底主要畫面格的指標, 可識別分鏡腳本的起點。

### <a name="remarks"></a>備註

取得此主要畫面格, 以在分鏡腳本開始時, 以任何其他主要畫面或轉換為基礎。

##  <a name="getuianimationmanager"></a>CAnimationController:: GetUIAnimationManager

提供對封裝的 IUIAnimationManager 物件的存取。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>傳回值

IUIAnimationManager 介面的指標, 如果建立動畫管理員失敗, 則為 Null。

### <a name="remarks"></a>備註

如果目前的 OS 不支援 Windows 動畫 API, 這個方法會傳回 Null, 之後在 CAnimationController:: IsValid 上的所有後續呼叫都會傳回 FALSE。 您可能需要存取 IUIAnimationManager, 才能呼叫其介面方法, 而不是由動畫控制器加以包裝。

##  <a name="getuianimationtimer"></a>CAnimationController:: GetUIAnimationTimer

提供對封裝的 IUIAnimationTimer 物件的存取。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>傳回值

IUIAnimationTimer 介面的指標, 如果建立動畫計時器失敗, 則為 Null。

### <a name="remarks"></a>備註

如果目前的 OS 不支援 Windows 動畫 API, 這個方法會傳回 Null, 之後在 CAnimationController:: IsValid 上的所有後續呼叫都會傳回 FALSE。

##  <a name="getuitransitionfactory"></a>CAnimationController:: GetUITransitionFactory

IUIAnimationTransitionFactory 介面的指標, 如果建立轉換程式庫失敗, 則為 Null。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>傳回值

如果建立轉換 factory 失敗, 則為 IUIAnimationTransitionFactory 的指標或 Null。

### <a name="remarks"></a>備註

如果目前的 OS 不支援 Windows 動畫 API, 這個方法會傳回 Null, 之後在 CAnimationController:: IsValid 上的所有後續呼叫都會傳回 FALSE。

##  <a name="getuitransitionlibrary"></a>CAnimationController:: GetUITransitionLibrary

提供對封裝的 IUIAnimationTransitionLibrary 物件的存取。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>傳回值

IUIAnimationTransitionLibrary 介面的指標, 如果建立轉換程式庫失敗, 則為 Null。

### <a name="remarks"></a>備註

如果目前的 OS 不支援 Windows 動畫 API, 這個方法會傳回 Null, 之後在 CAnimationController:: IsValid 上的所有後續呼叫都會傳回 FALSE。

##  <a name="isanimationinprogress"></a>CAnimationController:: IsAnimationInProgress

告知是否至少有一個群組現正播放動畫。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>傳回值

如果此動畫控制器有動畫正在進行中, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

檢查動畫管理員的狀態, 如果狀態為 UI_ANIMATION_MANAGER_BUSY, 則傳回 TRUE。

##  <a name="isvalid"></a>CAnimationController:: IsValid

告訴動畫控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果動畫控制器有效, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

只有當目前的 OS 不支援 Windows 動畫 API, 且因為未註冊而導致動畫管理員的建立失敗時, 這個方法才會傳回 FALSE。 在初始化 COM 程式庫之後, 您至少需要呼叫 GetUIAnimationManager 一次, 使其設定此旗標。

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

指定動畫控制器是否有效。 如果目前的作業系統不支援 Windows 動畫 API, 此成員會設定為 FALSE。

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>CAnimationController:: m_lstAnimationGroups

屬於此動畫控制器的動畫群組清單。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

儲存動畫管理員 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>CAnimationController:: m_pAnimationTimer

儲存動畫計時器 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>CAnimationController:: m_pRelatedWnd

相關 CWnd 物件的指標, 可在動畫管理員的狀態變更時自動重新繪製, 或發生 post update 事件。 可以是 Null。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

儲存轉換 Factory COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>CAnimationController:: m_pTransitionLibrary

儲存轉換程式庫 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>CAnimationController:: OnAfterSchedule

當指定群組的動畫剛排程時, 由架構呼叫。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
已排程之動畫群組的指標。

### <a name="remarks"></a>備註

預設的執行會從指定的群組中移除主要畫面格, 並從屬於指定群組的動畫變數轉換。 可以在衍生類別中覆寫, 以便在動畫排程時採取任何其他動作。

##  <a name="onanimationintegervaluechanged"></a>CAnimationController:: OnAnimationIntegerValueChanged

當動畫變數的整數值已變更時由架構呼叫。

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
包含其值已變更之動畫物件的動畫群組指標。

*pObject*<br/>
動畫物件的指標, 其中包含值已變更的動畫變數。

*variable*<br/>
動畫變數的指標。

*newValue*<br/>
指定新的值。

*prevValue*<br/>
指定先前的值。

### <a name="remarks"></a>備註

如果您針對特定的動畫變數或動畫物件, 使用名為的 EnableIntegerValueChangedEvent 來啟用動畫變數事件, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController:: OnAnimationManagerStatusChanged

由架構呼叫, 以回應動畫管理員的 StatusChanged 事件。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*newStatus*<br/>
新的動畫管理員狀態。

*previousStatus*<br/>
先前的動畫管理員狀態。

### <a name="remarks"></a>備註

如果您使用 EnableAnimationManagerEvent 啟用動畫管理員事件, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如果已使用 SetRelatedWnd 設定相關的視窗, 則預設的執行會進行更新。

##  <a name="onanimationtimerpostupdate"></a>CAnimationController:: OnAnimationTimerPostUpdate

在動畫更新完成之後由架構呼叫。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>備註

如果您使用 EnableAnimationTimerEventHandler 來啟用計時器事件處理常式, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationtimerpreupdate"></a>CAnimationController:: OnAnimationTimerPreUpdate

在動畫更新開始之前, 由架構呼叫。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>備註

如果您使用 EnableAnimationTimerEventHandler 來啟用計時器事件處理常式, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController:: OnAnimationTimerRenderingTooSlow

當動畫的轉譯畫面播放速率低於最小的預期畫面播放速率時, 由架構呼叫。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>參數

*fps*<br/>
目前的畫面播放速率 (以每秒框架數為單位)。

### <a name="remarks"></a>備註

如果您使用 EnableAnimationTimerEventHandler 來啟用計時器事件處理常式, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 需要的最小畫面播放速率是藉由呼叫 IUIAnimationTimer:: SetFrameRateThreshold 來指定。

##  <a name="onanimationvaluechanged"></a>CAnimationController:: OnAnimationValueChanged

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
包含其值已變更之動畫物件的動畫群組指標。

*pObject*<br/>
動畫物件的指標, 其中包含值已變更的動畫變數。

*variable*<br/>
動畫變數的指標。

*newValue*<br/>
指定新的值。

*prevValue*<br/>
指定先前的值。

### <a name="remarks"></a>備註

如果您針對特定的動畫變數或動畫物件, 使用名為的 EnableValueChangedEvent 來啟用動畫變數事件, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onbeforeanimationstart"></a>CAnimationController:: OnBeforeAnimationStart

在排程動畫之前由架構呼叫。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
動畫即將開始的動畫群組指標。

### <a name="remarks"></a>備註

這個呼叫會路由至相關的 CWnd, 而且可以在衍生類別中覆寫, 以便在動畫開始進行指定的群組之前執行任何其他動作。

##  <a name="onhasprioritycancel"></a>CAnimationController:: OnHasPriorityCancel

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

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CANCEL 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如需有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊, 請參閱 WINDOWS 動畫 API 檔。

##  <a name="onhasprioritycompress"></a>CAnimationController:: OnHasPriorityCompress

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

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_COMPRESS 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如需有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊, 請參閱 WINDOWS 動畫 API 檔。

##  <a name="onhaspriorityconclude"></a>CAnimationController:: OnHasPriorityConclude

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

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CONCLUDE 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如需有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊, 請參閱 WINDOWS 動畫 API 檔。

##  <a name="onhasprioritytrim"></a>CAnimationController:: OnHasPriorityTrim

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

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_TRIM 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如需有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊, 請參閱 WINDOWS 動畫 API 檔。

##  <a name="onstoryboardstatuschanged"></a>CAnimationController:: OnStoryboardStatusChanged

當分鏡腳本狀態變更時由架構呼叫。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
擁有其狀態已變更之分鏡腳本的動畫群組指標。

*newStatus*<br/>
指定新的狀態。

*previousStatus*<br/>
指定先前的狀態。

### <a name="remarks"></a>備註

如果您使用 CAnimationController:: EnableStoryboardEventHandler 啟用分鏡腳本事件, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="onstoryboardupdated"></a>CAnimationController:: OnStoryboardUpdated

當腳本已更新時由架構呼叫。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*pGroup*<br/>
擁有分鏡腳本之群組的指標。

### <a name="remarks"></a>備註

如果您使用 CAnimationController:: EnableStoryboardEventHandler 啟用分鏡腳本事件, 則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

從動畫控制器移除所有的動畫群組。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>備註

將刪除所有群組, 其指標 (如果儲存在應用層級) 必須失效。 如果要刪除的群組的 CAnimationGroup:: m_bAutodestroyAnimationObjects 為 TRUE, 則會刪除屬於該群組的所有動畫物件;否則, 其父動畫控制器的參考將會設定為 Null, 而且可以加入至另一個控制器。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

從動畫控制器移除具有指定之識別碼的動畫群組。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定動畫群組識別碼。

### <a name="remarks"></a>備註

這個方法會從群組的內部清單中移除動畫群組, 並將它刪除, 因此, 如果您儲存該動畫群組的指標, 它就必須是不正確。 如果 CAnimationGroup:: m_bAutodestroyAnimationObjects 為 TRUE, 則會刪除屬於該群組的所有動畫物件;否則, 其父動畫控制器的參考將會設定為 Null, 而且可以加入至另一個控制器。

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

從動畫控制器移除動畫物件。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>參數

*pObject*<br/>
動畫物件的指標。

*bNoDelete*<br/>
如果此參數為 TRUE, 則不會在移除時刪除物件。

### <a name="remarks"></a>備註

從動畫控制器和動畫群組移除動畫物件。 如果特定物件不應該再動畫, 或如果您需要將物件移至另一個動畫控制器, 請呼叫此函式。 在最後一個案例中, bNoDelete 必須為 TRUE。

##  <a name="removetransitions"></a>CAnimationController:: RemoveTransitions

從屬於指定群組的動畫物件中移除轉換。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定群組識別碼。

### <a name="remarks"></a>備註

群組會對其動畫物件進行迴圈, 並針對每個動畫物件呼叫 ClearTransitions (FALSE)。 在排程動畫之後, 架構會呼叫這個方法。

##  <a name="schedulegroup"></a>CAnimationController:: ScheduleGroup

排定動畫。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>參數

*nGroupID*<br/>
指定要排程的動畫群組識別碼。

*time*<br/>
指定排程的時間。

### <a name="return-value"></a>傳回值

如果已成功排程動畫, 則為 TRUE。 如果尚未建立分鏡腳本, 或發生其他錯誤, 則為 FALSE。

### <a name="remarks"></a>備註

您必須呼叫 AnimateGroup, 並將參數 bScheduleNow 設為 FALSE, 然後再 ScheduleGroup。 您可以指定從 IUIAnimationTimer:: GetTime 取得的所需動畫時間。 如果時間參數為 0.0, 動畫會排定目前的時間。

##  <a name="setrelatedwnd"></a>CAnimationController:: SetRelatedWnd

建立動畫控制器和視窗之間的關聯性。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
要設定的 window 物件指標。

### <a name="remarks"></a>備註

如果已設定相關的 CWnd 物件, 當動畫管理員的狀態變更或計時器更新後事件發生時, 動畫控制器可以自動更新 (傳送 WM_PAINT 訊息)。

##  <a name="updateanimationmanager"></a>CAnimationController:: UpdateAnimationManager

指示動畫管理員更新所有動畫變數的值。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>備註

呼叫這個方法會讓動畫管理員前進到目前的時間, 並視需要變更分鏡腳本的狀態, 並將任何動畫變數更新為適當的插入值。 就內部而言, 這個方法會呼叫 IUIAnimationTimer:: GetTime (timeNow) 和 IUIAnimationManager:: Update (timeNow)。 在衍生類別中覆寫這個方法, 以自訂此行為。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
