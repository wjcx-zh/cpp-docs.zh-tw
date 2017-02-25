---
title: "CPaintDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaintDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaintDC class"
  - "OnPaint handler"
  - "WM_PAINT message"
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CPaintDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 [CDC](../../mfc/reference/cdc-class.md)所取得的裝置內容類別。  
  
## 語法  
  
```  
class CPaintDC : public CDC  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPaintDC::CPaintDC](../Topic/CPaintDC::CPaintDC.md)|建構 `CPaintDC` 連接到指定的 [CWnd](../../mfc/reference/cwnd-class.md)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)|包含用來繪製的 [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) 工作區。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPaintDC::m\_hWnd](../Topic/CPaintDC::m_hWnd.md)|這 `CPaintDC` 物件附加的 `HWND` 。|  
  
## 備註  
 它會 [CWnd::BeginPaint](../Topic/CWnd::BeginPaint.md) 在建構階段和 [CWnd::EndPaint](../Topic/CWnd::EndPaint.md) 在終結時間。  
  
 在回應 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 訊息，通常 `CPaintDC` 物件在您的 `OnPaint` 訊息處理常式成員函式時，才可以使用。  
  
 如需使用 `CPaintDC`的資訊，請參閱 [裝置內容。](../../mfc/device-contexts.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)