---
title: 多頁文件
ms.date: 11/19/2018
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
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370726"
---
# <a name="multipage-documents"></a>多頁文件

本文描述 Windows 列印通訊協定並說明如何列印包含多個頁面的文件。 本文包括下列主題：

- [列印協定](#_core_the_printing_protocol)

- [重寫檢視類別函式](#_core_overriding_view_class_functions)

- [帕吉內斯](#_core_pagination)

- [印表機頁面與文件頁面](#_core_printer_pages_vs.._document_pages)

- [列印時間分頁](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>列印協定

列印多頁文件時，架構會以下列方式與檢視互動。 首先,框架顯示 **「列印」** 對話框,為印表機創建設備上下文,並調用[CDC](../mfc/reference/cdc-class.md)物件的[StartDoc](../mfc/reference/cdc-class.md#startdoc)成員函數。 然後,對於文檔的每個頁面,框架調`CDC`用 物件的[StartPage](../mfc/reference/cdc-class.md#startpage)成員函數,指示檢視物件列印該頁,並調用[EndPage](../mfc/reference/cdc-class.md#endpage)成員函數。 如果在啟動特定頁面之前必須更改印表機模式,則視圖將調用[ResetDC](../mfc/reference/cdc-class.md#resetdc),該模式將更新包含新印表機模式資訊的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)結構。 列印整個文件後,框架將調用[EndDoc](../mfc/reference/cdc-class.md#enddoc)成員函數。

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>重寫檢視類別函式

[CView](../mfc/reference/cview-class.md)類定義多個成員函數,這些函數在列印過程中由框架調用。 藉由在檢視類別中覆寫這些函式，您可以提供架構的列印邏輯和檢視類別的列印邏輯之間的連接。 下表列出這些成員函式。

### <a name="cviews-overridable-functions-for-printing"></a>列印的 CView 可覆寫函式

|名稱|覆寫的原因|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|在 [列印] 對話方塊中插入值，特別是文件的長度|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|配置字型或其他 GDI 資源|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|為指定的頁面調整裝置內容的屬性，或在列印時分頁|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|列印指定頁面|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|解除配置 GDI 資源|

您也可以在其他函式中執行列印相關的處理，不過，這些函式可用來驅動列印處理序。

下圖說明列印處理序中包含的步驟，並顯示所呼叫的每個 `CView` 列印成員函式。 本文的其餘部分將詳細說明大部分的步驟。 列印過程的其他部分在[《分配 GDI 資源》](../mfc/allocating-gdi-resources.md)一文中進行了介紹。

![列印迴圈處理序](../mfc/media/vc37c71.gif "列印迴圈處理序") <br/>
列印迴圈

## <a name="pagination"></a><a name="_core_pagination"></a> 分頁

該框架將有關列印作業的大部分資訊存儲在[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構中。 `CPrintInfo` 中有多個值與分頁有關，這些值的存取方式如下表所示。

### <a name="page-number-information-stored-in-cprintinfo"></a>在 CPrintInfo 中儲存頁碼資訊。

|成員變數或<br /><br /> 函式名稱|參考的頁碼|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|文件的第一頁|
|`GetMaxPage`/`SetMaxPage`|文件的最後一頁|
|`GetFromPage`|要列印的第一頁|
|`GetToPage`|要列印的最後一頁|
|`m_nCurPage`|目前列印的頁面|

頁碼從 1 開始，第一頁為 1，而不是 0。 有關這些和[CPrintInfo](../mfc/reference/cprintinfo-structure.md)其他成員的詳細資訊,請參閱*MFC 參考*。

在列印過程開始時,框架調用檢視的[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)成員函數,傳遞指向結構`CPrintInfo`的指標。 應用程式精靈提供調用[DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting)`CView``OnPreparePrinting`的 實現,DoPreparePrinting 是的另一個成員函數。 `DoPreparePrinting` 是一個顯示 [列印] 對話方塊並建立印表機內容的函式。

此時應用程式不知道文件有多少頁。 它會使用預設值 1 和 0xFFFF 做為文件的第一頁及最後一頁。 如果您知道文件具有多少頁,請覆蓋`OnPreparePrinting`並呼`CPrintInfo`叫結構的 [SetMaxPage] - 斷開連結--(引用/cprintinfo-class.md_setmaxpage)的結構,然後`DoPreparePrinting`再將其發送到 。 這可讓您指定文件的長度。

`DoPreparePrinting` 接著會顯示 [列印] 對話方塊。 當它傳回時，`CPrintInfo` 結構會包含使用者指定的值。 如果使用者只想要列印某個選取範圍的頁面，則可以在 [列印] 對話方塊中指定開始和結束頁碼。 框架使用[CPrintInfo](../mfc/reference/cprintinfo-structure.md)的`GetFromPage``GetToPage`和函數檢索這些值。 如果使用者未指定列印範圍，架構會呼叫 `GetMinPage` 和 `GetMaxPage`，並使用傳回的值列印整份文件。

對於要列印的文件的每個頁面,框架調用檢視類中的兩個成員函數[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)和[OnPrint](../mfc/reference/cview-class.md#onprint),並傳遞每個函數兩個參數:指向[CDC](../mfc/reference/cdc-class.md)物件的指標`CPrintInfo`和指向結構的指標。 每次`OnPrepareDC`框架調`OnPrint`用 和 時,`CPrintInfo`它都會在結構*m_nCurPage*成員中傳遞不同的值。 在這種方式下，架構會指示檢視所要列印的頁面。

[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)成員功能也用於屏幕顯示。 在繪製之前，它會調整裝置內容。 `OnPrepareDC` 的功能與列印類似，不過其中有兩個差異：首先，`CDC` 物件代表印表機內容而非螢幕裝置內容，其次，`CPrintInfo` 物件會做為第二個參數傳遞 (當螢幕顯示`OnPrepareDC`時,此參數為**NULL。** 覆蓋`OnPrepareDC`以根據要列印的頁面對設備上下文進行調整。 例如，您可以捲動檢視區原點和裁剪區域確定將會印出文件的適當部分。

[OnPrint](../mfc/reference/cview-class.md#onprint)成員功能執行頁面的實際列印。 文章[「預設列印如何完成」](../mfc/how-default-printing-is-done.md)顯示了框架如何使用印表機裝置上下文調用[OnDraw](../mfc/reference/cview-class.md#ondraw)來執行列印。 更明確地說，架構會以 `OnPrint` 結構和裝置內容呼叫 `CPrintInfo`，而 `OnPrint` 會傳遞裝置內容至 `OnDraw`。 覆寫 `OnPrint` 以執行應該只有在列印期間完成且不進行螢幕顯示的所有轉譯。 例如,要列印頁眉或頁腳(有關詳細資訊,請參閱文章["標題"和"頁腳"。](../mfc/headers-and-footers.md) 接著再從 `OnDraw` 的覆寫呼叫 `OnPrint` 來轉譯螢幕顯示和列印的常用部分。

事實上，`OnDraw` 為螢幕顯示和列印進行轉譯表示您的應用程式是 WYSIWYG：「所見即所得 (WYSIWYG)」。 不過，假設您撰寫的不是 WYSIWYG 應用程式。 例如，考慮一個使用以粗體字型來列印，但是在螢幕上顯示表示粗體文字之控制碼的文字編輯器。 在這種情況下，您只會使用 `OnDraw` 進行螢幕顯示。 當您覆寫 `OnPrint` 時，會使用不同繪圖函式的呼叫取代 `OnDraw` 的呼叫。 該函式會使用您未顯示在螢幕上的屬性，以在紙張上顯示的方式繪製文件。

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>印表機頁與文件頁

當您參考頁碼時，區別頁面的印表機概念與頁面的文件概念有時候是必要的。 從印表機檢視的角度來說，一個頁面就是一張紙。 不過，一張紙不一定等於文件的一個頁面。 例如，如果您列印的是會摺疊紙張的報紙，則一張紙可能同時包含文件的第一頁和最後一頁。 同樣地，如果您列印的是試算表，則文件根本不是由頁面所組成。 相反地，一張紙可能包含第 1 列到第 20 列，第 6 行至第 10 行。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構中的所有頁碼都引用印表機頁面。 架構會在每張紙張通過印表機時呼叫 `OnPrepareDC` 和 `OnPrint`。 當您重寫[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)函數以指定文件的長度時,必須使用印表機頁面。 如果其中具有一對一的對應關係 (也就是印表機頁面等於文件頁面)，則這是容易的。 另一方面，如果文件頁面和印表機頁面無法直接對應，您必須在兩者之間進行轉譯。 例如，請考慮列印試算表的情形。 當覆寫 `OnPreparePrinting` 時，您必須計算列印整份試算表需要多少紙張，並在呼叫 `SetMaxPage` 的 `CPrintInfo` 成員函式時使用該值。 同樣,重寫時`OnPrepareDC`,必須將*m_nCurPage*轉換為將顯示在該特定工作表上的行和列的範圍,然後相應地調整視口原點。

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>列印時間分頁

在某些狀況下，您的檢視類別在實際列印前無法事先知道文件的長度。 例如，假設您的應用程式不是 WYSIWYG，則螢幕上文件的長度與列印時的長度無法對應。

當您重寫檢視類的[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)時,這會導致問題:由於不知道文檔的長度,因此`SetMaxPage`無法將 值傳遞給[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構的函數。 如果使用者在使用 [列印] 對話方塊未指定停止的頁碼，架構就不知道應於何時停止列印迴圈。 唯一判斷何時停止列印迴圈的方式是印出文件然後看它何時結束。 您的檢視類別必須在列印時檢查文件的結尾，然後在到達尾端時告知架構。

框架依賴於檢視類的[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)函數來告訴它何時停止。 每次調用`OnPrepareDC`後 ,框架將`CPrintInfo`檢查稱為*m_bContinuePrinting*的結構的成員。 其預設值為**TRUE。** 只要該值保持不變，架構就會繼續進行列印迴圈。 如果設置為**FALSE,** 則框架將停止。 要執行列印時間分頁,請重寫`OnPrepareDC`以檢查文檔的末尾是否已到達,並在文檔已到達時將*m_bContinuePrinting*設置為**FALSE。**

如果當前頁面大於`OnPrepareDC`1,則集的默認實現*m_bContinuePrinting* **FALSE。** 這表示，如果未指定文件的長度，架構會假設文件的長度為一頁。 這樣一來，您必須在呼叫 `OnPrepareDC` 的基底類別版本時特別小心。 不要假定*m_bContinuePrinting*在調用基類版本後為**TRUE。**

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [標題與註腳](../mfc/headers-and-footers.md)

- [配置 GDI 資源](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>另請參閱

[列印](../mfc/printing.md)<br/>
[CView 類別](../mfc/reference/cview-class.md)<br/>
[CDC 類別](../mfc/reference/cdc-class.md)
