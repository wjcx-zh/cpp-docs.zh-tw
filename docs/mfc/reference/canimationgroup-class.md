---
title: "CAnimationGroup 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationGroup"
  - "CAnimationGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationGroup 類別"
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationGroup 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作動畫群組，結合動畫腳本、動畫物件和轉換以定義動畫。  
  
## 語法  
  
```  
class CAnimationGroup;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationGroup::CAnimationGroup](../Topic/CAnimationGroup::CAnimationGroup.md)|建構動畫群組。|  
|[CAnimationGroup::~CAnimationGroup](../Topic/CAnimationGroup::~CAnimationGroup.md)|解構函式。  當正在終結動畫群組時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationGroup::Animate](../Topic/CAnimationGroup::Animate.md)|將群組顯示為動畫。|  
|[CAnimationGroup::ApplyTransitions](../Topic/CAnimationGroup::ApplyTransitions.md)|將轉換套用至動畫物件。|  
|[CAnimationGroup::FindAnimationObject](../Topic/CAnimationGroup::FindAnimationObject.md)|尋找包含指定之動畫變數的動畫物件。|  
|[CAnimationGroup::GetGroupID](../Topic/CAnimationGroup::GetGroupID.md)|傳回 GroupID。|  
|[CAnimationGroup::RemoveKeyframes](../Topic/CAnimationGroup::RemoveKeyframes.md)|移除並選擇性終結屬於動畫群組的所有主要畫面格。|  
|[CAnimationGroup::RemoveTransitions](../Topic/CAnimationGroup::RemoveTransitions.md)|從屬於動畫群組的動畫物件中移除轉換。|  
|[CAnimationGroup::Schedule](../Topic/CAnimationGroup::Schedule.md)|將動畫排程在指定的時間。|  
|[CAnimationGroup::SetAutodestroyTransitions](../Topic/CAnimationGroup::SetAutodestroyTransitions.md)|指示屬於群組的所有動畫物件自動終結轉換。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationGroup::AddKeyframes](../Topic/CAnimationGroup::AddKeyframes.md)|加入主要畫面格的協助程式。|  
|[CAnimationGroup::AddTransitions](../Topic/CAnimationGroup::AddTransitions.md)|將轉換加入至腳本的協助程式。|  
|[CAnimationGroup::CreateTransitions](../Topic/CAnimationGroup::CreateTransitions.md)|建立 COM 轉換物件的協助程式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationGroup::m\_bAutoclearTransitions](../Topic/CAnimationGroup::m_bAutoclearTransitions.md)|指定如何將轉換從屬於群組的動畫物件中清除。  如果這個成員為 TRUE，則會在已排程動畫時自動移除轉換。  否則，您必須以手動方式移除轉換。|  
|[CAnimationGroup::m\_bAutodestroyAnimationObjects](../Topic/CAnimationGroup::m_bAutodestroyAnimationObjects.md)|指定如何終結動畫物件。  如果這個參數為 TRUE，將會在終結群組時自動終結動畫物件。  否則必須手動終結動畫物件。  預設值為 FALSE。  只有在使用 new 運算子配置屬於群組的所有動畫物件時，才要將這個值設定為 TRUE。|  
|[CAnimationGroup::m\_bAutodestroyKeyframes](../Topic/CAnimationGroup::m_bAutodestroyKeyframes.md)|指定如何終結主要畫面格。  如果這個值為 TRUE，則會移除並終結所有的主要畫面格，否則只是在清單中移除它們。  預設值為 TRUE。|  
|[CAnimationGroup::m\_lstAnimationObjects](../Topic/CAnimationGroup::m_lstAnimationObjects.md)|包含動畫物件清單。|  
|[CAnimationGroup::m\_lstKeyFrames](../Topic/CAnimationGroup::m_lstKeyFrames.md)|包含主要畫面格清單。|  
|[CAnimationGroup::m\_pStoryboard](../Topic/CAnimationGroup::m_pStoryboard.md)|指向動畫腳本。  這個指標只有在呼叫 Animate 之後才有效。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationGroup::m\_nGroupID](../Topic/CAnimationGroup::m_nGroupID.md)|動畫群組的唯一識別碼。|  
|[CAnimationGroup::m\_pParentController](../Topic/CAnimationGroup::m_pParentController.md)|這個群組所屬之動畫控制器的指標。|  
  
## 備註  
 當您使用 CAnimationController::AddAnimationObject 加入動畫物件時，動畫控制器 \(CAnimationController\) 會自動建立動畫群組。  動畫群組由 GroupID 識別，這通常用來當做參數以操作動畫群組。  GroupID 是取自加入新動畫群組的第一個動畫物件。  呼叫 CAnimationController::AnimateGroup 之後便會建立封裝的動畫腳本，您可透過公用成員 m\_pStoryboard 加以存取。  
  
## 繼承階層架構  
 [CAnimationGroup](../../mfc/reference/canimationgroup-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)