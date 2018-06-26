---
title: 多頁文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7362e7b9ccb15d338c09da337a6af5077a9789
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929870"
---
# <a name="multipage-documents"></a>多頁文件
本文描述 Windows 列印通訊協定並說明如何列印包含多個頁面的文件。 本文包括下列主題：  
  
-   [列印通訊協定](#_core_the_printing_protocol)  
  
-   [覆寫檢視類別函式](#_core_overriding_view_class_functions)  
  
-   [分頁](#_core_pagination)  
  
-   [文件頁面和印表機頁面](#_core_printer_pages_vs.._document_pages)  
  
-   [列印時分頁](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> 列印通訊協定  
 列印多頁文件時，架構會以下列方式與檢視互動。 架構會先顯示**列印**對話方塊中，建立裝置內容的印表機，然後呼叫[Cdc](../mfc/reference/cdc-class.md#startdoc)成員函式[CDC](../mfc/reference/cdc-class.md)物件。 然後，在文件的每一頁，架構會呼叫[StartPage](../mfc/reference/cdc-class.md#startpage)成員函式`CDC`物件，會指示要列印的頁面上和呼叫的檢視物件[EndPage](../mfc/reference/cdc-class.md#endpage)成員函式。 如果必須變更印表機模式啟動的特定頁面之前，檢視便會呼叫[ResetDC](../mfc/reference/cdc-class.md#resetdc)，哪些更新[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)結構，其中包含新的印表機模式資訊。 當列印整份文件架構會呼叫[EndDoc](../mfc/reference/cdc-class.md#enddoc)成員函式。  
  
##  <a name="_core_overriding_view_class_functions"></a> 覆寫檢視類別函式  
 [CView](../mfc/reference/cview-class.md)類別會定義幾個成員函式會在列印期間由架構呼叫。 藉由在檢視類別中覆寫這些函式，您可以提供架構的列印邏輯和檢視類別的列印邏輯之間的連接。 下表列出這些成員函式。  
  
### <a name="cviews-overridable-functions-for-printing"></a>列印的 CView 可覆寫函式  
  
|名稱|覆寫的原因|  
|----------|---------------------------|  
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|在 [列印] 對話方塊中插入值，特別是文件的長度|  
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|配置字型或其他 GDI 資源|  
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|為指定的頁面調整裝置內容的屬性，或在列印時分頁|  
|[OnPrint](../mfc/reference/cview-class.md#onprint)|列印指定頁面|  
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|解除配置 GDI 資源|  
  
 您也可以在其他函式中執行列印相關的處理，不過，這些函式可用來驅動列印處理序。  
  
 下圖說明列印處理序中包含的步驟，並顯示所呼叫的每個 `CView` 列印成員函式。 本文的其餘部分將詳細說明大部分的步驟。 列印程序的其他組件所述的發行項[配置 GDI 資源](../mfc/allocating-gdi-resources.md)。  
  
 ![列印迴圈處理序](../mfc/media/vc37c71.gif "vc37c71")  
列印迴圈  
  
##  <a name="_core_pagination"></a> 分頁  
 架構會儲存在列印工作的相關資訊的許多[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構。 `CPrintInfo` 中有多個值與分頁有關，這些值的存取方式如下表所示。  
  
### <a name="page-number-information-stored-in-cprintinfo"></a>在 CPrintInfo 中儲存頁碼資訊。  
  
|成員變數或<br /><br /> 函式名稱|參考的頁碼|  
|-----------------------------------------------|----------------------------|  
|`GetMinPage`/`SetMinPage`|文件的第一頁|  
|`GetMaxPage`/`SetMaxPage`|文件的最後一頁|  
|`GetFromPage`|要列印的第一頁|  
|`GetToPage`|要列印的最後一頁|  
|`m_nCurPage`|目前列印的頁面|  
  
 頁碼從 1 開始，第一頁為 1，而不是 0。 如需有關這些和其他成員[CPrintInfo](../mfc/reference/cprintinfo-structure.md)，請參閱*MFC 參考*。  
  
 在開始列印程序時，架構會呼叫檢視[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)成員函式，傳遞指標`CPrintInfo`結構。 應用程式精靈提供的實作`OnPreparePrinting`呼叫[DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting)，另一個成員函式的`CView`。 `DoPreparePrinting` 是一個顯示 [列印] 對話方塊並建立印表機內容的函式。  
  
 此時應用程式不知道文件有多少頁。 它會使用預設值 1 和 0xFFFF 做為文件的第一頁及最後一頁。 如果您知道您的文件中有多少頁面時，覆寫`OnPreparePrinting`呼叫 [如 SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage)`CPrintInfo`結構在傳送前`DoPreparePrinting`。 這可讓您指定文件的長度。  
  
 `DoPreparePrinting` 接著會顯示 [列印] 對話方塊。 當它傳回時，`CPrintInfo` 結構會包含使用者指定的值。 如果使用者只想要列印某個選取範圍的頁面，則可以在 [列印] 對話方塊中指定開始和結束頁碼。 架構會擷取使用這些值`GetFromPage`和`GetToPage`函式的[CPrintInfo](../mfc/reference/cprintinfo-structure.md)。 如果使用者未指定列印範圍，架構會呼叫 `GetMinPage` 和 `GetMaxPage`，並使用傳回的值列印整份文件。  
  
 為要列印的文件的每一頁，架構會呼叫兩個成員函式在檢視類別中， [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)和[OnPrint](../mfc/reference/cview-class.md#onprint)，並將每個函式傳遞兩個參數： 指標[CDC](../mfc/reference/cdc-class.md)物件以及一個指向`CPrintInfo`結構。 每次架構呼叫`OnPrepareDC`和`OnPrint`，它會傳遞不同的值*m_nCurPage*隸屬`CPrintInfo`結構。 在這種方式下，架構會指示檢視所要列印的頁面。  
  
 [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)成員函式也用於螢幕顯示。 在繪製之前，它會調整裝置內容。 `OnPrepareDC` 的功能與列印類似，不過其中有兩個差異：首先，`CDC` 物件代表印表機內容而非螢幕裝置內容，其次，`CPrintInfo` 物件會做為第二個參數傳遞 (這個參數是**NULL**時`OnPrepareDC`稱為進行螢幕顯示。)覆寫 `OnPrepareDC` 視列印頁面調整裝置內容。 例如，您可以捲動檢視區原點和裁剪區域確定將會印出文件的適當部分。  
  
 [OnPrint](../mfc/reference/cview-class.md#onprint)成員函式會執行實際列印的頁面。 發行項[如何完成預設列印](../mfc/how-default-printing-is-done.md)顯示架構如何呼叫[OnDraw](../mfc/reference/cview-class.md#ondraw)與印表機裝置內容執行列印。 更明確地說，架構會以 `OnPrint` 結構和裝置內容呼叫 `CPrintInfo`，而 `OnPrint` 會傳遞裝置內容至 `OnDraw`。 覆寫 `OnPrint` 以執行應該只有在列印期間完成且不進行螢幕顯示的所有轉譯。 例如，若要列印頁首或頁尾 (請參閱文章[頁首和頁尾](../mfc/headers-and-footers.md)如需詳細資訊)。 接著再從 `OnDraw` 的覆寫呼叫 `OnPrint` 來轉譯螢幕顯示和列印的常用部分。  
  
 事實上，`OnDraw` 為螢幕顯示和列印進行轉譯表示您的應用程式是 WYSIWYG：「所見即所得 (WYSIWYG)」。 不過，假設您撰寫的不是 WYSIWYG 應用程式。 例如，考慮一個使用以粗體字型來列印，但是在螢幕上顯示表示粗體文字之控制碼的文字編輯器。 在這種情況下，您只會使用 `OnDraw` 進行螢幕顯示。 當您覆寫 `OnPrint` 時，會使用不同繪圖函式的呼叫取代 `OnDraw` 的呼叫。 該函式會使用您未顯示在螢幕上的屬性，以在紙張上顯示的方式繪製文件。  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> 印表機頁面 vs。文件頁面  
 當您參考頁碼時，區別頁面的印表機概念與頁面的文件概念有時候是必要的。 從印表機檢視的角度來說，一個頁面就是一張紙。 不過，一張紙不一定等於文件的一個頁面。 例如，如果您列印的是會摺疊紙張的報紙，則一張紙可能同時包含文件的第一頁和最後一頁。 同樣地，如果您列印的是試算表，則文件根本不是由頁面所組成。 相反地，一張紙可能包含第 1 列到第 20 列，第 6 行至第 10 行。  
  
 所有頁碼中[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構參考印表機頁面。 架構會在每張紙張通過印表機時呼叫 `OnPrepareDC` 和 `OnPrint`。 當您覆寫[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)函式指定文件長度，您必須使用印表機頁面。 如果其中具有一對一的對應關係 (也就是印表機頁面等於文件頁面)，則這是容易的。 另一方面，如果文件頁面和印表機頁面無法直接對應，您必須在兩者之間進行轉譯。 例如，請考慮列印試算表的情形。 當覆寫 `OnPreparePrinting` 時，您必須計算列印整份試算表需要多少紙張，並在呼叫 `SetMaxPage` 的 `CPrintInfo` 成員函式時使用該值。 同樣地，當覆寫`OnPrepareDC`，則必須將轉譯*m_nCurPage*插入資料列和資料行，將會出現在特定工作表上，然後據以調整檢視區原點的範圍。  
  
##  <a name="_core_print.2d.time_pagination"></a> 列印時分頁  
 在某些狀況下，您的檢視類別在實際列印前無法事先知道文件的長度。 例如，假設您的應用程式不是 WYSIWYG，則螢幕上文件的長度與列印時的長度無法對應。  
  
 這會造成問題，當您覆寫[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)檢視類別： 您無法將值傳遞`SetMaxPage`函式的[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構，因為您不知道的長度文件。 如果使用者在使用 [列印] 對話方塊未指定停止的頁碼，架構就不知道應於何時停止列印迴圈。 唯一判斷何時停止列印迴圈的方式是印出文件然後看它何時結束。 您的檢視類別必須在列印時檢查文件的結尾，然後在到達尾端時告知架構。  
  
 架構仰賴檢視類別的[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)函式來得知其何時停止。 若要每次呼叫之後`OnPrepareDC`，架構會檢查的成員`CPrintInfo`結構稱為*m_bContinuePrinting*。 預設值是 **，則為 TRUE。** 只要該值保持不變，架構就會繼續進行列印迴圈。 如果設定為**FALSE**，架構會停止。 若要執行列印時分頁，覆寫`OnPrepareDC`檢查文件結尾是否已達到，而且設定*m_bContinuePrinting*至**FALSE**時有。  
  
 預設實作`OnPrepareDC`設定*m_bContinuePrinting*至**FALSE**如果目前頁面大於 1。 這表示，如果未指定文件的長度，架構會假設文件的長度為一頁。 這樣一來，您必須在呼叫 `OnPrepareDC` 的基底類別版本時特別小心。 不要假設*m_bContinuePrinting*將**TRUE**之後呼叫基底類別版本。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [頁首和頁尾](../mfc/headers-and-footers.md)  
  
-   [配置 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>另請參閱  
 [列印](../mfc/printing.md)   
 [CView 類別](../mfc/reference/cview-class.md)   
 [CDC 類別](../mfc/reference/cdc-class.md)