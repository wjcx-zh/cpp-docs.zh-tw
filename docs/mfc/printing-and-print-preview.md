---
title: "列印和預覽列印 | Microsoft Docs"
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
  - "預覽列印"
  - "預覽列印"
  - "列印 [C++]"
  - "列印 [C++], 預覽列印"
  - "列印 [MFC]"
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 列印和預覽列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過 MFC 類別 [CView](../mfc/reference/cview-class.md)支援列印和預覽程式的文件中。  對於基本列印和預覽列印，請覆寫您的檢視類別的 [OnDraw](../Topic/CView::OnDraw.md) 成員函式，您必須繼續進行。  該函式可以繪製到畫面上的檢視，以實際印表機的印表機內容，或是模擬在螢幕之印表機的裝置內容。  
  
 您也可以加入程式碼以處理多頁文件列印和預覽，分頁您要列印的文件並將頁首和頁尾加入它們。  
  
 本文章系列說明列印如何在 MFC 程式庫實作以及如何利用列印結構已經建立至架構。  文件也說明 MFC 如何支援預覽列印功能的最簡單的實作，以及如何使用和修改該功能。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [列印](../mfc/printing.md)  
  
-   [預覽列印結構](../mfc/print-preview-architecture.md)  
  
-   [範例](../top/visual-cpp-samples.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)