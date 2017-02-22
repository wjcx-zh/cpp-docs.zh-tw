---
title: "CBaseTransition 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseTransition"
  - "afxanimationcontroller/CBaseTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTransition 類別"
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CBaseTransition 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示基本轉換。  
  
## 語法  
  
```  
class CBaseTransition : public CObject;  
```  
  
## Members  
  
### 公用列舉  
  
|名稱|描述|  
|--------|--------|  
|[CBaseTransition::TRANSITION\_TYPE 列舉](../Topic/CBaseTransition::TRANSITION_TYPE%20Enumeration.md)|定義 Windows 動畫 API 的 MFC 實作目前支援的轉換類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBaseTransition::CBaseTransition](../Topic/CBaseTransition::CBaseTransition.md)|建構基底轉換物件。|  
|[CBaseTransition::~CBaseTransition](../Topic/CBaseTransition::~CBaseTransition.md)|解構函式。  當正在終結轉換物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBaseTransition::AddToStoryboard](../Topic/CBaseTransition::AddToStoryboard.md)|將轉換加入至腳本。|  
|[CBaseTransition::AddToStoryboardAtKeyframes](../Topic/CBaseTransition::AddToStoryboardAtKeyframes.md)|將轉換加入至腳本。|  
|[CBaseTransition::Clear](../Topic/CBaseTransition::Clear.md)|釋放封裝的 IUIAnimationTransition COM 物件。|  
|[CBaseTransition::Create](../Topic/CBaseTransition::Create.md)|建立 COM 轉換。|  
|[CBaseTransition::GetEndKeyframe](../Topic/CBaseTransition::GetEndKeyframe.md)|傳回開始主要畫面格。|  
|[CBaseTransition::GetRelatedVariable](../Topic/CBaseTransition::GetRelatedVariable.md)|傳回相關變數的指標。|  
|[CBaseTransition::GetStartKeyframe](../Topic/CBaseTransition::GetStartKeyframe.md)|傳回開始主要畫面格。|  
|[CBaseTransition::GetTransition](../Topic/CBaseTransition::GetTransition.md)|多載。  傳回基礎 COM 轉換物件的指標。|  
|[CBaseTransition::GetType](../Topic/CBaseTransition::GetType.md)|傳回轉換類型。|  
|[CBaseTransition::IsAdded](../Topic/CBaseTransition::IsAdded.md)|判斷轉換是否已加入至腳本。|  
|[CBaseTransition::SetKeyframes](../Topic/CBaseTransition::SetKeyframes.md)|設定轉換的主要畫面格。|  
|[CBaseTransition::SetRelatedVariable](../Topic/CBaseTransition::SetRelatedVariable.md)|建立動畫變數和轉換之間的關聯性。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CBaseTransition::m\_bAdded](../Topic/CBaseTransition::m_bAdded.md)|指定轉換是否已加入至腳本。|  
|[CBaseTransition::m\_pEndKeyframe](../Topic/CBaseTransition::m_pEndKeyframe.md)|儲存主要畫面格的指標，這個主要畫面格會指定轉換的結尾。|  
|[CBaseTransition::m\_pRelatedVariable](../Topic/CBaseTransition::m_pRelatedVariable.md)|動畫變數的指標，這個變數透過儲存在 m\_transition 中的轉換顯示動畫效果。|  
|[CBaseTransition::m\_pStartKeyframe](../Topic/CBaseTransition::m_pStartKeyframe.md)|儲存主要畫面格的指標，這個主要畫面格會指定轉換的開頭。|  
|[CBaseTransition::m\_transition](../Topic/CBaseTransition::m_transition.md)|儲存 IUIAnimationTransition 的指標。  如果尚未建立 COM 轉換物件，則為 NULL。|  
|[CBaseTransition::m\_type](../Topic/CBaseTransition::m_type.md)|儲存轉換類型。|  
  
## 備註  
 這個類別會封裝 IUIAnimationTransition 介面，並做為所有轉換的基底類別。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)