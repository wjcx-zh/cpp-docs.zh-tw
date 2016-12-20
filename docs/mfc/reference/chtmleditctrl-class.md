---
title: "CHtmlEditCtrl Class | Microsoft Docs"
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
  - "CHtmlEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrl class"
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 WebBrowser ActiveX 控制項的功能在 MFC 視窗的。  
  
## 語法  
  
```  
class CHtmlEditCtrl: public CWnd,   
   public CHtmlEditCtrlBase< CHtmlEditCtrl >  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](../Topic/CHtmlEditCtrl::CHtmlEditCtrl.md)|建構 `CHtmlEditCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHtmlEditCtrl::Create](../Topic/CHtmlEditCtrl::Create.md)|建立 WebBrowser ActiveX 控制項並將其附加至 `CHtmlEditCtrl` 物件。  這個函式會自動將 WebBrowser ActiveX 控制項進入編輯模式。|  
|[CHtmlEditCtrl::GetDHtmlDocument](../Topic/CHtmlEditCtrl::GetDHtmlDocument.md)|擷取在內含的瀏覽器控制項正在載入之文件的 [IHTMLDocument2](https://msdn.microsoft.com/en-us/library/aa752574.aspx) 介面。|  
|[CHtmlEditCtrl::GetStartDocument](../Topic/CHtmlEditCtrl::GetStartDocument.md)|在包含的瀏覽器控制項擷取 URL 為預設檔案載入。|  
  
## 備註  
 在建立之後，由瀏覽器裝載控制項會自動在編輯模式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## 需求  
 **Header:** afxhtml.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)