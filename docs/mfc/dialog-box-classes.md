---
title: 對話方塊類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 5747e4450816b803f97ad5ff6338b9e01ad41bca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264036"
---
# <a name="dialog-box-classes"></a>對話方塊類別

類別`CDialog`和其衍生的類別封裝對話方塊中的功能。 對話方塊是一種特殊的視窗中，由於`CDialog`衍生自`CWnd`。 衍生您的對話方塊類別從`CDialog`或使用下列其中一個的通用對話方塊類別為標準的對話方塊，例如開啟或儲存檔案、 列印、 選取的字型或色彩，初始化搜尋和取代作業，或執行各種 OLE 相關作業。

[CDialog](../mfc/reference/cdialog-class.md)<br/>
所有的對話方塊，強制回應和非強制回應的基底類別。

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
提供對話方塊資料交換和驗證的資訊。

## <a name="common-dialogs"></a>通用對話方塊

這些對話方塊類別會封裝 Windows 通用對話方塊。 它們提供簡單易用的實作複雜的對話方塊。

[CCommonDialog](../mfc/reference/ccommondialog-class.md)<br/>
所有的通用對話方塊的基底類別。

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
提供標準對話方塊來開啟或儲存檔案。

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
提供標準的對話方塊中選取一種色彩。

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
提供標準的對話方塊中選取的字型。

[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)<br/>
可提供標準對話方塊搜尋並取代作業。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供標準對話方塊，來列印檔案。

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
提供 Windows 列印屬性工作表。

[CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)<br/>
封裝 Windows 通用 版面設定對話方塊中所提供額外的支援以及設定和修改列印邊界的服務。

## <a name="ole-common-dialogs"></a>OLE 通用對話方塊

OLE 會將 Windows 中的幾個通用對話方塊。 這些類別會封裝 OLE 通用對話方塊。

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
由架構用來包含所有 OLE 對話方塊的通用實作。 在使用者介面分類中的所有對話方塊類別都是衍生自這個基底類別。 `COleDialog` 無法直接使用。

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
顯示 [插入物件] 對話方塊，用於插入新的 OLE 連結的或內嵌的項目的標準使用者介面。

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
顯示 [選擇性貼上] 對話方塊，用於實作 [編輯選擇性貼上] 命令的標準使用者介面。

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
顯示 [編輯連結] 對話方塊中，用於修改連結項目的相關資訊的標準使用者介面。

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
顯示 [變更圖示] 對話方塊，用於變更與 OLE 內嵌或連結的項目關聯的圖示的標準使用者介面。

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
顯示 [轉換] 對話方塊，用於將 OLE 項目從一個類型轉換為另一個類型的標準使用者介面。

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
封裝 Windows 通用 OLE 屬性對話方塊。 [通用 OLE 屬性] 對話方塊可讓您使用與 Windows 標準一致的方式，輕鬆顯示和修改 OLE 文件項目的屬性。

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
顯示 [更新] 對話方塊，用於更新文件中的所有連結的標準使用者介面。 對話方塊包含進度指示器，以指出更新程序是如何接近完成。

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
顯示 [變更來源] 對話方塊，用於變更連結的目的地或來源的標準使用者介面。

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
顯示 [伺服器忙碌中] 和 [伺服器沒有回應] 對話方塊，用於處理呼叫忙碌的應用程式的標準使用者介面。 通常會自動顯示[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)實作。

## <a name="property-sheet-classes"></a>屬性工作表類別

屬性工作表類別可讓應用程式以使用屬性工作表，也稱為索引標籤式對話方塊。 屬性工作表是有效的方式來組織大量的單一對話方塊中的控制項。

[CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
提供的屬性工作表內的各個頁面。 自`CPropertyPage`針對每個頁面，可以加入至屬性工作表。

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
提供多個屬性頁中的框架。 衍生您的屬性工作表類別從`CPropertySheet`快速實作您的屬性工作表。

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
在類似對話方塊的圖形介面中顯示 OLE 控制項的屬性。

## <a name="html-based-dialog-classes"></a>以 HTML 為基礎的對話方塊類別

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
用來建立實作其使用者介面，與 HTML，而不是對話方塊資源的對話方塊。

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
循序顯示多個 HTML 網頁，並處理來自每個頁面的事件。

## <a name="related-classes"></a>相關的類別

這些類別不是對話方塊本身，但是他們使用對話方塊範本，並有許多的對話方塊行為。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
控制列以對話方塊範本為基礎。

[CFormView](../mfc/reference/cformview-class.md)<br/>
捲軸檢視，在對話方塊範本中定義的配置。 自`CFormView`實作根據對話方塊範本的使用者介面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供表單直接連接到資料存取物件 (DAO) 資料錄集物件的檢視。 像所有的表單檢視中，`CDaoRecordView`根據對話方塊範本。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供表單直接連接到開放式資料庫連接 (ODBC) 資料錄集物件的檢視。 像所有的表單檢視中，`CRecordView`根據對話方塊範本。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
結構，包含列印或預覽列印工作的相關資訊。 使用列印的架構[CView](../mfc/reference/cview-class.md)。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
