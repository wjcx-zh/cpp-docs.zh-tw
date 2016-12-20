---
title: "剪貼簿 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪貼簿"
  - "剪貼簿, 程式設計"
  - "複製資料"
  - "剪下和複製資料"
  - "傳輸資料"
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪貼簿
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這系列文章說明如何實作在 MFC 應用程式的 Windows 剪貼簿的支援。  Windows 剪貼簿有兩種使用方式:  
  
-   實作標準的編輯功能表命令，例如剪下，複製，然後貼上。  
  
-   實作統一資料傳輸與拖放 \(OLE\)。  
  
 剪貼簿是在來源和目的之間傳輸資料的標準 Windows 方法。  這也可以是非常適用於 OLE 作業。  隨著 OLE 的存在，Windows 有兩種剪貼簿機制。  標準 Windows 剪貼簿應用程式開發介面仍然可用，不過，它補充了 OLE 資料傳輸機制。  OLE 一致的資料傳輸 \(UDT\) 支援剪下、複製和貼上與剪貼簿和拖放。  
  
 剪貼簿是整個 Windows 工作階段共用系統服務，因此，沒有控制代碼或自己的階層架構。  您可透過 [CWnd](../mfc/reference/cwnd-class.md) 類別的成員函式管理剪貼簿。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [何時使用每個剪貼簿機制](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [使用傳統 Windows 剪貼簿應用程式開發介面](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [加入其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="1bc8aafd7da110d0b343b54cffa169d9" class\="tgtSentence"\>Windows 剪貼簿\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms648709)  
  
-   [實作拖放功能 \(OLE\)](../mfc/drag-and-drop-ole.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)