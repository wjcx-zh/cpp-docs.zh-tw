---
title: "列印 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件, 列印"
  - "列印 [MFC]"
  - "列印 [MFC], 從架構"
  - "檢視類別, 列印作業"
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Windows 實作與裝置無關的顯示。  在 MFC，這表示相同的繪製呼叫，在您的檢視類別的 `OnDraw` 成員函式，要在其中繪製負責在顯示和其他裝置，例如印表機。  如需預覽列印，目標裝置是一個模擬印表機輸出至顯示。  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> 在列印的效果 Framework 的角色  
 檢視類別具有下列責任:  
  
-   告知架構多少頁文件。  
  
-   當要求列印指定的頁面，繪製文件的部分。  
  
-   配置和解除配置為列印或其他繪圖裝置介面 \(Graphics Device \(GDI\) 資源所需的所有字型。  
  
-   如果需要，將必要的任何逸出程式碼在列印特定頁面之前，例如，變更以每頁為基礎的列印方向變更印表機方式。  
  
 框架的責任如下:  
  
-   顯示 **Print** 對話方塊。  
  
-   建立印表機的 [CDC](../mfc/reference/cdc-class.md) 物件。  
  
-   呼叫 `CDC` 物件的 [StartDoc](../Topic/CDC::StartDoc.md) 和 [EndDoc](../Topic/CDC::EndDoc.md) 成員函式。  
  
-   重複呼叫 `CDC` 物件的 [StartPage](../Topic/CDC::StartPage.md) 成員函式，通知檢視類別應該列印頁，並呼叫 `CDC` 物件的 [EndPage](../Topic/CDC::EndPage.md) 成員函式。  
  
-   呼叫在檢視中的可覆寫的函式在適當的時間。  
  
 下列文件說明架構如何支援列印和預覽列印:  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [預設印表機如何完成](../mfc/how-default-printing-is-done.md)  
  
-   [多頁文件](../mfc/multipage-documents.md)  
  
-   [頁首和頁尾](../mfc/headers-and-footers.md)  
  
-   [配置列印的 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
-   [預覽列印](../mfc/print-preview-architecture.md)  
  
## 請參閱  
 [列印和預覽列印](../mfc/printing-and-print-preview.md)