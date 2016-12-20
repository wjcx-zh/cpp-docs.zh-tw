---
title: "CMFCRibbonApplicationButton Class | Microsoft Docs"
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
  - "CMFCRibbonApplicationButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonApplicationButton class"
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonApplicationButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作位於應用程式視窗左上角的特殊按鈕。  當按一下  按鈕，開啟通常包含與 \[**開啟**\]、 \[**儲存**\] 和 \[**結束**\] 的一般 \[**檔案**\] 命令的功能表。  
  
## 語法  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](../Topic/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton.md)|建構和 `CMFCRibbonApplicationButton` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonApplicationButton::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CMFCRibbonApplicationButton::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCRibbonApplicationButton::SetImage](../Topic/CMFCRibbonApplicationButton::SetImage.md)|將影像指派給功能區應用程式按鈕。|  
  
## 範例  
 下列範例會在 `CMFCRibbonApplicationButton` 類別會示範如何使用各種方法。  這個範例顯示如何將影像指派給應用程式按鈕以及如何設定它的工具提示。  這個程式碼片段是 [繪製用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## 需求  
 **標題:** afxRibbonBar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)