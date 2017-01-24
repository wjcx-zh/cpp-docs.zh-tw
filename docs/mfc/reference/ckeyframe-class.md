---
title: "CKeyFrame 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CKeyFrame"
  - "CKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyFrame 類別"
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CKeyFrame 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示動畫主要畫面格。  
  
## 語法  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CKeyFrame::CKeyFrame](../Topic/CKeyFrame::CKeyFrame.md)|多載。  建構相依於其他主要畫面格的主要畫面格。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CKeyFrame::AddToStoryboard](../Topic/CKeyFrame::AddToStoryboard.md)|將主要畫面格加入至腳本。  \(覆寫 [CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md)\)。|  
|[CKeyFrame::AddToStoryboardAfterTransition](../Topic/CKeyFrame::AddToStoryboardAfterTransition.md)|在轉換之後將主要畫面格加入至腳本。|  
|[CKeyFrame::AddToStoryboardAtOffset](../Topic/CKeyFrame::AddToStoryboardAtOffset.md)|在位移處將主要畫面格加入至腳本。|  
|[CKeyFrame::GetExistingKeyframe](../Topic/CKeyFrame::GetExistingKeyframe.md)|傳回這個主要畫面格相依所在之主要畫面格的指標。|  
|[CKeyFrame::GetOffset](../Topic/CKeyFrame::GetOffset.md)|傳回與其他主要畫面格的位移。|  
|[CKeyFrame::GetTransition](../Topic/CKeyFrame::GetTransition.md)|傳回這個主要畫面格相依所在之轉換的指標。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CKeyFrame::m\_offset](../Topic/CKeyFrame::m_offset.md)|指定這個主要畫面格相對於儲存在 m\_pExistingKeyFrame 之主要畫面格的位移。|  
|[CKeyFrame::m\_pExistingKeyFrame](../Topic/CKeyFrame::m_pExistingKeyFrame.md)|儲存現有主要畫面格的指標。  這個主要畫面格會加入至腳本，其與現有主要畫面格的位移為 m\_offset。|  
|[CKeyFrame::m\_pTransition](../Topic/CKeyFrame::m_pTransition.md)|儲存會在此主要畫面格開始之轉換的指標。|  
  
## 備註  
 這個類別會實作動畫主要畫面格。  主要畫面格代表腳本中的某個時間點，並且可用來指定轉換的開始和結束時間。  主要畫面格可能以其他主要畫面格為基準而具有相對於此基準的位移 \(以秒為單位\)，或者以轉換為基準而表示此轉換結束時的某個時間點。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)