---
title: 建置 MFC 應用程式的作業順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bafcec75643c292a887b54de1b852609dd251c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383805"
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>建置 MFC 應用程式的作業順序
下表說明當您開發 MFC 應用程式時，通常會遵循的一般順序。  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>使用架構建置應用程式的順序  
  
|工作|您會做|架構會做|  
|----------|------------|------------------------|  
|建立基本架構應用程式。|執行[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)。 在選項頁面中指定所需選項。 這些選項包括將應用程式建立為 COM 元件、容器 (或兩者)，加入 Automation，以及使應用程式支援資料庫。|[MFC 應用程式精靈] 會建立基本架構應用程式的檔案，包括應用程式的原始程式檔、文件、檢視和框架視窗、資源檔、專案檔，以及其他所有符合您規格的項目。|  
|查看架構和 MFC 應用程式精靈提供的項目，而不需在您的程式碼中新增任何程式碼。|在 Visual C++ 中建置並執行基本架構應用程式。|執行基本架構應用程式衍生許多標準**檔案**，**編輯**，**檢視**，和**協助**從架構的功能表命令。 對於 MDI 應用程式，您也會取得完整的 Windows 功能表，而架構會管理 MDI 子視窗的建立、排列和解構等動作。|  
|建構應用程式的使用者介面。|使用 Visual c + +[資源編輯器](../windows/resource-editors.md)以視覺化方式編輯應用程式的使用者介面：<br /><br /> -建立功能表。<br />-定義快速鍵。<br />-建立對話方塊。<br />-建立和編輯點陣圖、 圖示和游標。<br />-編輯 MFC 應用程式精靈為您建立的工具列。<br />-建立和編輯其他資源。<br /><br /> 您也可以在對話方塊編輯器中測試對話方塊。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。 Visual C++ 可讓您透過輕鬆且視覺化的方式編輯現有的資源並加入新的資源。|  
|對應功能表與處理函式。|使用**事件**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)連接功能表和快速鍵與處理函式程式碼中。|[屬性] 視窗會插入訊息對應項目和空函示範本到您指定的原始程式檔中，並管理許多手動編碼的工作。|  
|撰寫處理常式程式碼。|使用 [類別檢視] 直接跳至原始程式碼編輯器中的程式碼。 填入處理函式的程式碼。 如需使用類別檢視 和精靈加入程式碼加入專案的相關資訊，請參閱[使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。|[類別檢視] 會開啟編輯器、捲動至空函式範本和並為您放置游標的位置。|  
|對應工具列按鈕與命令。|藉由為按鈕指派適當的命令 ID，將工具列上的每個按鈕對應至功能表或快速鍵命令。|架構會控制繪製、啟用、停用、檢查和工具列按鈕的其他視覺外觀。|  
|測試您的處理函式。|重建程式並使用內建的偵錯工具來測試您的處理常式昰否正確運作。|您可以逐步執行或追蹤程式碼以查看處理常式呼叫的方式。 如果您已填入處理常式程式碼，處理常式便會執行命令。 架構會自動停用未處理的功能表項目和工具列按鈕。|  
|新增[對話方塊](../mfc/dialog-boxes.md)。|使用對話方塊編輯器設計對話方塊範本資源。 然後建立對話方塊類別和處理對話方塊的程式碼。|架構會處理對話方塊並協助擷取使用者輸入的資訊。|  
|初始化、驗證以及擷取對話方塊資料。|您也可以定義對話方塊的控制項如何初始化及驗證。 使用 Visual Studio 將成員變數加入至對話方塊類別，並將它們對應至對話方塊控制項。 指定使用者輸入資料時，套用到每個控制項的驗證規則。 如果需要的話，也可以提供您的自訂驗證。|架構會處理對話方塊的初始化及驗證。 如果使用者輸入無效的資訊，架構會顯示一個訊息方塊，並讓使用者重新輸入資料。|  
|建立其他類別。|使用 [類別檢視] 建立 MFC 應用程式精靈不會自動建立的其他文件、檢視和框架視窗類別。 您可以建立其他資料庫資料錄集類別、對話方塊類別等等 (使用 [類別檢視] 時，您可以建立不從 MFC 類別衍生的類別)。|[類別檢視] 會將這些類別加入至原始程式檔，並協助您定義它們與其處理之所有命令的連接。|  
|對您的應用程式加入立即可用的元件。|使用`New Item dialog box`以加入各種項目。|這些項目可以很容易地整合到您的應用程式，並可節省大量工作。|  
|實作您的文件類別。|實作應用程式專屬的文件類別或類別。 加入成員變數來保存資料結構。 加入成員函式以提供介面給資料。|架構已經知道如何與文件資料檔案互動。 它可開啟和關閉文件檔案、讀取和寫入文件的資料，以及處理其他使用者介面。 您可以將焦點放在如何操作文件的資料。|  
|實作開啟、儲存和另存新檔命令。|撰寫文件的 `Serialize` 成員函式的程式碼。|架構會顯示對話方塊**開啟**，**儲存**，和**存**命令**檔案**功能表。 它會使用 `Serialize` 成員函式中所指定的資料格式讀取並寫入一個文件。|  
|實作您的檢視類別。|實作一個或多個與文件對應的檢視類別。 針對已使用 [類別檢視] 對應至使用者介面的項目實作檢視的成員函式。 各種[CView](../mfc/reference/cview-class.md)-衍生的類別，提供了包括[CListView](../mfc/reference/clistview-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。|架構會處理大部分文件及其檢視之間的關聯性。 檢視的成員函式會存取檢視的文件，以便在螢幕或列印頁面上呈現其影像，以及更新文件的資料結構以回應使用者編輯的命令。|  
|強化預設的列印。|如果需要支援多頁列印，請覆寫檢視成員函式。|架構支援**列印**，**版面**，和**預覽列印**命令**檔案**功能表。 您必須告訴它如何為您的文件分頁。|  
|加入捲動功能。|如果您需要支援捲動，衍生您的檢視類別或類別從[CScrollView](../mfc/reference/cscrollview-class.md)。|當檢視視窗變得太小時，檢視會自動加入捲軸。|  
|建立表單檢視。|如果您想要讓檢視採用對話方塊範本資源，衍生您的檢視類別或類別從[CFormView](../mfc/reference/cformview-class.md)。|檢視會使用對話方塊範本資源來顯示控制項。 使用者可以在檢視中的各個控制項之間切換。|  
|建立資料庫表單。|如果您想以表單為基礎的資料存取應用程式時，衍生檢視類別從[CRecordView](../mfc/reference/crecordview-class.md) （適用於 ODBC 程式設計）。|檢視的運作方式類似於表單檢視中，但它的控制項會連接到的欄位[CRecordset](../mfc/reference/crecordset-class.md)物件，代表資料庫資料表。 MFC 會為您在控制項與資料錄集之間移動資料。|  
|建立簡單的文字編輯器。|如果您想檢視，以簡單的文字編輯器，衍生您的檢視類別或類別從[CEditView](../mfc/reference/ceditview-class.md)或[CRichEditView](../mfc/reference/cricheditview-class.md)。|檢視會提供編輯功能、剪貼簿支援和檔案 I/O。 `CRichEditView` 提供可套用樣式的文字。|  
|加入分隔視窗。|如果您想要支援視窗分割，加入[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)物件至您的 SDI 框架視窗或 MDI 子視窗，並將它連結的視窗中[OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。|架構會在捲軸旁邊提供分隔器方塊控制項，並將您的檢視分割為多個窗格。 如果使用者分割了某個視窗，架構會建立並附加其他檢視物件至文件。|  
|建置、測試，以及偵錯應用程式。|使用 Visual C++ 的功能來建置、測試和偵錯應用程式。|Visual C++ 可讓您調整編譯、連結和其他選項。 它也可讓您瀏覽原始程式碼和類別結構。|  
  
## <a name="see-also"></a>另請參閱  
 [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [一系列的作業，用於建立 ActiveX 控制項](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [在架構上建置](../mfc/building-on-the-framework.md)

