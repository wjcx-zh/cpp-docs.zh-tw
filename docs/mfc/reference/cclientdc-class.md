---
title: "CClientDC Class | Microsoft Docs"
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
  - "CClientDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CClientDC class"
  - "CDC 類別, device contexts for client areas"
  - "client-area device context"
  - "device contexts, 工作區"
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CClientDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

負責呼叫 Windows 函式 [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) 在建構階段和 [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) 在終結時間。  
  
## 語法  
  
```  
  
class CClientDC : public CDC  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CClientDC::CClientDC](../Topic/CClientDC::CClientDC.md)|建構連接的 `CClientDC` 物件 `CWnd`。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CClientDC::m\_hWnd](../Topic/CClientDC::m_hWnd.md)|這 `CClientDC` 是有效的 Windows 的 `HWND` 。|  
  
## 備註  
 這表示裝置內容與 `CClientDC` 物件是視窗的工作區。  
  
 如需 `CClientDC`的資訊，請參閱 [裝置內容。](../../mfc/device-contexts.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)