---
title: "CMultiPageDHtmlDialog Class | Microsoft Docs"
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
  - "CMultiPageDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPageDHtmlDialog class"
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiPageDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多重網頁對話連續顯示多個 HTML 網頁和管理從每個網頁的事件。  
  
## 語法  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog.md)|建構多重網頁 \(精靈樣式\) DHTML 對話方塊物件。|  
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog.md)|終結多重網頁 DHTML 對話方塊物件。|  
  
## 備註  
 這個作業的機制是 [URL 和 DHTML 事件對應。](http://msdn.microsoft.com/zh-tw/2a7332f0-79d7-46e4-b816-0a618c46777a)，包含每個頁面的 [內嵌事件對應。](../Topic/BEGIN_EMBED_DHTML_EVENT_MAP.md) 。  
  
## 範例  
 這個多頁對話方塊會假設定義簡單的類似精靈的功能的三個 HTML 資源。  第一個頁面都有一個 `Next` 按鈕，第二個 **上一步** 和 `Next` 按鈕和三個 **上一步** 按鈕。  當其中一個按鈕，處理常式函式呼叫載入適當的新頁面 [CDHtmlDialog::LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md) 。  
  
 類別宣告的正確區段 \(在 CMyMultiPageDlg.h\):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_1.h)]  
  
 類別實作的正確區段 \(在 CMyMultipageDlg.cpp\):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## 需求  
 **Header:** afxdhtml.h  
  
## 請參閱  
 [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md)   
 [Multipage DHTML and URL Event Maps \(NIB\)](http://msdn.microsoft.com/zh-tw/2a7332f0-79d7-46e4-b816-0a618c46777a)