---
title: "多頁文件 | Microsoft Docs"
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
  - "CPrintInfo 結構, 多頁文件"
  - "文件頁面和印表機頁面比較"
  - "文件, 分頁"
  - "文件, 列印"
  - "DoPreparePrinting 方法和分頁"
  - "多頁文件"
  - "OnBeginPrinting 方法"
  - "OnDraw 方法, 列印"
  - "OnEndPrinting 方法"
  - "OnPrepareDC 方法"
  - "OnPreparePrinting 方法"
  - "OnPrint 方法"
  - "覆寫, 列印的檢視類別函式"
  - "頁面, 列印"
  - "分頁"
  - "分頁, 列印多頁文件"
  - "印表機模式"
  - "印表機, 印表機模式"
  - "列印 [MFC], 多頁文件"
  - "列印 [MFC], 分頁"
  - "列印 [MFC], 通訊協定"
  - "協定, 列印通訊協定"
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多頁文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明列印通訊協定的視窗並說明如何列印包含多個頁面的文件。  本文包括下列主題：  
  
-   [列印通訊協定](#_core_the_printing_protocol)  
  
-   [覆寫檢視類別函式](#_core_overriding_view_class_functions)  
  
-   [分頁](#_core_pagination)  
  
-   [印表機頁面和文件頁面比較](#_core_printer_pages_vs.._document_pages)  
  
-   [列印時間分頁](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> 列印通訊協定  
 以下列方式列印在多頁文件、互動式架構和檢視。  首先架構顯示 **Print** 對話方塊，建立印表機的裝置內容，然後呼叫 [CDC](../mfc/reference/cdc-class.md) 物件的 [StartDoc](../Topic/CDC::StartDoc.md) 成員函式。  然後，文件的頁面，架構呼叫 `CDC` 物件的 [StartPage](../Topic/CDC::StartPage.md) 成員函式，指示檢視物件來列印頁面，然後呼叫 [EndPage](../Topic/CDC::EndPage.md) 成員函式。  如果必須在啟動特定頁面之前變更印表機方式，檢視呼叫 [ResetDC](../Topic/CDC::ResetDC.md)，以包含新的印表機方式資訊的 [轉換](http://msdn.microsoft.com/library/windows/desktop/dd183565) 結構。  在整個文件列印時，架構會呼叫 [EndDoc](../Topic/CDC::EndDoc.md) 成員函式。  
  
##  <a name="_core_overriding_view_class_functions"></a> 覆寫檢視類別函式  
 [CView](../mfc/reference/cview-class.md) 類別會定義數個成員函式，該函釋在列印期間由架構呼叫。  藉由覆寫您的檢視類別的這些功能，您必須提供架構的列印邏輯和檢視類別的列印邏輯之間建立連接。  下表列出這些成員函式。  
  
### 列印的 CView 的可覆寫函式  
  
|Name|覆寫的原因|  
|----------|-----------|  
|[OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|插入值在列印對話方塊，特別是文件的長度|  
|[OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|配置字型或其他 GDI 資源|  
|[OnPrepareDC](../Topic/CView::OnPrepareDC.md)|為指定的頁面上調整裝置內容的屬性，或做列印時分頁|  
|[OnPrint](../Topic/CView::OnPrint.md)|列印特定頁面|  
|[OnEndPrinting](../Topic/CView::OnEndPrinting.md)|解除配置 GDI 資源|  
  
 您可以列印相關處理其他功能，不過，這些函式是巡覽列印處理序的章節。  
  
 下圖說明在列印處理序所需的步驟並顯示列印成員函式的每個 `CView` 位置呼叫。  其餘本文詳細說明大部分步驟。  列印程序的其他部分在文件 [配置 GDI 資源](../mfc/allocating-gdi-resources.md)中說明。  
  
 ![列印迴圈處理序](../mfc/media/vc37c71.png "vc37C71")  
列印迴圈  
  
##  <a name="_core_pagination"></a> 分頁  
 架構在 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 結構儲存許多關於列印工作的資訊。  列舉 `CPrintInfo` 中的值給分頁；這些值可如下表所示。  
  
### 在 CPrintInfo 儲存頁碼資訊。  
  
|成員變數或<br /><br /> 函式名稱|參考的頁碼。|  
|--------------------|------------|  
|`GetMinPage`\/`SetMinPage`|文件第一頁|  
|`GetMaxPage`\/`SetMaxPage`|文件的最後一頁|  
|`GetFromPage`|要列印的第一頁|  
|`GetToPage`|要列印的最後一頁|  
|`m_nCurPage`|目前列印頁面|  
  
 頁碼從 1 開始，第一頁為 1，而不是 0。  如需 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 的這些或其他成員的更多資訊，請參閱 *MFC 參考*。  
  
 在列印處理序開始時，架構會呼叫檢視的 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 成員函式，將指標傳遞給 `CPrintInfo` 結構。  應用程式精靈提供呼叫 [DoPreparePrinting](../Topic/CView::DoPreparePrinting.md)`OnPreparePrinting` 的實作， `CView`的其他 10% 成員函式。  `DoPreparePrinting` 是顯示列印對話方塊並建立印表機內容的函式。  
  
 此時應用程式不知道文件有多少頁。  它使用預設值 1 和 0xFFFF 為文件的第一頁及最後一頁。  如果您知道文件有多少頁，覆寫 `OnPreparePrinting` 和呼叫 [SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md) `CPrintInfo` 結構中，在將其傳送至 `DoPreparePrinting`之前。  這可讓您指定您的文件長度。  
  
 `DoPreparePrinting`顯示列印的對話方塊。  當它傳回時， `CPrintInfo` 結構包含使用者指定的值。  如果使用者想要列印頁面中只有一個選取範圍，則在列印對話方塊可以指定開始和結束頁碼。  架構使用 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)的 `GetFromPage` 和 `GetToPage` 函式擷取這些值。  如果使用者未指定區域設定，架構會呼叫 `GetMinPage` 和 `GetMaxPage` 並使用傳回的值列印整份文件。  
  
 對於要列印的文件的所有頁面，架構會呼叫您的檢視類別的兩個成員函式，[OnPrepareDC](../Topic/CView::OnPrepareDC.md) 和 [OnPrint](../Topic/CView::OnPrint.md)，並每個函式傳遞兩個參數：對 [CDC](../mfc/reference/cdc-class.md) 物件的指標、對 `CPrintInfo` 結構的指標。  每次架構呼叫 `OnPrepareDC` 和 `OnPrint`，則傳不同的值給 `CPrintInfo` 結構的 `m_nCurPage` 成員。  這種方法中，架構指示檢視要列印的頁面。  
  
 [OnPrepareDC](../Topic/CView::OnPrepareDC.md) 成員函式也為螢幕顯示使用。  在繪製之前，它會調整裝置內容。  `OnPrepareDC` 以類似列印的服務，不過，有兩個差異：首先， `CDC` 物件代表印表機內容而非螢幕裝置內容，其次， `CPrintInfo` 物件會傳遞做為第二個參數。\(當 `OnPrepareDC` 為螢幕顯示呼叫時，這個參數是 **NULL**\)。覆寫 `OnPrepareDC` 視列印頁面調整裝置內容。  例如，您可以捲動檢視區原點和裁剪區域確定文件的適當部分印出。  
  
 [OnPrint](../Topic/CView::OnPrint.md) 成員函式執行頁面上的實際列印。  這篇文章 [如何完成預設印表機](../mfc/how-default-printing-is-done.md) 顯示架構如何呼叫 [OnDraw](../Topic/CView::OnDraw.md) 搭配印表機內容執行列印。  更明確地說，與 `CPrintInfo` 結構和裝置內容的框架呼叫 `OnPrint` 和 `OnPrint` 傳遞 `OnDraw`的裝置內容。  覆寫 `OnPrint` 執行應該完成在列印期間和不為螢幕顯示的所有轉換。  例如，列印頁首或頁尾 \(請參閱本文件中的 [頁首和頁尾](../mfc/headers-and-footers.md) \)。  然後從 `OnPrint` 的覆寫呼叫 `OnDraw` 來轉換共用到螢幕顯示和列印。  
  
 這個事實 `OnDraw` 做螢幕顯示和列印的轉換表示您的應用程式是 WYSIWYG：「所見即所得 \(WYSIWYG\)」。不過，假設您不要撰寫 WYSIWYG 應用程式。  例如，請考慮使用以粗體字型來列印但是顯示控制代碼以表示螢幕的粗體文字的文字編輯器。  在這種情況下，您螢幕顯示僅使用 `OnDraw` 。  當您覆寫 `OnPrint`時，將對 `OnDraw` 的呼叫替代成對不同繪圖函釋的呼叫。  函式以在頁面上顯示的方式繪製文件，使用您不顯示在螢幕上的屬性。  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> 印表機頁面和文件頁面比較  
 當您參考頁碼時，區別頁面的印表機概念和頁面的文件概念有時候是必要的。  從印表機來說，網頁是一張紙。  不過，一張紙不一定等於文件的頁面。  例如，如果您列印時事通訊，為摺疊的工作表，一張紙可能包含文件的第一個和最後一頁。  同樣地，如果您列印報表，文件根本不包含頁面。  相反地，一張紙可能包含列 1 到列 20，行 6 至行 10。  
  
 在 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 結構中的所有頁碼參考印表機頁面。  架構對通過印表機的每張紙張一次呼叫 `OnPrepareDC` 和 `OnPrint` 。  當您覆寫 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 函式指定文件的長度時，您必須使用印表機頁面。  如果有一對一對應關係 \(也就是印表機網頁等資料頁\)，則這是容易的。  另一方面，如果文件頁面和印表機頁面不直接對應，您必須轉譯這兩者。  例如，請考慮列印報表。  當覆寫 `OnPreparePrinting`時，您必須計算需要多少個紙張列印整份報表，並在呼叫 `CPrintInfo`的 `SetMaxPage` 成員函式時使用該值。  同樣地，覆寫 `OnPrepareDC` 時，您必須轉譯 `m_nCurPage` 到會顯示在特定工作表的行列範圍，然後調整檢視區原始來源。  
  
##  <a name="_core_print.2d.time_pagination"></a> 列印時間分頁  
 在某些狀況下，您的檢視類別直到實際列印前無法事先知道文件有多長。  例如，假設您的應用程式不是 WYSIWYG，則在螢幕上文件的長度在列印時不會對應其長度。  
  
 這會在您為檢視類別覆寫 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 時造成問題：您無法傳遞一個值到 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 架構的`SetMaxPage` 函式，因為您並不知道文件的長度。  如果使用者未指定頁碼停止在使用列印對話方塊，架構不知道何時停止列印迴圈。  唯一判斷何時停止列印迴圈的方式是印出文件然後看它何時結束。  檢視類別必須在列印時檢查文件結尾，在這結束端到達時告知架構。  
  
 這個框架視您檢視類別的 [OnPrepareDC](../Topic/CView::OnPrepareDC.md) 函式來辨識何時停止。  在對 `OnPrepareDC` 的每個呼叫之後，架構會檢查稱為 `m_bContinuePrinting` 的 `CPrintInfo` 結構的成員。  預設值為 **TRUE.**只要保持，架構會繼續列印迴圈。  如果設為 **FALSE**，架構會停止。  執行階段列印分頁、覆寫 `OnPrepareDC` 檢查文件結尾是否已到達，並將 `m_bContinuePrinting` \(如果有\)設定為 **FALSE** 。  
  
 如果目前頁面是大於 1.， `OnPrepareDC` 的預設實作會將 `m_bContinuePrinting` 設定為 **FALSE** 。  這表示，如果文件的長度未指定，架構會假設文件長度為一頁。  一個結果是您必須小心，如果呼叫 `OnPrepareDC`的基底類別版本。  在呼叫基底類別版本之後，不要假設 `m_bContinuePrinting` 將會是 **TRUE**。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [頁首和頁尾](../mfc/headers-and-footers.md)  
  
-   [配置 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
## 請參閱  
 [列印](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC 類別](../mfc/reference/cdc-class.md)