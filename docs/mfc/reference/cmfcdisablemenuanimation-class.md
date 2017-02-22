---
title: "CMFCDisableMenuAnimation Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDisableMenuAnimation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDisableMenuAnimation class"
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCDisableMenuAnimation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

停用快顯功能表動畫。  
  
## 語法  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|建構 `CMFCDisableMenuAnimation` 物件。|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDisableMenuAnimation::Restore](../Topic/CMFCDisableMenuAnimation::Restore.md)|還原應用程式的架構會顯示快顯功能表的前一個動畫。|  
  
### 資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::m_animType`|儲存前一個快顯功能表動畫型別。|  
  
### 備註  
 使用這個 Helper 類別暫時停用快顯功能表動畫 \(例如，在中，在處理滑鼠或鍵盤命令時\)。  
  
 在其存留期 \(Lifetime\) 期間， `CMFCDisableMenuAnimation` 物件停用快顯功能表動畫。  建構函式將目前快顯功能表動畫輸出 `m_animType` 欄位和目前集合動畫型別為 `CMFCPopupMenu::NO_ANIMATION`。  解構函式會還原先前的動畫型別。  
  
 您可以在堆疊上的物件。 `CMFCDisableMenuAnimation` 停用在單一函式中的快顯功能表動畫。  如果您要停用在函式之間的快顯功能表動畫，請在堆積上的物件 `CMFCDisableMenuAnimation` 然後刪除，當您要還原的快顯功能表動畫時鐘。  
  
## 範例  
 下列範例顯示如何使用堆疊暫時停用功能表動畫。  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/CPP/cmfcdisablemenuanimation-class_1.h)]  
  
## 繼承階層架構  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## 需求  
 **標題:** afxpopupmenu.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)