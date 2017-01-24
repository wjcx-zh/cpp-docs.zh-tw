---
title: "CMFCSpinButtonCtrl Class | Microsoft Docs"
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
  - "CMFCSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCSpinButtonCtrl class"
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCSpinButtonCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCSpinButtonCtrl` 類別支援螢幕微調按鈕控制項的視覺管理員。  
  
## 語法  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|預設建構函式。|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCSpinButtonCtrl::OnDraw](../Topic/CMFCSpinButtonCtrl::OnDraw.md)|繪製目前微調按鈕控制項。|  
  
## 備註  
 若要使用視覺管理員繪製在應用程式中使用微調按鈕控制項，以 `CMFCSpinButtonCtrl` 類別取代 `CSpinButtonCtrl` 類別的所有執行個體。  
  
## 範例  
 下列範例示範如何建立 `CMFCSpinButtonCtrl` 類別的物件並使用其 `Create` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/CPP/cmfcspinbuttonctrl-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## 需求  
 **標題:** afxspinbuttonctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)