---
title: "CWindowDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWindowDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowDC class"
  - "device contexts, 視窗"
  - "screen output classes"
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CWindowDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

衍生自 `CDC`  
  
## 語法  
  
```  
class CWindowDC : public CDC  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWindowDC::CWindowDC](../Topic/CWindowDC::CWindowDC.md)|建構 `CWindowDC` 物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWindowDC::m\_hWnd](../Topic/CWindowDC::m_hWnd.md)|`CWindowDC` 所附加的 `HWND`。|  
  
## 備註  
 在建構時期呼叫 Windows 函式 [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)，在解構時期呼叫 [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx)。  這表示 `CWindowDC` 物件存取 [CWnd](../../mfc/reference/cwnd-class.md) 的整個螢幕區域 \(工作區和非工作區\)。  
  
 如需`CWindowDC`的詳細資訊，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## 需求  
 標題: afxwin.h  
  
## 請參閱  
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)