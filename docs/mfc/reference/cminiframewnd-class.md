---
title: "CMiniFrameWnd Class | Microsoft Docs"
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
  - "CMiniFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMiniFrameWnd class"
  - "mini-frame windows"
  - "工具列 [C++]"
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMiniFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示工具列浮動。周圍通常會看見半高度框架視窗。  
  
## 語法  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMiniFrameWnd::CMiniFrameWnd](../Topic/CMiniFrameWnd::CMiniFrameWnd.md)|建構 `CMiniFrameWnd` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMiniFrameWnd::Create](../Topic/CMiniFrameWnd::Create.md)|在建構完成後建立 `CMiniFrameWnd` 物件。|  
|[CMiniFrameWnd::CreateEx](../Topic/CMiniFrameWnd::CreateEx.md)|在建構完成後建立 `CMiniFrameWnd` 物件 \(以及其他選項\)。|  
  
## 備註  
 這些小型框架視窗的行為如同一般框架視窗，不過，它們沒有最小化和最大化按鈕或功能表和您必須只在關閉其系統功能表的按一下。  
  
 若要使用 `CMiniFrameWnd` 物件，請先定義物件。  然後呼叫 [建立](../Topic/CMiniFrameWnd::Create.md) 成員函式顯示小型框架視窗。  
  
 如需如何使用 `CMiniFrameWnd` 物件的詳細資訊，請參閱本文 [固定或浮動工具列](../../mfc/docking-and-floating-toolbars.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)