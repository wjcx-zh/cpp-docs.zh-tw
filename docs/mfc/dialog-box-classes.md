---
title: "對話方塊類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.dialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用對話方塊類別"
  - "對話方塊類別"
  - "OLE 通用對話方塊類別"
  - "屬性工作表類別"
  - "索引標籤對話方塊"
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對話方塊類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將 `CDialog` 與其衍生類別封裝對話方塊功能分類。  因為對話方塊是一種特殊的視窗， `CDialog` 衍生自 `CWnd`。  從 `CDialog` 衍生您自己的對話方塊類別或為標準對話方塊使用其中一個通用對話方塊類別，例如開啟或儲存檔案，列印，選取字型或色彩，啟始搜尋和取代作業或執行各種 OLE 相關作業。  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 所有對話方塊的基底類別，強制回應和非強制回應。  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 提供資料交換和對話方塊的驗證資訊。  
  
## 通用對話方塊。  
 這些對話方塊類別封裝 Windows 通用對話方塊。  它們提供複雜的對話方塊中可使用的實作。  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 所有通用對話方塊的基底類別。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 為開啟或儲存檔案提供標準的對話方塊。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 提供所選取色彩的標準的對話方塊。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 提供選取字型的標準的對話方塊。  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 用於搜尋和取代作業的標準的對話方塊。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 指定列印檔案提供標準的對話方塊。  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 提供 Windows 2000 列印屬性工作表。  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 封裝 Windows 通用版面設定對話方塊中提供的服務附加支援設定及修改列印邊界。  
  
## OLE 通用對話方塊。  
 OLE 加入數個通用對話方塊的控制代碼。  這些類別會封裝 OLE 通用對話方塊。  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 由框架包含所有 OLE 對話方塊的通用實作。  在使用者介面 \(UI\) 分類的所有對話方塊類別中衍生自這個基底類別。  無法直接使用`COleDialog` 。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 顯示插入物件對話方塊，插入新的 OLE 連結或內嵌項目使用標準的使用者介面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 顯示選擇性貼上對話方塊，實作的編輯選擇性貼上命令使用標準的使用者介面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 顯示編輯連結對話方塊中，使用標準的使用者介面對連結項目的修改資訊。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 顯示變更圖示對話方塊，變更的圖示使用標準的使用者介面與 OLE 內嵌或連結的項目。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 顯示轉換對話方塊，轉譯的 OLE 項目標準使用者介面從一個型別對應到另一個。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封裝 Windows 通用 OLE 屬性對話方塊。  通用 OLE 屬性對話方塊讓您能夠輕鬆顯示和修改 OLE 文件項目的某些屬性與 Windows 標準。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 顯示更新對話方塊中，更新的所有連結使用標準的使用者介面在文件。  對話方塊包含進度指示器指出關閉更新程序是如何對完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 顯示變更來源對話方塊中，變更連結的來源或目的使用標準的使用者介面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 顯示伺服器沒有回應的處理和的伺服器對話方塊，處理呼叫標準使用者介面為忙碌應用程式。  通常會自動顯示由 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) 實作。  
  
## 屬性工作表類別  
 屬性工作表類別可讓您的應用程式使用屬性工作表，也就是索引標籤式對話方塊。  屬性工作表的更有效率方式組織在單一對話方塊的大量的控制項。  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 提供在屬性工作表中的個別頁面。  從每個頁面的 `CPropertyPage` 衍生類別可以將加入至屬性工作表。  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 這個屬性頁提供框架。  從 `CPropertySheet` 衍生您自己的屬性工作表類別快速實作自己的屬性工作表。  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 顯示 OLE automation 控制項的屬性在圖形介面的，類似於對話方塊。  
  
## 以 HTML 為基礎的對話方塊類別。  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 用來建立實作其與 HTML 的使用者介面而非對話方塊資源的對話方塊。  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 將多個 HTML 執行網頁和處理來自每頁的事件。  
  
## 相關類別  
 這些類別不是就其本身而言對話方塊，但是，使用對話方塊範本並有許多對話方塊行為。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 根據對話方塊樣板的控制列。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 設定對話方塊範本中定義的捲動檢視。  衍生自 `CFormView` 類別實作以對話方塊範本的使用者介面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供一個表單檢視直接連接到資料存取物件 \(DAO\) 資料錄集物件。  就像所有表單檢視 `CDaoRecordView` ，根據對話方塊範本。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供一個表單檢視直接連接至開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料錄集物件。  就像所有表單檢視 `CRecordView` ，根據對話方塊範本。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含列印或預覽列印工作的結構資訊。  使用由 [CView](../mfc/reference/cview-class.md)列印結構。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)