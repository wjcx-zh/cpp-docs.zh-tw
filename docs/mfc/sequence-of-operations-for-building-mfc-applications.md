---
title: "建置 MFC 應用程式的作業順序 | Microsoft Docs"
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
  - "應用程式 [MFC], 開發"
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 建置 MFC 應用程式的作業順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表說明您當您開發 MFC 應用程式時，可能通常遵循的一般序列。  
  
### 提供建立與 Framework 應用程式的順序  
  
|工作|您做|架構做|  
|--------|--------|---------|  
|若要建立骨幹應用程式|執行 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)。  指定要在索引標籤頁要的選項。  選項包括讓應用程式每個 COM 元件，容器 \(或兩者都有\)；加入 Automation；並顯示於應用程式的資料庫中。|MFC 應用程式精靈建立基本架構應用程式的檔案，包括原始程式檔對您的應用程式、文件、檢視和框架視窗;資源檔；專案檔；和其他所有適合您的規格的文件。|  
|查看架構和 MFC 應用程式精靈提供，而不在您的程式碼新增行。|建立基本架構應用程式並在 Visual C\+\+執行。|執行基本架構應用程式從架構衍生許多標準 **File**和 **Edit**和 **Help** 、 \[**檢視**\] 命令。  對於 MDI 應用程式，您也可以取得一份功能完整視窗功能表，因此，架構管理建立、MDI 子視窗的排列和解構。|  
|建構您的應用程式的使用者介面。|使用 Visual C\+\+ [資源編輯器](../mfc/resource-editors.md) 以視覺化方式編輯應用程式的使用者介面:<br /><br /> -   建立功能表<br />-   定義快速鍵。<br />-   建立對話方塊。<br />-   建立及編輯點陣圖、圖示和游標。<br />-   編譯為您建立的工具列由 MFC 應用程式精靈。<br />-   建立和編輯其他資源。<br /><br /> 您也可以測試在對話方塊編輯器的對話方塊。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。  Visual C\+\+ 可讓您輕鬆和視覺化編輯現有的資源並加入新的資源。|  
|對處理函式的導覽功能表。|使用在 [屬性視窗](../Topic/Properties%20Window.md) **Events** 按鈕以連接功能表和快速鍵至處理函式程式碼。|屬性視窗插入訊息對應項目和空函示範本到您指定和處理許多手動編碼的原始檔案中。|  
|撰寫處理常式程式碼。|使用類別檢視直接跳至原始程式碼編輯器的程式碼。  填入您的處理常式函式的程式碼。  如需使用類別檢視和加入專案精靈的詳細資訊，請參閱[使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。|類別檢視開啟編輯器、捲動至空函式範本和位置將游標。|  
|對命令的對應工具列按鈕。|將您的工具列中的每個按鈕加入至功能表或快速鍵命令會將按鈕指派適當的命令 ID.|這個框架繪製控制項，啟用，停用，檢查和工具列按鈕的其他視覺外觀。|  
|測試您的處理函式。|重建程式並使用內建的偵錯工具來測試您的處理常式能夠正確地運作。|您可以逐步執行程式碼或追蹤看到您的處理常式如何呼叫。  如果您完成處理常式程式碼，處理常式會執行命令。  架構會自動停用未處理的功能表項目和工具列按鈕。|  
|加入[對話方塊](../mfc/dialog-boxes.md) 。|設計與對話方塊編輯器的對話方塊範本資源。  然後建立對話方塊類別和處理對話方塊的程式碼。|架構處理對話方塊並加速擷取使用者輸入的資訊。|  
|初始化，驗證，並擷取對話方塊資訊。|您也可以定義對話方塊的控制項如何初始化及驗證。  使用 Visual Studio 將成員變數加入至對話方塊類別和對應至對話方塊控制項。  指定驗證規則套用到每個控制項，使用者輸入資料。  如果您希望，也可以提供您的自訂驗證。|架構處理對話方塊初始化及驗證。  如果使用者輸入無效的資訊，架構會顯示訊息方塊並讓使用者重新輸入資料。|  
|建立其他類別。|使用類別檢視建立其他文件、檢視和框架視窗類別在 MFC 應用程式精靈會自動建立的項目之外。  您可以建立其他資料庫資料錄集類別，對話方塊類別，依此類推。\(使用類別檢視中，您可以從 MFC 類別所衍生的類別\)。|類別檢視加入這些類別加入至原始程式檔並可協助您定義來處理其與所有命令的連接。|  
|對您的應用程式將立即可用的元件。|使用 `New Item dialog box` 以加入各種種類的項目。|這些項目可以整合到您的應用程式和節省大量工作。|  
|實作您的資料類別。|實作應用程式專屬資料類別或類別。  加入成員變數來保存資料結構。  加入成員函式提供介面給資料。|架構已經會與文件資料檔案互動。  它可開啟和關閉文件，讀取和寫入文件的資料，並在其他使用者介面控制。  您可以將焦點放在文件中的資料如何操作。|  
|開啟實作，儲存和另存新檔命令。|文件的 `Serialize` 成員函式的程式碼。|這個框架在 **檔案** 功能表顯示 **開啟**、 **儲存**和 **另存新檔**的命令對話方塊。  它會使用 `Serialize` 成員函式中所指定的資料格式讀取並寫入一個文件。|  
|實作您的檢視類別。|實作一或多個檢視類別與您的檔案對應。  實作檢視的成員函式已對應至與類別檢視的使用者介面。  各種 [CView](../mfc/reference/cview-class.md)衍生類別可以使用，包括 [CListView](../mfc/reference/clistview-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。|架構處理大部分文件及其檢視之間的關聯性。  檢視的成員函式存取檢視的文件呈現其在螢幕或列印頁面的影像和更新文件的資料結構以回應編輯命令的使用者。|  
|引發預設印表機。|如果您需要支援多頁列印，請覆寫檢視成員函式。|架構在 **檔案** 功能表支援 **列印**、 **版面設定。** 和 **預覽列印**命令。  您必須告訴它如何細分成您的資料頁。|  
|加入捲動。|如果您需要支援捲動，從 [CScrollView](../mfc/reference/cscrollview-class.md)衍生您的檢視類別或類別。|當檢視視窗變得太小時，這個檢視會自動將入捲軸。|  
|建立表單檢視。|如果您要根據您的檢視對話方塊範本資源，請從 [CFormView](../mfc/reference/cformview-class.md)衍生您的檢視類別或類別。|檢視使用對話方塊樣板資源為顯示控制項。  使用者可以從控制項選取儲存到檢視中的控制項。|  
|建立資料庫資料表。|如果您想要表單架構的資料存取應用程式，請從 [CRecordView](../mfc/reference/crecordview-class.md) 衍生您的檢視類別 \(適用於 ODBC 程式設計\)。|這個檢視會像表單檢視，不過，它的控制項連接到代表資料庫資料表之 [CRecordset](../mfc/reference/crecordset-class.md) 物件的欄位。  MFC 會為您在資料控制項與資料錄集之間移動。|  
|建立簡單的文字編輯器。|如果您想要檢視是一個簡單的文字編輯器，從 [CEditView](../mfc/reference/ceditview-class.md) 或 [CRichEditView](../mfc/reference/cricheditview-class.md)衍生您的檢視類別或類別。|這個檢視提供編輯功能、剪貼簿支援和檔案 I\/O。  `CRichEditView` 提供要套用樣式的文字。|  
|加入分隔視窗。|如果您要支援分割的視窗，請將 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) 物件加入至您的 SDI 框架視窗或 MDI 子視窗並將它顯示在視窗的 [OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) 成員函式。|架構在捲軸旁邊提供分隔器方塊控制項分割您要將多個窗格。  如果使用者分隔視窗，架構建立和附加至文件的其他檢視物件。|  
|組建，測試，以及偵錯應用程式。|使用 Visual C\+\+ 的功能，以建立測試和偵錯應用程式。|Visual C\+\+ 可讓您調整編譯，連結和其他選項。  它也可讓您瀏覽您的原始程式碼和類別結構。|  
  
## 請參閱  
 [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [在架構上建置](../mfc/building-on-the-framework.md)