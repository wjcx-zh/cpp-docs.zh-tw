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
ms.openlocfilehash: 2399b27fc081dcc810277079729b0e62ef80d603
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616943"
---
# <a name="dialog-box-classes"></a>對話方塊類別

類別 `CDialog` 及其衍生類別會封裝對話方塊功能。 由於對話方塊是一種特殊的視窗， `CDialog` 衍生自 `CWnd` 。 從衍生您的對話方塊類別 `CDialog` ，或使用標準對話方塊的其中一個通用對話方塊類別，例如開啟或儲存檔案、列印、選取字型或色彩、起始搜尋與取代作業，或執行各種 OLE 相關作業。

[CDialog](reference/cdialog-class.md)<br/>
所有對話方塊的基類，包括強制回應和非強制回應。

[CDataExchange](reference/cdataexchange-class.md)<br/>
提供對話方塊的資料交換和驗證資訊。

## <a name="common-dialogs"></a>通用對話方塊

這些對話方塊類別會封裝 Windows 通用對話方塊。 它們提供容易使用的複雜對話方塊。

[CCommonDialog](reference/ccommondialog-class.md)<br/>
所有通用對話方塊的基類。

[CFileDialog](reference/cfiledialog-class.md)<br/>
提供開啟或儲存檔案的標準對話方塊。

[CColorDialog](reference/ccolordialog-class.md)<br/>
提供用來選取色彩的標準對話方塊。

[CFontDialog](reference/cfontdialog-class.md)<br/>
提供用來選取字型的標準對話方塊。

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
提供搜尋與取代作業的標準對話方塊。

[CPrintDialog](reference/cprintdialog-class.md)<br/>
提供用來列印檔案的標準對話方塊。

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
提供 Windows 列印屬性工作表。

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
封裝 [Windows 通用版面設定] 對話方塊所提供的服務，以及設定和修改列印邊界的額外支援。

## <a name="ole-common-dialogs"></a>OLE 通用對話方塊

OLE 會在 Windows 中加入數個通用的對話方塊。 這些類別會封裝 OLE 通用對話方塊。

[COleDialog](reference/coledialog-class.md)<br/>
由架構用來包含所有 OLE 對話方塊的通用實作。 在使用者介面分類中的所有對話方塊類別都是衍生自這個基底類別。 `COleDialog` 無法直接使用。

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
顯示 [插入物件] 對話方塊，用於插入新的 OLE 連結的或內嵌的項目的標準使用者介面。

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
顯示 [選擇性貼上] 對話方塊，用於實作 [編輯選擇性貼上] 命令的標準使用者介面。

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
顯示 [編輯連結] 對話方塊中，用於修改連結項目的相關資訊的標準使用者介面。

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
顯示 [變更圖示] 對話方塊，用於變更與 OLE 內嵌或連結的項目關聯的圖示的標準使用者介面。

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
顯示 [轉換] 對話方塊，用於將 OLE 項目從一個類型轉換為另一個類型的標準使用者介面。

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
封裝 Windows 通用 OLE 屬性對話方塊。 [通用 OLE 屬性] 對話方塊可讓您使用與 Windows 標準一致的方式，輕鬆顯示和修改 OLE 文件項目的屬性。

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
顯示 [更新] 對話方塊，用於更新文件中的所有連結的標準使用者介面。 對話方塊包含進度指示器，以指出更新程序是如何接近完成。

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
顯示 [變更來源] 對話方塊，用於變更連結的目的地或來源的標準使用者介面。

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
顯示 [伺服器忙碌中] 和 [伺服器沒有回應] 對話方塊，用於處理呼叫忙碌的應用程式的標準使用者介面。 通常會由[COleMessageFilter](reference/colemessagefilter-class.md)的執行自動顯示。

## <a name="property-sheet-classes"></a>屬性工作表類別

屬性工作表類別可讓您的應用程式使用屬性工作表，也稱為索引標籤式對話方塊。 屬性工作表是在單一對話方塊中組織大量控制項的有效方式。

[CPropertyPage](reference/cpropertypage-class.md)<br/>
提供屬性工作表中的個別頁面。 `CPropertyPage`針對要加入至屬性工作表的每個頁面，從衍生一個類別。

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
提供多個屬性頁的框架。 從衍生您的屬性工作表類別 `CPropertySheet` ，以快速執行您的屬性工作表。

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
在類似對話方塊的圖形介面中顯示 OLE 控制項的屬性。

## <a name="html-based-dialog-classes"></a>以 HTML 為基礎的對話方塊類別

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
用來建立對話方塊，以使用 HTML 而非對話方塊資源來執行其使用者介面。

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
依序顯示多個 HTML 頁面，並處理每個頁面中的事件。

## <a name="related-classes"></a>相關類別

這些類別不是每個 se 的對話方塊，但會使用對話方塊範本，而且會有許多對話方塊的行為。

[CDialogBar](reference/cdialogbar-class.md)<br/>
以對話方塊範本為基礎的控制列。

[CFormView](reference/cformview-class.md)<br/>
一個捲軸，其版面配置定義于對話方塊範本中。 從衍生類別 `CFormView` ，以根據對話方塊範本來執行使用者介面。

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
提供直接連接到資料存取物件（DAO）記錄集物件的表單檢視。 就像所有表單檢視一樣， `CDaoRecordView` 是以對話方塊範本為基礎。

[CRecordView](reference/crecordview-class.md)<br/>
提供直接連接到開放式資料庫連接（ODBC）記錄集物件的表單檢視。 就像所有表單檢視一樣， `CRecordView` 是以對話方塊範本為基礎。

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
結構，包含列印或預覽列印工作的相關資訊。 由[CView](reference/cview-class.md)的列印架構所使用。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
