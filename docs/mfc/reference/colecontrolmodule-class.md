---
title: "COleControlModule Class | Microsoft Docs"
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
  - "COleControlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlModule class"
  - "control modules"
  - "MFC ActiveX controls, OLE control modules"
  - "OLE control modules"
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您從衍生出 OLE 控制項控制項模組物件的基底類別。  
  
## 語法  
  
```  
class COleControlModule : public CWinApp  
```  
  
## 備註  
 這個類別會使用自己的控制項模組提供成員函式。  使用 Microsoft Foundation Class 的每一個 OLE 控制項控制項模組只能包含 `COleControlModule`從衍生的物件。  其他 C\+\+ 全域建構物件時，這個物件會建構。  宣告您的衍生 `COleControlModule` 物件在全域層級。  
  
 如需使用 `COleControlModule` 類別的詳細資訊，請參閱 [CWinApp](../../mfc/reference/cwinapp-class.md) 類別和本文 [ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [MFC TESTHELP 範例](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)