---
title: 建置 MFC 應用程式的作業順序
ms.date: 09/09/2019
helpviewer_keywords:
- applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
ms.openlocfilehash: ab5f9bcd50ab2f2c5456ca666ef79f7033966589
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907567"
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>建置 MFC 應用程式的作業順序

下表說明當您開發 MFC 應用程式時，通常會遵循的一般順序。

### <a name="sequence-for-building-an-application-with-the-framework"></a>使用架構建置應用程式的順序

|工作|您會做|架構會做|
|----------|------------|------------------------|
|建立基本架構應用程式。|執行 [ [MFC 應用程式]](../mfc/reference/mfc-application-wizard.md)。 在選項頁面中指定所需選項。 這些選項包括將應用程式建立為 COM 元件、容器 (或兩者)，加入 Automation，以及使應用程式支援資料庫。|[MFC 應用程式精靈] 會建立基本架構應用程式的檔案，包括應用程式的原始程式檔、文件、檢視和框架視窗、資源檔、專案檔，以及其他所有符合您規格的項目。|
|查看架構和 MFC 應用程式精靈提供的項目，而不需在您的程式碼中新增任何程式碼。|在 Visual C++ 中建置並執行基本架構應用程式。|執行中的基本架構應用程式會從 framework 衍生許多標準 [檔案]、[**編輯** **]、[** **查看** **] 和 [** 說明] 功能表命令。 對於 MDI 應用程式，您也會取得完整的 Windows 功能表，而架構會管理 MDI 子視窗的建立、排列和解構等動作。|
|建構應用程式的使用者介面。|使用視覺效果C++ [資源編輯器](../windows/resource-editors.md)，以視覺化方式編輯應用程式的使用者介面：<br /><br /> -[建立] 功能表。<br />-定義加速器。<br />-建立對話方塊。<br />-建立和編輯點陣圖、圖示和游標。<br />-編輯 MFC 應用程式精靈為您建立的工具列。<br />-建立和編輯其他資源。<br /><br /> 您也可以在對話方塊編輯器中測試對話方塊。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。 Visual C++ 可讓您透過輕鬆且視覺化的方式編輯現有的資源並加入新的資源。|
|對應功能表與處理函式。|使用 [ [**屬性**] 視窗](/visualstudio/ide/reference/properties-window)**類別檢視**中的 [**事件**] 按鈕（在 [[類別] [Wizard]](reference/mfc-class-wizard.md)的 [**命令**] 索引標籤中），連接功能表和快速鍵與程式碼中的處理函式。|這些工具會在您指定的原始程式檔中插入訊息對應專案和空白函式範本，並管理許多手動編碼工作。|
|撰寫處理常式程式碼。|使用 [類別檢視] 直接跳至原始程式碼編輯器中的程式碼。 填入處理函式的程式碼。 如需有關使用類別檢視以及將程式碼加入至專案之嚮導的詳細資訊，請參閱[使用程式碼嚮導加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。|[類別檢視] 會開啟編輯器、捲動至空函式範本和並為您放置游標的位置。|
|對應工具列按鈕與命令。|藉由為按鈕指派適當的命令 ID，將工具列上的每個按鈕對應至功能表或快速鍵命令。|架構會控制繪製、啟用、停用、檢查和工具列按鈕的其他視覺外觀。|
|測試您的處理函式。|重建程式並使用內建的偵錯工具來測試您的處理常式昰否正確運作。|您可以逐步執行或追蹤程式碼以查看處理常式呼叫的方式。 如果您已填入處理常式程式碼，處理常式便會執行命令。 架構會自動停用未處理的功能表項目和工具列按鈕。|
|加入[對話方塊](../mfc/dialog-boxes.md)。|使用對話方塊編輯器設計對話方塊範本資源。 然後建立對話方塊類別和處理對話方塊的程式碼。|架構會處理對話方塊並協助擷取使用者輸入的資訊。|
|初始化、驗證以及擷取對話方塊資料。|您也可以定義對話方塊的控制項如何初始化及驗證。 使用 Visual Studio 將成員變數加入至對話方塊類別，並將它們對應至對話方塊控制項。 指定使用者輸入資料時，套用到每個控制項的驗證規則。 如果需要的話，也可以提供您的自訂驗證。|架構會處理對話方塊的初始化及驗證。 如果使用者輸入無效的資訊，架構會顯示一個訊息方塊，並讓使用者重新輸入資料。|
|建立其他類別。|使用 [類別檢視] 建立 MFC 應用程式精靈不會自動建立的其他文件、檢視和框架視窗類別。 您可以建立其他資料庫資料錄集類別、對話方塊類別等等 (使用 [類別檢視] 時，您可以建立不從 MFC 類別衍生的類別)。|[類別檢視] 會將這些類別加入至原始程式檔，並協助您定義它們與其處理之所有命令的連接。|
|對您的應用程式加入立即可用的元件。|使用`New Item dialog box`以加入各種項目。|這些項目可以很容易地整合到您的應用程式，並可節省大量工作。|
|實作您的文件類別。|實作應用程式專屬的文件類別或類別。 加入成員變數來保存資料結構。 加入成員函式以提供介面給資料。|架構已經知道如何與文件資料檔案互動。 它可開啟和關閉文件檔案、讀取和寫入文件的資料，以及處理其他使用者介面。 您可以將焦點放在如何操作文件的資料。|
|實作開啟、儲存和另存新檔命令。|撰寫文件的 `Serialize` 成員函式的程式碼。|此架構會在 [檔案] 功能表上顯示 [**開啟**]、[**儲存**]**和 [** **另存**新檔] 命令的對話方塊。 它會使用 `Serialize` 成員函式中所指定的資料格式讀取並寫入一個文件。|
|實作您的檢視類別。|實作一個或多個與文件對應的檢視類別。 針對已使用 [類別檢視] 對應至使用者介面的項目實作檢視的成員函式。 有各種[CView](../mfc/reference/cview-class.md)衍生的類別可供使用，包括[CListView](../mfc/reference/clistview-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。|架構會處理大部分文件及其檢視之間的關聯性。 檢視的成員函式會存取檢視的文件，以便在螢幕或列印頁面上呈現其影像，以及更新文件的資料結構以回應使用者編輯的命令。|
|強化預設的列印。|如果需要支援多頁列印，請覆寫檢視成員函式。|此架構**支援 [檔案] 功能表上**的 [**列印**]、[版面**設定**] 和 [**預覽列印**] 命令。 您必須告訴它如何為您的文件分頁。|
|加入捲動功能。|如果您需要支援滾動，請從[CScrollView](../mfc/reference/cscrollview-class.md)衍生您的 view 類別或類別。|當檢視視窗變得太小時，檢視會自動加入捲軸。|
|建立表單檢視。|如果您想要以對話方塊範本資源為您的視圖做為基礎，請從[CFormView](../mfc/reference/cformview-class.md)衍生您的 view 類別或類別。|檢視會使用對話方塊範本資源來顯示控制項。 使用者可以在檢視中的各個控制項之間切換。|
|建立資料庫表單。|如果您想要以表單為基礎的資料存取應用程式，請從[CRecordView](../mfc/reference/crecordview-class.md) （適用于 ODBC 程式設計）衍生您的 view 類別。|此視圖的運作方式與表單檢視相同，但其控制項會連接到代表資料庫資料表之[CRecordset](../mfc/reference/crecordset-class.md)物件的欄位。 MFC 會為您在控制項與資料錄集之間移動資料。|
|建立簡單的文字編輯器。|如果您想要讓視圖成為簡單的文字編輯器，請從[CEditView](../mfc/reference/ceditview-class.md)或[CRichEditView](../mfc/reference/cricheditview-class.md)衍生您的 view 類別或類別。|檢視會提供編輯功能、剪貼簿支援和檔案 I/O。 `CRichEditView` 提供可套用樣式的文字。|
|加入分隔視窗。|如果您想要支援視窗分割，請將[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)物件新增至您的 SDI 框架視窗或 MDI 子視窗，並在視窗的[OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient)成員函式中連結。|架構會在捲軸旁邊提供分隔器方塊控制項，並將您的檢視分割為多個窗格。 如果使用者分割了某個視窗，架構會建立並附加其他檢視物件至文件。|
|建置、測試，以及偵錯應用程式。|使用 Visual C++ 的功能來建置、測試和偵錯應用程式。|Visual C++ 可讓您調整編譯、連結和其他選項。 它也可讓您瀏覽原始程式碼和類別結構。|

## <a name="see-also"></a>另請參閱

[建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)<br/>
[在架構上建置](../mfc/building-on-the-framework.md)
