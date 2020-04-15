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
ms.openlocfilehash: 34a02567bfeb76666cc38ccf05dcc285a1f658f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369759"
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
|[動畫控制器::動畫控制器](#canimationcontroller)|構造動畫控制器。|
|[動畫控制器::~動畫控制器](#_dtorcanimationcontroller)|解構函式。 銷毀動畫控制器物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫控制器::新增動畫物件](#addanimationobject)|將動畫物件添加到屬於動畫控制器的組。|
|[動畫控制器::將關鍵幀新增到組](#addkeyframetogroup)|將關鍵幀添加到組。|
|[動畫控制器::動畫組](#animategroup)|準備一個組來運行動畫,並選擇性地安排它。|
|[動畫控制器::清理組](#cleanupgroup)|已多載。 由框架調用,以在計劃動畫時清理組。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|已多載。 建立隨轉換而改變的主要畫面格，將它加入指定的群組。|
|[動畫控制器::啟用動畫管理員事件](#enableanimationmanagerevent)|設置或釋放在動畫管理器狀態更改時調用的處理程式。|
|[動畫控制器::啟用動畫計時器事件處理程式](#enableanimationtimereventhandler)|設置或釋放計時事件處理程式和計時更新處理程式。|
|[動畫控制器::啟用優先權比較處理程式](#enableprioritycomparisonhandler)|設置或釋放要調用的優先順序比較處理程式,以確定是否可以取消、完成、修剪或壓縮計劃情節提要。|
|[動畫控制器::啟用故事板事件處理程式](#enablestoryboardeventhandler)|設置或釋放情節提要狀態和更新事件的處理程式。|
|[動畫控制器::尋找動畫群組](#findanimationgroup)|已多載。 按情節提要查找動畫組。|
|[動畫控制器::尋找動畫物件](#findanimationobject)|查找包含指定動畫變數的動畫物件。|
|[動畫控制器::獲取關鍵幀故事板啟動](#getkeyframestoryboardstart)|返回標識情節提要開頭的關鍵幀。|
|[動畫控制器::抓取動畫管理員](#getuianimationmanager)|提供對封裝的 IUI動畫管理員物件的訪問。|
|[動畫控制器::取得動畫計時器](#getuianimationtimer)|提供對封裝的 IUI動畫定時對象的訪問。|
|[動畫控制器::取得 UI 轉換工廠](#getuitransitionfactory)|如果創建過渡庫失敗,則指向 IUIAnimation 轉換工廠介面或 NULL 的指標。|
|[動畫控制器::取得 UI 轉換庫](#getuitransitionlibrary)|提供對封裝的 IUI 動畫轉換庫對象的訪問。|
|[動畫控制器::動畫在進行中](#isanimationinprogress)|告訴是否至少有一個組正在播放動畫。|
|[動畫控制器::有效](#isvalid)|告訴動畫控制器是否有效。|
|[動畫控制器::在動畫中值已更改](#onanimationintegervaluechanged)|當動畫變數的整數值發生更改時,由框架調用。|
|[動畫控制器::打開動畫管理員狀態已變更](#onanimationmanagerstatuschanged)|由框架呼叫以回應動畫管理器中的狀態更改事件。|
|[動畫控制器::打開動畫計時器后更新](#onanimationtimerpostupdate)|動畫更新完成後由框架調用。|
|[動畫控制器::打開動畫計時器預更新](#onanimationtimerpreupdate)|在動畫更新開始之前由框架調用。|
|[動畫控制器::動畫計時器渲染速度慢](#onanimationtimerrenderingtooslow)|當動畫的渲染幀速率低於所需的最小幀速率時,由框架調用。|
|[動畫控制器::打開動畫值已變更](#onanimationvaluechanged)|當動畫變數的值發生更改時,由框架調用。|
|[動畫控制器::在動畫啟動之前開啟](#onbeforeanimationstart)|在計劃動畫之前由框架調用。|
|[動畫控制器::onHas優先取消](#onhasprioritycancel)|由架構呼叫來解決排程衝突。|
|[動畫控制器::打開哈斯優先壓縮](#onhasprioritycompress)|由架構呼叫來解決排程衝突。|
|[動畫控制器::onHas優先結束](#onhaspriorityconclude)|由架構呼叫來解決排程衝突。|
|[動畫控制器::onHas優先修剪](#onhasprioritytrim)|由架構呼叫來解決排程衝突。|
|[動畫控制器::在故事板狀態更改](#onstoryboardstatuschanged)|情節提要狀態更改時由框架調用。|
|[動畫控制器::在故事板上更新](#onstoryboardupdated)|更新情節提要時由框架調用。|
|[動畫控制器::刪除所有動畫群組](#removeallanimationgroups)|從動畫控制器中刪除所有動畫組。|
|[動畫控制器::刪除動畫群組](#removeanimationgroup)|從動畫控制器中刪除具有指定 ID 的動畫組。|
|[動畫控制器::刪除動畫物件](#removeanimationobject)|從動畫控制器中刪除動畫物件。|
|[動畫控制器::刪除轉換](#removetransitions)|從屬於指定組的動畫物件中刪除過渡。|
|[動畫控制器::計劃組](#schedulegroup)|計劃動畫。|
|[動畫控制器::設定相關](#setrelatedwnd)|在動畫控制器和窗口之間建立關係。|
|[動畫控制器::更新動畫管理員](#updateanimationmanager)|指示動畫管理器更新所有動畫變數的值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫控制器::清理組](#cleanupgroup)|已多載。 清理組的説明者。|
|[動畫控制器::在計劃后](#onafterschedule)|當指定組的動畫剛剛計劃時,由框架調用。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫控制器::關鍵幀故事板啟動](#g_keyframestoryboardstart)|表示情節提要開頭的關鍵幀。|
|[動畫控制器::m_bIsValid](#m_bisvalid)|指定動畫控制器是否有效。 如果目前作業系統不支援 Windows 動畫 API,則此成員設置為 FALSE。|
|[動畫控制器::m_lstAnimationGroups](#m_lstanimationgroups)|屬於此動畫控制器的動畫組的清單。|
|[動畫控制器::m_pAnimationManager](#m_panimationmanager)|儲存指向動畫管理員 COM 物件的指標。|
|[動畫控制器::m_pAnimationTimer](#m_panimationtimer)|儲存指向動畫計時器 COM 物件的指標。|
|[動畫控制器::m_pRelatedWnd](#m_prelatedwnd)|指向相關 CWnd 物件的指標,可在動畫管理器的狀態更改或更新後事件發生時自動重繪。 可以是 NULL。|
|[動畫控制器::m_pTransitionFactory](#m_ptransitionfactory)|儲存指向過渡工廠 COM 物件的指標。|
|[動畫控制器::m_pTransitionLibrary](#m_ptransitionlibrary)|儲存指向過渡庫 COM 物件的指標。|

## <a name="remarks"></a>備註

CAnimationController 類是管理動畫的鍵類。 您可以在應用程式中創建一個或多個動畫控制器實例,也可以使用 CAnimationController::SetNdnd 將動畫控制器的實例連接到 CWnd 物件。 當動畫管理員狀態發生更改或動畫計時器更新時,需要此連接自動將WM_PAINT訊息發送到相關視窗。 如果不啟用此關係,則必須重新繪製手動顯示動畫的視窗。 為此,可以從 CAnimationController 派生一個類,並重寫 OnAnimationManagerStatus 已更改和/或 OnAnimationTimerPostUpdate,並在必要時使一個或多個視窗無效。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>動畫控制器::~動畫控制器

解構函式。 銷毀動畫控制器物件時調用。

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>動畫控制器::新增動畫物件

將動畫物件添加到屬於動畫控制器的組。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>參數

*pObject*<br/>
指向動畫物件的指標。

### <a name="return-value"></a>傳回值

指向現有或新動畫組的指標,其中已添加 pObject(如果函數成功);如果函數成功,則指向現有動畫組或新動畫組。如果 pObject 已新增到屬於另一個動畫控制器的組,則為 NULL。

### <a name="remarks"></a>備註

調用此方法以向動畫控制器添加動畫物件。 對象將根據物件的組 ID 添加到組(請參閱 CAnimationBaseObject:SetID)。 如果動畫控制器是使用指定的 GroupID 添加的第一個物件,則該組將創建新組。 動畫物件只能添加到一個動畫控制器。 如果需要將物件添加到其他控制器,請先調用刪除動畫物件。 如果為已添加到組的物件呼叫 SetID,則該物件將從舊組中刪除,並添加到具有指定 ID 的另一個組中。

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>動畫控制器::將關鍵幀新增到組

將關鍵幀添加到組。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*p 鍵框*<br/>
指向關鍵幀的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

通常不需要調用此方法,而是使用 CAnimationController::createKeyframe,它會自動創建已創建的關鍵幀並將其添加到組中。

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>動畫控制器::動畫組

準備一個組來運行動畫,並選擇性地安排它。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*b 時間表現在*<br/>
指定是否直接運行動畫。

### <a name="return-value"></a>傳回值

如果動畫已成功計劃並運行,則為 TRUE。

### <a name="remarks"></a>備註

此方法執行創建情節提要、添加動畫變數、應用過渡和設置關鍵幀的實際工作。 如果將 b-計劃現在設置為 FALSE,則可以延遲計劃。 在這種情況下,指定的組將保存已為動畫設置的情節提要。 此時,您可以為情節提要和動畫變數設置事件。 當您實際需要運行動畫調用 CAnimation 控制器::計劃組。

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>動畫控制器::動畫控制器

構造動畫控制器。

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>動畫控制器::清理組

由框架調用,以在計劃動畫時清理組。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*p組*<br/>
要清理的動畫組的指標。

### <a name="remarks"></a>備註

此方法從指定的組中刪除所有過渡和關鍵幀,因為它們在計劃動畫后不相關。

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>動畫控制器::建立關鍵幀

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

*n集團ID*<br/>
指定主要畫面格建立對象的群組識別碼。

*p 轉換*<br/>
轉換指標。 這項轉換之後，主要畫面格就會插入分鏡腳本中。

*p 鍵框*<br/>
這個主要畫面格的基底主要畫面格指標。

*位移*<br/>
pKeyframe 指定的基底主要畫面格位移，以秒為單位。

### <a name="return-value"></a>傳回值

函式成功後，新建立的主要畫面格指標。

### <a name="remarks"></a>備註

您可以儲存傳回的指標，讓其他的主要畫面格以新建立的主要畫面格為基礎 (請參閱第二個多載)。 即可開始主要畫面格的轉換，請參閱 CBaseTransition::SetKeyframes。 您不需要刪除以這種方式建立的主要畫面格，因為動畫群組會自動刪除它們。 根據其他主要畫面格和轉換建立主要畫面格時要小心，避免循環參照。

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>動畫控制器::啟用動畫管理員事件

設置或釋放在動畫管理器狀態更改時調用的處理程式。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
指定是設置還是釋放處理程式。

### <a name="return-value"></a>傳回值

如果處理程式已成功設置或釋放,則為 TRUE。

### <a name="remarks"></a>備註

設置(啟用)處理程式時,Windows 動畫在動畫管理器的狀態更改時調用 OnAnimationManager 狀態更改。

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>動畫控制器::啟用動畫計時器事件處理程式

設置或釋放計時事件處理程式和計時更新處理程式。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
指定是設置還是釋放處理程式。

*閒置行為*<br/>
為計時器更新處理程式指定空閒行為。

### <a name="return-value"></a>傳回值

如果已成功設置或釋放處理程式,則為 TRUE;如果操作器已成功設置或釋放,則為 TRUE。如果在不首先釋放處理程序的情況下第二次調用此方法,或者發生任何其他錯誤,則 FALSE。

### <a name="remarks"></a>備註

當處理程式設定(啟用)Windows 動畫 API 調用上動畫計時器預更新、上動畫計時器更新、"渲染太慢"方法。 您需要啟用動畫計時器以允許 Windows 動畫 API 更新情節提要。 否則,您需要調用 CAnimationController::更新動畫管理器,以便指示動畫管理器更新所有動畫變數的值。

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>動畫控制器::啟用優先權比較處理程式

設置或釋放要調用的優先順序比較處理程式,以確定是否可以取消、完成、修剪或壓縮計劃情節提要。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>參數

*德漢德勒型*<br/>
UI_ANIMATION_PHT_標誌(請參閱備註)的組合,它指定要設置或釋放的處理程式。

### <a name="return-value"></a>傳回值

如果處理程式已成功設置或釋放,則為 TRUE。

### <a name="remarks"></a>備註

設置(啟用)處理程式時,Windows 動畫會根據 dwHandlerType 調用以下虛擬方法:OnHas優先取消、OnHas優先結束、OnHas優先修剪、OnHas優先壓縮。 dwHandler 可以是以下旗標的組合: UI_ANIMATION_PHT_NONE - 釋放UI_ANIMATION_PHT_CANCEL - 設定取消比較處理程式UI_ANIMATION_PHT_CONCLUDE - 設定"結束比較處理程式UI_ANIMATION_PHT_COMPRESS - 設定壓縮比較處理程式 UI_ANIMATION_PHT_TRIM - 設定修剪比較處理程式UI_ANIMATION_PHT_CANCEL_REMOVE - 刪除取消比較處理程式UI_ANIMATION_PHT_CONCLUDE_REMOVE - 刪除UI_ANIMATION_PHT_COMPRESS_REMOVE結束比較處理程式 - 刪除壓縮比較處理程式UI_ANIMATION_PHT_TRIM_REMOVE -移除修剪比較處理程式

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>動畫控制器::啟用故事板事件處理程式

設置或釋放情節提要狀態和更新事件的處理程式。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*b 啟用*<br/>
指定是設置還是釋放處理程式。

### <a name="return-value"></a>傳回值

如果處理程式已成功設置或釋放,則為 TRUE;如果處理程式已成功設置或釋放該處理程式,則為 TRUE。如果現在找到指定的動畫組,或者尚未啟動指定組的動畫,並且其內部情節提要為 NULL,則 FALSE。

### <a name="remarks"></a>備註

設置(啟用)處理程式時,Windows 動畫 API 將調用 OnStoryboard 狀態更改和 OnStoryboard 更新的虛擬方法。 處理程式必須在 CAnimationController::Animate 為指定的動畫組調用,因為它創建封裝的 IUIAnimateStoryboard 物件。

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>動畫控制器::尋找動畫群組

按組 ID 查找動畫組。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*板*<br/>
指向情節提要的指標。

### <a name="return-value"></a>傳回值

如果找不到具有指定 ID 的組,則指向動畫群組或 NULL 的指標。

### <a name="remarks"></a>備註

使用此方法在運行時查找動畫組。 將具有特定 GroupID 的第一個動畫物件添加到動畫控制器時,將創建組並將其添加到動畫組的內部清單中。

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>動畫控制器::尋找動畫物件

查找包含指定動畫變數的動畫物件。

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>參數

*pvariable*<br/>
指向動畫變數的指標。

*ppObject*<br/>
輸出。 包含指向動畫物件或 NULL 的指標。

*ppGroup*<br/>
輸出。 包含指向保存動畫物件的動畫組的指標,或 NULL。

### <a name="return-value"></a>傳回值

如果找到物件,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

從事件處理程式調用,當它需要從傳入動畫變數查找動畫物件時。

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>動畫控制器::關鍵幀故事板啟動

表示情節提要開頭的關鍵幀。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>動畫控制器::獲取關鍵幀故事板啟動

返回標識情節提要開頭的關鍵幀。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>傳回值

指向基本關鍵幀的指標,用於標識情節提要的開頭。

### <a name="remarks"></a>備註

獲取此關鍵幀以基於情節提要啟動時的時間時刻設置任何其他關鍵幀或過渡。

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>動畫控制器::抓取動畫管理員

提供對封裝的 IUI動畫管理員物件的訪問。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>傳回值

如果動畫管理員的建立失敗,則指向 IUI動畫管理器介面或 NULL 的指標。

### <a name="remarks"></a>備註

如果目前作業系統不支援 Windows 動畫 API,則此方法將返回 NULL,之後 CAnimationController 上的所有後續呼叫:有效傳回 FALSE。 您可能需要存取 IUI動畫管理器才能呼叫其介面方法,這些方法不是由動畫控制器包裝的。

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>動畫控制器::取得動畫計時器

提供對封裝的 IUI動畫定時對象的訪問。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>傳回值

如果動畫計時器的創建失敗,則指向 IUIAnimationTimer 介面或 NULL 的指標。

### <a name="remarks"></a>備註

如果目前作業系統不支援 Windows 動畫 API,則此方法將返回 NULL,之後 CAnimationController 上的所有後續呼叫:有效傳回 FALSE。

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>動畫控制器::取得 UI 轉換工廠

如果創建過渡庫失敗,則指向 IUIAnimation 轉換工廠介面或 NULL 的指標。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>傳回值

如果轉換工廠的建立失敗,則指向 IUIAnimation 轉換工廠或 NULL 的指標。

### <a name="remarks"></a>備註

如果目前作業系統不支援 Windows 動畫 API,則此方法將返回 NULL,之後 CAnimationController 上的所有後續呼叫:有效傳回 FALSE。

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>動畫控制器::取得 UI 轉換庫

提供對封裝的 IUI 動畫轉換庫對象的訪問。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>傳回值

如果建立過渡庫失敗,則指向 IUIAnimation 轉換庫介面或 NULL 的指標。

### <a name="remarks"></a>備註

如果目前作業系統不支援 Windows 動畫 API,則此方法將返回 NULL,之後 CAnimationController 上的所有後續呼叫:有效傳回 FALSE。

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>動畫控制器::動畫在進行中

告訴是否至少有一個組正在播放動畫。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>傳回值

如果此動畫控制器正在進行動畫,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

檢查動畫管理器的狀態,如果狀態為UI_ANIMATION_MANAGER_BUSY,則返回 TRUE。

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>動畫控制器::有效

告訴動畫控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果動畫控制器有效,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

僅當當前作業系統不支援 Windows 動畫 API 且動畫管理器的創建失敗,因為它未註冊時,此方法才會返回 FALSE。 在 COM 庫初始化後,需要至少呼叫 GetUI 動畫管理器一次,以便設置此標誌。

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>動畫控制器::m_bIsValid

指定動畫控制器是否有效。 如果目前作業系統不支援 Windows 動畫 API,則此成員設置為 FALSE。

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>動畫控制器::m_lstAnimationGroups

屬於此動畫控制器的動畫組的清單。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>動畫控制器::m_pAnimationManager

儲存指向動畫管理員 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>動畫控制器::m_pAnimationTimer

儲存指向動畫計時器 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>動畫控制器::m_pRelatedWnd

指向相關 CWnd 物件的指標,可在動畫管理器的狀態更改或更新後事件發生時自動重繪。 可以是 NULL。

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>動畫控制器::m_pTransitionFactory

儲存指向過渡工廠 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>動畫控制器::m_pTransitionLibrary

儲存指向過渡庫 COM 物件的指標。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>動畫控制器::在計劃后

當指定組的動畫剛剛計劃時,由框架調用。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向已計劃的動畫組的指標。

### <a name="remarks"></a>備註

預設實現從指定組中刪除關鍵幀,並從屬於指定組的動畫變數轉換。 可以在派生類中重寫,以便根據動畫計劃執行任何其他操作。

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>動畫控制器::在動畫中值已更改

當動畫變數的整數值發生更改時,由框架調用。

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向包含其值已更改的動畫物件的動畫組的指標。

*pObject*<br/>
指向動畫物件的指標,該物件包含其值已更改的動畫變數。

*變動*<br/>
指向動畫變數的指標。

*newValue*<br/>
指定新值。

*前置值*<br/>
指定以前的值。

### <a name="remarks"></a>備註

如果啟用啟用啟用 IntegerValue改變事件為特定動畫變數或動畫物件啟用動畫變數事件,則調用此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>動畫控制器::打開動畫管理員狀態已變更

由框架呼叫以回應動畫管理器中的狀態更改事件。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*新狀態*<br/>
新的動畫管理器狀態。

*前一個狀態*<br/>
以前的動畫管理器狀態。

### <a name="remarks"></a>備註

如果使用啟用動畫管理器事件啟用動畫管理器事件,則調用此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 如果已使用 SetTheNd 設置相關視窗,則預設實現將更新該視窗。

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>動畫控制器::打開動畫計時器后更新

動畫更新完成後由框架調用。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>備註

如果使用啟用動畫計時器事件處理程式啟用計時器事件處理程式,則呼叫此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>動畫控制器::打開動畫計時器預更新

在動畫更新開始之前由框架調用。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>備註

如果使用啟用動畫計時器事件處理程式啟用計時器事件處理程式,則呼叫此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>動畫控制器::動畫計時器渲染速度慢

當動畫的渲染幀速率低於所需的最小幀速率時,由框架調用。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>參數

*Fps*<br/>
當前幀速率(以幀/秒表示)。

### <a name="remarks"></a>備註

如果使用啟用動畫計時器事件處理程式啟用計時器事件處理程式,則呼叫此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 通過調用 IUI動畫計時器::設置FrameRate閾值來指定所需的最小幀速率。

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>動畫控制器::打開動畫值已變更

當動畫變數的值發生更改時,由框架調用。

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向包含其值已更改的動畫物件的動畫組的指標。

*pObject*<br/>
指向動畫物件的指標,該物件包含其值已更改的動畫變數。

*變動*<br/>
指向動畫變數的指標。

*newValue*<br/>
指定新值。

*前置值*<br/>
指定以前的值。

### <a name="remarks"></a>備註

如果啟用動畫變數事件,啟用啟用ValueChangedEvent為特定動畫變數或動畫物件調用,則調用此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>動畫控制器::在動畫啟動之前開啟

在計劃動畫之前由框架調用。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向其動畫即將開始的動畫組的指標。

### <a name="remarks"></a>備註

此調用路由到相關的 CWnd,並且可以在派生類中重寫,以在指定組的動畫啟動之前執行任何其他操作。

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>動畫控制器::onHas優先取消

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*p 組元計劃*<br/>
擁有目前排程的分鏡腳本的群組。

*p群組新*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*優先順序效果*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CANCEL 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊,請閱讀 Windows 動畫 API 文檔。

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>動畫控制器::打開哈斯優先壓縮

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*p 組元計劃*<br/>
擁有目前排程的分鏡腳本的群組。

*p群組新*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*優先順序效果*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_COMPRESS 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊,請閱讀 Windows 動畫 API 文檔。

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>動畫控制器::onHas優先結束

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*p 組元計劃*<br/>
擁有目前排程的分鏡腳本的群組。

*p群組新*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*優先順序效果*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_CONCLUDE 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊,請閱讀 Windows 動畫 API 文檔。

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>動畫控制器::onHas優先修剪

由架構呼叫來解決排程衝突。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>參數

*p 組元計劃*<br/>
擁有目前排程的分鏡腳本的群組。

*p群組新*<br/>
擁有新分鏡腳本的群組，其與 pGroupScheduled 所擁有的排定分鏡腳本發生排程衝突。

*優先順序效果*<br/>
如果 pGroupScheduled 具有較高的優先順序，可能會影響 pGroupNew。

### <a name="return-value"></a>傳回值

如果 pGroupNew 所擁有的分鏡腳本優先適用，應傳回 TRUE。 如果 pGroupScheduled 所擁有的分鏡腳本優先適用，應傳回 FALSE。

### <a name="remarks"></a>備註

如果您使用 CAnimationController::EnablePriorityComparisonHandler 和指定 UI_ANIMATION_PHT_TRIM 來啟用優先順序比較事件，則會呼叫這個方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。 有關[衝突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的詳細資訊,請閱讀 Windows 動畫 API 文檔。

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>動畫控制器::在故事板狀態更改

情節提要狀態更改時由框架調用。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向具有狀態已更改的情節提要的動畫組的指標。

*新狀態*<br/>
指定新狀態。

*前一個狀態*<br/>
指定上一個狀態。

### <a name="remarks"></a>備註

如果使用 C動畫控制器::啟用 Storyboard 事件處理程序啟用情節提要事件,則調用此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>動畫控制器::在故事板上更新

更新情節提要時由框架調用。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向擁有情節提要的組的指標。

### <a name="remarks"></a>備註

如果使用 C動畫控制器::啟用 Storyboard 事件處理程序啟用情節提要事件,則調用此方法。 可覆寫衍生類別中的該方法來採取應用程式的特定動作。

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>動畫控制器::刪除所有動畫群組

從動畫控制器中刪除所有動畫組。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>備註

所有組都將被刪除,如果存儲在應用程式級別,其指標必須失效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects刪除的組為 TRUE,則屬於該組的所有動畫物件都將被刪除;如果 CAnimationGroup:m_bAutodestroyAnimationObjects 為要刪除的組,則屬於該組的所有動畫物件都將被刪除。否則,它們對父動畫控制器的引用將設置為 NULL,並且可以添加到其他控制器。

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>動畫控制器::刪除動畫群組

從動畫控制器中刪除具有指定 ID 的動畫組。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定動畫組識別碼。

### <a name="remarks"></a>備註

此方法從組的內部清單中刪除動畫組並刪除它,因此,如果您存儲了指向該動畫組的指標,則必須將其失效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects 為 TRUE,則屬於該組的所有動畫物件都將被刪除;如果 CAnimationGroup::m_bAutodestroyAnimationObjects 為 TRUE,則屬於該組的所有動畫物件都將被刪除。否則,它們對父動畫控制器的引用將設置為 NULL,並且可以添加到其他控制器。

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>動畫控制器::刪除動畫物件

從動畫控制器中刪除動畫物件。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>參數

*pObject*<br/>
指向動畫物件的指標。

*b 不刪除*<br/>
如果此參數為 TRUE,則刪除後不會刪除物件。

### <a name="remarks"></a>備註

從動畫控制器和動畫組中刪除動畫物件。 如果不應再對特定物件進行動畫處理,或者需要將對象移動到其他動畫控制器,請調用此函數。 在最後一種情況下,bNoDelete 必須為 TRUE。

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>動畫控制器::刪除轉換

從屬於指定組的動畫物件中刪除過渡。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

### <a name="remarks"></a>備註

該組迴圈在其動畫物件上,併為每個動畫物件調用 ClearTransition(FALSE)。 計劃動畫后,框架將調用此方法。

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>動畫控制器::計劃組

計劃動畫。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定要計劃動畫組 ID。

*time*<br/>
指定計劃時間。

### <a name="return-value"></a>傳回值

如果動畫計劃成功,則為 TRUE。 如果未創建情節提要,或者發生其他錯誤,則 FALSE。

### <a name="remarks"></a>備註

您必須呼叫 AnimateGroup,參數 b"計劃現在"設置為 FALSE,提前計畫組。 您可以指定從 IUI 動畫計時器獲得所需的動畫時間::獲取時間。 如果時間參數為 0.0,則動畫將安排在當前時間。

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>動畫控制器::設定相關

在動畫控制器和窗口之間建立關係。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
要設置的視窗物件的指標。

### <a name="remarks"></a>備註

如果設置了相關的 CWnd 物件,則動畫控制器可以在動畫管理器的狀態發生或更新事件後計時器發生時自動更新它(發送WM_PAINT消息)。

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>動畫控制器::更新動畫管理員

指示動畫管理器更新所有動畫變數的值。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>備註

調用此方法會將動畫管理器提升為當前時間,根據需要更改情節提要的狀態,並將任何動畫變數更新為適當的插值。 在內部,此方法調用 IUI動畫計時器::獲取時間(現在)和 IUI動畫管理器:更新(現在)。 重寫派生類中的此方法以自定義此行為。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
