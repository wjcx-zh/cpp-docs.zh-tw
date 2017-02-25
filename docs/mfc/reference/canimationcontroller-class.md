---
title: "CAnimationController 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationController"
  - "afxanimationcontroller/CAnimationController"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationController 類別"
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationController 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作動畫控制器，提供用來建立和管理動畫的中央介面。  
  
## 語法  
  
```  
class CAnimationController : public CObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationController::CAnimationController](../Topic/CAnimationController::CAnimationController.md)|建構動畫控制器。|  
|[CAnimationController::~CAnimationController](../Topic/CAnimationController::~CAnimationController.md)|解構函式。  當正在終結動畫控制器物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationController::AddAnimationObject](../Topic/CAnimationController::AddAnimationObject.md)|將動畫物件加入至屬於動畫控制器的群組。|  
|[CAnimationController::AddKeyframeToGroup](../Topic/CAnimationController::AddKeyframeToGroup.md)|將主要畫面格加入至群組。|  
|[CAnimationController::AnimateGroup](../Topic/CAnimationController::AnimateGroup.md)|準備要執行動畫的群組，並選擇性地將其排程。|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|多載。  在排定動畫後，由架構呼叫以清除群組。|  
|[CAnimationController::CreateKeyframe](../Topic/CAnimationController::CreateKeyframe.md)|多載。  建立相依於轉換的主要畫面格，並將它加入至指定的群組。|  
|[CAnimationController::EnableAnimationManagerEvent](../Topic/CAnimationController::EnableAnimationManagerEvent.md)|設定或釋放要在動畫管理員狀態變更時呼叫的處理常式。|  
|[CAnimationController::EnableAnimationTimerEventHandler](../Topic/CAnimationController::EnableAnimationTimerEventHandler.md)|設定或釋放計時事件處理常式及計時更新處理常式。|  
|[CAnimationController::EnablePriorityComparisonHandler](../Topic/CAnimationController::EnablePriorityComparisonHandler.md)|設定或釋放要呼叫的優先順序比較處理常式，以判斷是否可以取消、結束、修剪或壓縮已排程的腳本。|  
|[CAnimationController::EnableStoryboardEventHandler](../Topic/CAnimationController::EnableStoryboardEventHandler.md)|設定或釋放腳本狀態及更新事件的處理常式。|  
|[CAnimationController::FindAnimationGroup](../Topic/CAnimationController::FindAnimationGroup.md)|多載。  依據其腳本尋找動畫群組。|  
|[CAnimationController::FindAnimationObject](../Topic/CAnimationController::FindAnimationObject.md)|尋找包含指定之動畫變數的動畫物件。|  
|[CAnimationController::GetKeyframeStoryboardStart](../Topic/CAnimationController::GetKeyframeStoryboardStart.md)|傳回識別腳本開始處的主要畫面格。|  
|[CAnimationController::GetUIAnimationManager](../Topic/CAnimationController::GetUIAnimationManager.md)|可讓您存取封裝的 IUIAnimationManager 物件。|  
|[CAnimationController::GetUIAnimationTimer](../Topic/CAnimationController::GetUIAnimationTimer.md)|可讓您存取封裝的 IUIAnimationTimer 物件。|  
|[CAnimationController::GetUITransitionFactory](../Topic/CAnimationController::GetUITransitionFactory.md)|IUIAnimationTransitionFactory 介面的指標，如果轉換程式庫建立失敗，則為 NULL。|  
|[CAnimationController::GetUITransitionLibrary](../Topic/CAnimationController::GetUITransitionLibrary.md)|可讓您存取封裝的 IUIAnimationTransitionLibrary 物件。|  
|[CAnimationController::IsAnimationInProgress](../Topic/CAnimationController::IsAnimationInProgress.md)|判斷是否至少一個群組正在播放動畫。|  
|[CAnimationController::IsValid](../Topic/CAnimationController::IsValid.md)|判斷動畫控制器是否有效。|  
|[CAnimationController::OnAnimationIntegerValueChanged](../Topic/CAnimationController::OnAnimationIntegerValueChanged.md)|在動畫變數的整數值已變更時，由架構呼叫。|  
|[CAnimationController::OnAnimationManagerStatusChanged](../Topic/CAnimationController::OnAnimationManagerStatusChanged.md)|由架構呼叫以回應動畫管理員的 StatusChanged 事件。|  
|[CAnimationController::OnAnimationTimerPostUpdate](../Topic/CAnimationController::OnAnimationTimerPostUpdate.md)|在動畫更新完成後，由架構呼叫。|  
|[CAnimationController::OnAnimationTimerPreUpdate](../Topic/CAnimationController::OnAnimationTimerPreUpdate.md)|在動畫更新開始前，由架構呼叫。|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](../Topic/CAnimationController::OnAnimationTimerRenderingTooSlow.md)|當動畫的轉譯畫面播放速率低於所需的最小畫面格速率時，會由架構呼叫。|  
|[CAnimationController::OnAnimationValueChanged](../Topic/CAnimationController::OnAnimationValueChanged.md)|在動畫變數的值已變更時，由架構呼叫。|  
|[CAnimationController::OnBeforeAnimationStart](../Topic/CAnimationController::OnBeforeAnimationStart.md)|在排程動畫前，立即由架構呼叫。|  
|[CAnimationController::OnHasPriorityCancel](../Topic/CAnimationController::OnHasPriorityCancel.md)|由架構呼叫以解決排程衝突。|  
|[CAnimationController::OnHasPriorityCompress](../Topic/CAnimationController::OnHasPriorityCompress.md)|由架構呼叫以解決排程衝突。|  
|[CAnimationController::OnHasPriorityConclude](../Topic/CAnimationController::OnHasPriorityConclude.md)|由架構呼叫以解決排程衝突。|  
|[CAnimationController::OnHasPriorityTrim](../Topic/CAnimationController::OnHasPriorityTrim.md)|由架構呼叫以解決排程衝突。|  
|[CAnimationController::OnStoryboardStatusChanged](../Topic/CAnimationController::OnStoryboardStatusChanged.md)|在腳本狀態已變更時，由架構呼叫。|  
|[CAnimationController::OnStoryboardUpdated](../Topic/CAnimationController::OnStoryboardUpdated.md)|在腳本已更新時，由架構呼叫。|  
|[CAnimationController::RemoveAllAnimationGroups](../Topic/CAnimationController::RemoveAllAnimationGroups.md)|從動畫控制器移除所有動畫群組。|  
|[CAnimationController::RemoveAnimationGroup](../Topic/CAnimationController::RemoveAnimationGroup.md)|從動畫控制器移除具有指定之識別碼的動畫群組。|  
|[CAnimationController::RemoveAnimationObject](../Topic/CAnimationController::RemoveAnimationObject.md)|從動畫控制器移除動畫物件。|  
|[CAnimationController::RemoveTransitions](../Topic/CAnimationController::RemoveTransitions.md)|從屬於指定之群組的動畫物件中移除轉換。|  
|[CAnimationController::ScheduleGroup](../Topic/CAnimationController::ScheduleGroup.md)|排程動畫。|  
|[CAnimationController::SetRelatedWnd](../Topic/CAnimationController::SetRelatedWnd.md)|建立動畫控制器和視窗之間的關聯性。|  
|[CAnimationController::UpdateAnimationManager](../Topic/CAnimationController::UpdateAnimationManager.md)|指示動畫管理員要更新所有動畫變數的值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|多載。  清除群組的協助程式。|  
|[CAnimationController::OnAfterSchedule](../Topic/CAnimationController::OnAfterSchedule.md)|在剛好排定指定之群組的動畫後，由架構呼叫。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationController::g\_KeyframeStoryboardStart](../Topic/CAnimationController::g_KeyframeStoryboardStart.md)|主要畫面格，表示腳本的開始。|  
|[CAnimationController::m\_bIsValid](../Topic/CAnimationController::m_bIsValid.md)|指定動畫控制器是否有效。  如果目前的作業系統不支援 Windows 動畫 API，此成員會設定為 FALSE。|  
|[CAnimationController::m\_lstAnimationGroups](../Topic/CAnimationController::m_lstAnimationGroups.md)|屬於此動畫控制器之動畫群組的清單。|  
|[CAnimationController::m\_pAnimationManager](../Topic/CAnimationController::m_pAnimationManager.md)|儲存動畫管理員 COM 物件的指標。|  
|[CAnimationController::m\_pAnimationTimer](../Topic/CAnimationController::m_pAnimationTimer.md)|儲存動畫計時器 COM 物件的指標。|  
|[CAnimationController::m\_pRelatedWnd](../Topic/CAnimationController::m_pRelatedWnd.md)|相關 CWnd 物件的指標，這個物件可以在動畫管理員狀態已經變更或更新後續事件發生時自動重繪。  可以是 NULL。|  
|[CAnimationController::m\_pTransitionFactory](../Topic/CAnimationController::m_pTransitionFactory.md)|儲存轉換 Factory COM 物件的指標。|  
|[CAnimationController::m\_pTransitionLibrary](../Topic/CAnimationController::m_pTransitionLibrary.md)|儲存轉換程式庫 COM 物件的指標。|  
  
## 備註  
 CAnimationController 類別是管理動畫的重要類別。  您可以在應用程式中建立一個或多個動畫控制器執行個體，並選擇性地使用 CAnimationController::SetRelatedWnd，將動畫控制器的執行個體連接至 CWnd 物件。  必須有這個連線，才會在動畫管理員狀態已變更或動畫計時器已更新時，自動將 WM\_PAINT 訊息傳送給相關的視窗。  如果您未啟用此關聯，您必須手動重繪顯示動畫的視窗。  為此目的，您可以從 CAnimationController 衍生類別並覆寫 OnAnimationManagerStatusChanged 和 \(或\) OnAnimationTimerPostUpdate，然後在必要時使一個或多個視窗失效重繪。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationController](../../mfc/reference/canimationcontroller-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)