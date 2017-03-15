---
title: "預覽列印架構 | Microsoft Docs"
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
  - "預覽列印"
  - "預覽列印, 架構"
  - "預覽列印, 修改 MFC"
  - "預覽列印, 處理序"
  - "列印 [MFC], 預覽列印"
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 預覽列印架構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 架構如何實作預覽列印功能。  涵蓋的主題包括：  
  
-   [預覽列印處理序](#_core_the_print_preview_process)  
  
-   [修改預覽列印](#_core_modifying_print_preview)  
  
 預覽列印為某些與螢幕顯示和列印不同，因為，使用螢幕，而不是直接繪製在裝置的影像，應用程式必須模擬印表機。  為了納入此， MFC 程式庫定義衍生自 [CDC 類別](../mfc/reference/cdc-class.md)的特殊 \(未記載的\) 類別，呼叫 **CPreviewDC**。  任何 `CDC` 物件包含兩個裝置內容，不過，通常會是相同的。  在 **CPreviewDC** 物件，它們會不同：第一個代表模擬的印表機，第二個代表輸出實際顯示的畫面。  
  
##  <a name="_core_the_print_preview_process"></a> \[預覽列印\] 流程。  
 當使用者選取列印預覽命令從 **檔案**功能表時，這個架構建立 **CPreviewDC** 物件。  當您的應用程式執行設定印表機內容的特性的作業，架構也會在螢幕裝置內容類似的作業。  例如，如果您的應用程式會選取字型，架構為模擬印表機字型的螢幕顯示選取字型。  當您的應用程式會將輸出傳送至印表機，架構會傳送輸出至螢幕。  
  
 每個繪製文件頁面的預覽列印和列印也不同順序相同。  在列印期間，架構會繼續列印迴圈，直到頁面的部分範圍轉譯。  在預覽列印期間，一個網頁隨時顯示，應用程式等待;進一步頁面上不會顯示，直到使用者回應。  在預覽列印期間，在泛型的螢幕顯示期間，，就讓應用程式也必須回應 `WM_PAINT` 訊息。  
  
 [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 函式呼叫，以預覽方式叫用時，就是在列印工作開始。  [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) 結構傳遞至函式包含值可以設定調整預覽列印作業的某些特性的數個成員。  例如，您可以設定 **m\_nNumPreviewPages** 成員指定是否在一個頁面或頁面模式下要預覽的文件。  
  
##  <a name="_core_modifying_print_preview"></a> 修改預覽列印  
 您可以用多種更輕鬆的方式來修改預覽列印的行為和外觀。  例如，您可以依以下：  
  
-   造成預覽列印視窗中顯示可存取的捲軸加入文件的所有頁面。  
  
-   造成預覽列印透過啟動其顯示保持在文件的使用者的位置在目前頁面。  
  
-   造成額外初始化預覽列印和列印執行。  
  
-   產生預覽列印到顯示頁碼格式中。  
  
 如果您知道文件就是並呼叫具有適當值的 `SetMaxPage` ，在列印期間，架構會使用這項資訊在預覽方式以及。  一旦架構知道文件的長度，則會在預覽模式中提供預覽視窗的捲軸，允許使用者透過文件反覆呼叫。  如果您未設定文件的長度，架構無法將捲動方塊表示目前位置，因此，架構不將捲軸。  在這個案例中，使用者必須在預覽視窗中控制列的下一頁和上一頁按鈕的文字呼叫。  
  
 如需預覽列印，您可能會發覺指派值給 `CPrintInfo`的 `m_nCurPage` 成員，因此，即使您為一般列印將不會執行。  在一般列印期間，成員傳用從架構的資訊加入至檢視類別。  這是架構如何指示檢視要列印的頁面。  
  
 相反地，在預覽列印模式啟動時， `m_nCurPage` 成員傳用以相反方向的資訊:從檢視加入至框架。  架構會使用這個成員的值判斷應該先預覽哪個頁面。  此成員的預設值為 1，因此最初顯示為文件第一頁。  在預覽列印命令叫用時，您可以覆寫 `OnPreparePrinting` 設定成員至檢視網頁的數字。  如此一來，當從顯示模式向預覽列印模式時，應用程式維護使用者的目前位置。  
  
 有時您可能 `OnPreparePrinting` 執行其他初始化取決於是否呼叫用於列印工作或預覽列印。  您可以藉由查看 `CPrintInfo` 結構的 **m\_bPreview** 成員變數判斷此。  在預覽列印叫用時，這個成員設定為 **TRUE** 。  
  
 `CPrintInfo` 結構也包含名為 **m\_strPageDesc** 的成員，其用來格式化單一頁面和多頁方式中顯示在螢幕底部的字串。  預設情況下這些字串的格式為「Page *n*」以及「Page *n* \-*m*」，但是您可以修改 **m\_strPageDesc** 於 `OnPreparePrinting` 並設定字串為更複雜的事。  如需詳細資訊，請參閱*MFC Reference*中的[CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md)。  
  
## 請參閱  
 [列印和預覽列印](../mfc/printing-and-print-preview.md)   
 [列印](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC 類別](../mfc/reference/cdc-class.md)