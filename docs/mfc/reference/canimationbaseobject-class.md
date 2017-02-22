---
title: "CAnimationBaseObject 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationBaseObject"
  - "CAnimationBaseObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationBaseObject 類別"
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationBaseObject 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有動畫物件的基底類別。  
  
## 語法  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationBaseObject::CAnimationBaseObject](../Topic/CAnimationBaseObject::CAnimationBaseObject.md)|多載。  建構動畫物件。|  
|[CAnimationBaseObject::~CAnimationBaseObject](../Topic/CAnimationBaseObject::~CAnimationBaseObject.md)|解構函式。  當正在終結動畫物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationBaseObject::ApplyTransitions](../Topic/CAnimationBaseObject::ApplyTransitions.md)|透過封裝的動畫變數將轉換加入至腳本。|  
|[CAnimationBaseObject::ClearTransitions](../Topic/CAnimationBaseObject::ClearTransitions.md)|移除所有相關的轉換。|  
|[CAnimationBaseObject::ContainsVariable](../Topic/CAnimationBaseObject::ContainsVariable.md)|判斷動畫物件是否包含特定的動畫變數。|  
|[CAnimationBaseObject::CreateTransitions](../Topic/CAnimationBaseObject::CreateTransitions.md)|建立與動畫物件相關聯的轉換。|  
|[CAnimationBaseObject::DetachFromController](../Topic/CAnimationBaseObject::DetachFromController.md)|將動畫物件與父動畫控制器中斷連結。|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](../Topic/CAnimationBaseObject::EnableIntegerValueChangedEvent.md)|設定「整數值已變更」事件處理常式。|  
|[CAnimationBaseObject::EnableValueChangedEvent](../Topic/CAnimationBaseObject::EnableValueChangedEvent.md)|設定「數值已變更」事件處理常式。|  
|[CAnimationBaseObject::GetAutodestroyTransitions](../Topic/CAnimationBaseObject::GetAutodestroyTransitions.md)|判斷是否會自動終結相關的轉換。|  
|[CAnimationBaseObject::GetGroupID](../Topic/CAnimationBaseObject::GetGroupID.md)|傳回目前的群組識別碼。|  
|[CAnimationBaseObject::GetObjectID](../Topic/CAnimationBaseObject::GetObjectID.md)|傳回目前的物件識別碼。|  
|[CAnimationBaseObject::GetUserData](../Topic/CAnimationBaseObject::GetUserData.md)|傳回使用者定義資料。|  
|[CAnimationBaseObject::SetAutodestroyTransitions](../Topic/CAnimationBaseObject::SetAutodestroyTransitions.md)|設定自動命令終結轉換的旗標。|  
|[CAnimationBaseObject::SetID](../Topic/CAnimationBaseObject::SetID.md)|設定新的識別碼。|  
|[CAnimationBaseObject::SetUserData](../Topic/CAnimationBaseObject::SetUserData.md)|設定使用者定義資料。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)|收集包含的動畫變數的指標。|  
|[CAnimationBaseObject::SetParentAnimationObjects](../Topic/CAnimationBaseObject::SetParentAnimationObjects.md)|建立動畫變數 \(包含在動畫物件中\) 和其容器之間的關聯性。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationBaseObject::m\_bAutodestroyTransitions](../Topic/CAnimationBaseObject::m_bAutodestroyTransitions.md)|指定是否要自動終結相關的轉換。|  
|[CAnimationBaseObject::m\_dwUserData](../Topic/CAnimationBaseObject::m_dwUserData.md)|使用者定義資料。|  
|[CAnimationBaseObject::m\_nGroupID](../Topic/CAnimationBaseObject::m_nGroupID.md)|指定動畫物件的物件識別碼。|  
|[CAnimationBaseObject::m\_nObjectID](../Topic/CAnimationBaseObject::m_nObjectID.md)|指定動畫物件的物件識別碼。|  
|[CAnimationBaseObject::m\_pParentController](../Topic/CAnimationBaseObject::m_pParentController.md)|父動畫控制器的指標。|  
  
## 備註  
 這個類別會實作所有動畫物件的基本方法。  動畫物件可以表示應用程式中的值、點、大小、矩形或色彩，以及任何自訂實體。  動畫物件會儲存在動畫群組中 \(請參閱 CAnimationGroup\)。  每個群組可以個別顯示動畫，並視為腳本的類比。  動畫物件會根據其邏輯表示封裝一個或多個動畫變數 \(請參閱 CAnimationVariable\)。  例如，CAnimationRect 包含四個動畫變數，矩形的每一邊各使用一個變數來表示。  每個動畫物件類別都會公開多載的 AddTransition 方法，這個方法應該用來將轉換套用至封裝動畫變數。  動畫物件可由物件識別碼 \(選擇性\) 和群組識別碼識別。  必須有群組識別碼，才能將動畫物件放到正確的群組，但如果沒有指定群組識別碼，就會將物件放置在識別碼為 0 的預設群組。  如果您使用不同的 GroupID 呼叫 SetID，動畫物件將會移至其他群組 \(必要時建立新的群組\)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)