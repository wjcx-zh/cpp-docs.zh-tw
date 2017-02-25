---
title: "CBaseKeyFrame 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseKeyFrame"
  - "afxanimationcontroller/CBaseKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseKeyFrame 類別"
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CBaseKeyFrame 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作主要畫面格的基本功能。  
  
## 語法  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBaseKeyFrame::CBaseKeyFrame](../Topic/CBaseKeyFrame::CBaseKeyFrame.md)|建構主要畫面格物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md)|將主要畫面格加入至腳本。|  
|[CBaseKeyFrame::GetAnimationKeyframe](../Topic/CBaseKeyFrame::GetAnimationKeyframe.md)|傳回基礎主要畫面格值。|  
|[CBaseKeyFrame::IsAdded](../Topic/CBaseKeyFrame::IsAdded.md)|判斷主要畫面格是否已加入至腳本。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](../Topic/CBaseKeyFrame::IsKeyframeAtOffset.md)|指定應該按照位移還是在轉換後面，將主要畫面格加入至腳本。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CBaseKeyFrame::m\_bAdded](../Topic/CBaseKeyFrame::m_bAdded.md)|指定這個主要畫面格是否已加入至腳本。|  
|[CBaseKeyFrame::m\_bIsKeyframeAtOffset](../Topic/CBaseKeyFrame::m_bIsKeyframeAtOffset.md)|指定要在相對於另一個現有主要畫面格的位移處，還是在某個轉換的結尾，將這個主要畫面格加入至腳本。|  
|[CBaseKeyFrame::m\_keyframe](../Topic/CBaseKeyFrame::m_keyframe.md)|表示 Windows 動畫 API 主要畫面格。  當主要畫面格未初始化時，它會設定為預先定義的值 UI\_ANIMATION\_KEYFRAME\_STORYBOARD\_START。|  
  
## 備註  
 封裝 UI\_ANIMATION\_KEYFRAME 變數。  做為任何主要畫面格實作的基底類別。  主要畫面格代表腳本中的某個時間點，並且可用來指定轉換的開始和結束時間。  有兩種主要畫面格類型：在指定的位移 \(以時間為單位\) 加入至腳本的主要畫面格，或在指定轉換後面加入的主要畫面格。  由於有些轉換的期間無法在動畫啟動前得知，因此只能在執行階段確定某些主要畫面格的實際值。  由於主要畫面格可能相依於轉換，這些轉換又會輾轉相依於主要畫面格，因此在建置主要畫面格鏈結時防止無限遞迴是很重要的一點。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)