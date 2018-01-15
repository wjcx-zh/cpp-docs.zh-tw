---
title: "TN022： 標準命令實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.commands
dev_langs: C++
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05e5e927ebfcb1584913d6415349c473bde4463c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn022-standard-commands-implementation"></a>TN022：標準命令實作
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示描述 MFC 2.0 所提供的標準命令實作。 讀取[技術提示 21](../mfc/tn021-command-and-message-routing.md)第一個因為它會說明用來實作的許多標準命令的機制。  
  
 此描述會假設知識 MFC 架構、 Api 和常見的程式設計作法。 文件，以及未記載之 「 實作僅 「 應用程式開發介面有描述。 這不是開始學習的功能或如何以 MFC 程式的位置。 如需詳細資訊，並記載的 Api 的詳細資料，請參閱 Visual c + +。  
  
## <a name="the-problem"></a>問題  
 MFC 標頭檔 AFXRES 中定義許多標準命令 Id。H. Framework 支援的這些命令而有所不同。 了解架構類別何處以及如何處理這些命令不會只顯示您如何架構的內部運作，但會提供有用的資訊如何自訂標準的實作，並教導您數種技術實作您的命令處理常式。  
  
## <a name="contents-of-this-technical-note"></a>這個技術提示的內容  
 每個命令 ID 是由兩個章節所述：  
  
-   標題： 命令 ID 的符號名稱 (例如， **ID_FILE_SAVE**) 後面接著冒號分隔 （例如，"來儲存目前文件 」） 命令的目的。  
  
-   一或多個段落描述哪些類別實作命令，與預設實作的功能  
  
 大部分的預設命令實作被 prewired 架構的基底類別訊息對應中。 有一些需要明確的連接，衍生類別中的命令實作方式。 這些是 「 注意 」 下所述。 如果您在 AppWizard 選擇正確的選項，這些預設處理常式將為您產生的基本架構應用程式中連接。  
  
## <a name="naming-convention"></a>命名規範  
 標準命令，請依照下列簡單的命名慣例，我們建議您盡可能使用。 大部分的標準命令位於應用程式的功能表列中的標準位置。 此命令的符號名稱開頭"ID_"後面加上標準的快顯功能表名稱，後面接著功能表項目名稱。 符號名稱是使用底線斷字法的上限情況下。 對於不會有標準功能表項目名稱的命令，邏輯命令定義名稱開頭為"ID_"(例如， **ID_NEXT_PANE**)。  
  
 我們會使用前置詞"ID_"表示設計用來繫結至功能表項目、 工具列按鈕或其他命令的使用者介面物件的命令。 處理 「 ID_"命令的命令處理常式應該使用`ON_COMMAND`和`ON_UPDATE_COMMAND_UI`機制的 MFC 命令架構。  
  
 我們建議您未遵循命令架構和需要功能表特定程式碼來啟用和停用這些功能表項目使用標準 「 IDM_"前置詞。 當然功能表特定命令的數目應該很小因為遵循 MFC 命令架構不僅 （因為它們都可以使用工具列） 讓命令處理常式是更為強大，但也可讓命令處理常式程式碼可重複使用。  
  
## <a name="id-ranges"></a>識別碼範圍  
 請參閱[技術提示 20](../mfc/tn020-id-naming-and-numbering-conventions.md)如需詳細資訊，在 MFC 中的識別碼範圍使用。  
  
 MFC 的標準命令落在範圍內要 0xEFFF 0xE000。 請不要依賴這些識別碼的特定值因為它們都可能會在未來版本的程式庫中的變更。  
  
 您的應用程式應該在範圍內 0x8000 至 0xDFFF 定義其命令。  
  
## <a name="standard-command-ids"></a>標準命令 Id  
 對於每個命令識別碼，沒有標準訊息列提示字串可在檔案的提示中找到。RC。 該功能表提示字串 ID 必須是一樣命令 id。  
  
-   ID_FILE_NEW 建立新的/空白文件。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnFileNew`應用程式中實作此命令，以不同的方式視文件範本數目而定。 如果只有一個`CDocTemplate`，`CWinApp::OnFileNew`會建立該型別，以及適當的框架和檢視類別的新文件。  
  
     如果有一個以上`CDocTemplate`，`CWinApp::OnFileNew`會提示使用者與對話方塊 (**AFX_IDD_NEWTYPEDLG**) 但是讓他們可以選取要使用的文件類型。 所選`CDocTemplate`用來建立文件。  
  
     一個常見的自訂的`ID_FILE_NEW`是要提供不同和文件類型的圖形化選項。 在此情況下您可以實作您自己**CMyApp::OnFileNew**並將它放在您的訊息對應，而不是`CWinApp::OnFileNew`。 沒有需要呼叫基底類別實作。  
  
     另一個常見的自訂`ID_FILE_NEW`是提供一個個別的命令建立每個類型的文件。 在此情況下，您應該定義新的命令識別碼，例如 ID_FILE_NEW_CHART 和 ID_FILE_NEW_SHEET。  
  
-   ID_FILE_OPEN 開啟現有文件。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnFileOpen`有非常簡單的實作，於呼叫**CWinApp::DoPromptFileName**後面`CWinApp::OpenDocumentFile`来開啟的檔案的檔案或路徑名稱。 `CWinApp`實作常式**DoPromptFileName**標準 FileOpen 對話方塊隨即開啟，並填入取自目前文件範本的副檔名。  
  
     一個常見的自訂的`ID_FILE_OPEN`是來自訂 [開啟舊檔] 對話方塊或新增其他檔案篩選器。 若要自訂此的建議的方式是將預設實作取代您自己的 FileOpen 對話方塊中，並呼叫`CWinApp::OpenDocumentFile`文件的檔案或路徑名稱。 沒有需要呼叫基底類別。  
  
-   ID_FILE_CLOSE 關閉目前開啟的文件。  
  
     **CDocument::OnFileClose**呼叫`CDocument::SaveModified`提示使用者儲存文件，如果它已經過修改，然後呼叫`OnCloseDocument`。 所有右邏輯，包括破壞文件，都是在`OnCloseDocument`常式。  
  
    > [!NOTE]
    >  **ID_FILE_CLOSE**做以不同的方式從`WM_CLOSE`訊息或**SC_CLOSE**系統命令傳送至文件框架視窗。 關閉視窗會顯示文件的最後一個框架視窗時，才關閉文件。 關閉使用中文件**ID_FILE_CLOSE**才不會關閉文件，但所有顯示的文件的框架視窗將會關閉。  
  
-   ID_FILE_SAVE 儲存目前的文件。  
  
     實作會使用 helper 常式**CDocument::DoSave** ，可用來同時**OnFileSave**和**OnFileSaveAs**。 如果您儲存之前尚未儲存的文件 （也就是它並沒有為路徑名稱，如果是 FileNew） 或已讀取從唯讀的文件， **OnFileSave**邏輯有如**ID_FILE_SAVE_AS**命令，並要求使用者提供新的檔案名稱。 開啟檔案，並執行儲存的實際程序透過虛擬函式`OnSaveDocument`。  
  
     有兩個常見的原因，若要自訂**ID_FILE_SAVE**。 對於沒有儲存的文件，只要移除**ID_FILE_SAVE**功能表項目和工具列按鈕，從您的使用者介面。 此外也請確定您永遠不會變更您的文件 (也就是永遠不會呼叫`CDocument::SetModifiedFlag`) 和架構永遠不會造成要儲存文件。 對於某處儲存至磁碟檔以外的文件，定義新的命令，該作業。  
  
     如果是`COleServerDoc`， **ID_FILE_SAVE**同時用於儲存的檔案 （適用於一般的文件） 並 （適用於內嵌的文件） 的檔案更新。  
  
     如果文件資料會儲存在個別的磁碟檔案，但是您不想使用預設的**CDocument**序列化實作，您應該覆寫`CDocument::OnSaveDocument`而不是**OnFileSave**。  
  
-   ID_FILE_SAVE_AS 儲存目前的文件不同的檔案名稱。  
  
     **CDocument::OnFileSaveAs**實作會使用相同**CDocument::DoSave** helper 常式做為**OnFileSave**。 **OnFileSaveAs**就如同處理命令**ID_FILE_SAVE**如果文件儲存之前沒有任何檔案名稱。 **COleServerDoc::OnFileSaveAs**儲存一般文件資料檔案，或儲存表示 OLE 物件的伺服器文件的邏輯內嵌在其他應用程式是以個別檔案中的實作。  
  
     如果您自訂的邏輯**ID_FILE_SAVE**，您可能會想要自訂**ID_FILE_SAVE_AS**類似的方式或 另存新檔 」 的作業可能會套用到您的文件。 如果不需要您可以從功能表列移除功能表項目。  
  
-   ID_FILE_SAVE_COPY_AS 來儲存複製目前文件以新名稱。  
  
     **COleServerDoc::OnFileSaveCopyAs**實作是非常類似於**CDocument::OnFileSaveAs**，不同之處在於文件物件不 「 附加 」 到基礎檔案後儲存。 也就是記憶體中的文件的 「 修改 」 在儲存之前，如果它是仍 「 修改 」。 此外，此命令會具有不會影響路徑名稱或儲存在文件的標題。  
  
-   ID_FILE_UPDATE 通知儲存內嵌的文件容器。  
  
     `COleServerDoc::OnUpdateDocument`實作只要 notifiies 應儲存內嵌的容器。 容器接著呼叫適當 OLE Api 以儲存內嵌的物件。  
  
-   ID_FILE_PAGE_SETUP 會叫用應用程式的特定頁面安裝/版面配置 對話方塊。  
  
     目前有這個對話方塊中，沒有標準而且架構有預設的實作此命令。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_FILE_PRINT_SETUP 叫用標準的列印設定 對話方塊。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     此命令會叫用標準列印設定對話方塊，可讓使用者自訂印表機及列印設定至少這份文件或最多的所有文件在此應用程式。 您必須使用控制台中，若要變更預設的印表機設定整個系統。  
  
     `CWinApp::OnFilePrintSetup`有非常簡單的實作，建立`CPrintDialog`物件並呼叫**CWinApp::DoPrintDialog**實作函式。 這會設定應用程式的預設印表機設定。  
  
     一般需要自訂此命令可讓每個文件的印表機設定，應該儲存與文件儲存時。 若要這樣做，您應該加入中的訊息對應處理常式您**CDocument**類別會建立`CPrintDialog`物件，請使用適當的印表機屬性將它初始化 (通常**hDevMode**和**hDevNames**)，呼叫**CPrintDialog::DoModal，**並儲存變更的印表機的設定。 健全的實作，您應該查看的實作**CWinApp::DoPrintDialog**偵測錯誤和**CWinApp::UpdatePrinterSelection**合理的預設值處理和追蹤整個系統的印表機變更。  
  
-   ID_FILE_PRINT 標準列印目前文件的功能  
  
    > [!NOTE]
    >  您必須連接為您`CView`-衍生類別的訊息對應，若要啟用這項功能。  
  
     此命令會列印目前文件，或更正確地開始列印程序，牽涉到叫用標準的列印對話方塊，並執行列印引擎。  
  
     **CView::OnFilePrint**可實作此命令與主要列印迴圈。 它會呼叫虛擬`CView::OnPreparePrinting`與 [列印] 對話方塊之使用者的提示。 然後它會準備輸出 DC 移至印表機、 列印進度 對話方塊隨即開啟 (**AFX_IDD_PRINTDLG**)，並將傳送`StartDoc`逸出到印表機。 **CView::OnFilePrint**也包含主要頁面導向列印迴圈。 針對每個頁面上，它會呼叫虛擬`CView::OnPrepareDC`後面`StartPage`逸出，然後呼叫虛擬`CView::OnPrint`分頁。 完成時，虛擬`CView::OnEndPrinting`呼叫時，並關閉 [列印] 進度對話方塊。  
  
     MFC 列印架構被設計來攔截 (hook) 中列印和預覽列印的許多不同的方式。 您通常會發現各種`CView`適合任何頁面導向的列印工作的可覆寫函式。 只在使用印表機的非頁面導向輸出，您應該會發現需要取代的應用程式的情況下**ID_FILE_PRINT**實作。  
  
-   目前的文件 ID_FILE_PRINT_PREVIEW 輸入預覽列印模式。  
  
    > [!NOTE]
    >  您必須連接為您`CView`-衍生類別的訊息對應，若要啟用這項功能。  
  
     **CView::OnFilePrintPreview**藉由呼叫記載的 helper 函式會啟動預覽列印模式**CView::DoPrintPreview**。 **CView::DoPrintPreview**是一樣的預覽列印迴圈的主要引擎**OnFilePrint**是列印迴圈的主要引擎。  
  
     預覽列印作業可以藉由傳遞不同的參數，以自訂各種方式**DoPrintPreview**。 請參閱[技術附註 30](../mfc/tn030-customizing-printing-and-print-preview.md)、 會討論的一些預覽列印的詳細資訊以及如何加以自訂。  
  
-   **ID_FILE_MRU_FILE1**...**FILE16**檔案最近使用的命令 Id 範圍`list`。  
  
     **CWinApp::OnUpdateRecentFileMenu**是更進階的用途之一是更新命令 UI 處理常式`ON_UPDATE_COMMAND_UI`機制。 在功能表資源中，您只需要定義單一的功能表項目識別碼**ID_FILE_MRU_FILE1**。 該功能表項目會維持原先停用。  
  
     為 MRU 清單成長，多個功能表項目加入至清單。 標準`CWinApp`實作預設為標準的四個最近使用過的檔案限制。 您可以變更預設值，藉由呼叫`CWinApp::LoadStdProfileSettings`變大或較小的值。 MRU 清單會儲存在應用程式中。INI 檔案。 在您的應用程式中載入清單`InitInstance`函式，如果您呼叫`LoadStdProfileSettings`，並儲存您的應用程式結束時。 MRU 更新命令 UI 處理常式也會將轉換絕對路徑 [檔案] 功能表上顯示的相對路徑。  
  
     **CWinApp::OnOpenRecentFile**是`ON_COMMAND`執行實際的命令處理常式。 它只會從 MRU 清單和呼叫取得檔案名稱`CWinApp::OpenDocumentFile`，其會開啟檔案並更新 MRU 清單的所有工作。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_EDIT_CLEAR 清除目前的選取範圍  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供的實作此命令使用`CEdit::Clear`。 如果沒有目前的選取範圍，則命令會停用。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_CLEAR_ALL 清除整份文件。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。 請參閱 MFC 教學課程範例[SCRIBBLE](../visual-cpp-samples.md)範例實作。  
  
-   ID_EDIT_COPY 會將目前的選取範圍複製到剪貼簿。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供的實作，此命令，將目前所選取的文字複製到剪貼簿 CF_TEXT 使用`CEdit::Copy`。 如果沒有目前的選取範圍，則命令會停用。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_CUT 剪下目前的選取範圍至剪貼簿。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供的實作，這個命令，將目前選取的文字剪下到剪貼簿 CF_TEXT 使用`CEdit::Cut`。 如果沒有目前的選取範圍，則命令會停用。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_FIND 開始尋找作業，就會尋找非強制回應對話方塊開啟。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供此命令，就會呼叫實作 helper 函式的實作**OnEditFindReplace**使用，並將先前的尋找/取代設定儲存在私用實作變數。 `CFindReplaceDialog`類別用來管理非強制回應對話方塊，提示使用者。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_PASTE 插入目前的剪貼簿內容。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供的複製目前剪貼簿的資料取代所選取的文字使用這個命令實作`CEdit::Paste`。 如果沒有，命令會停用任何**CF_TEXT**剪貼簿中。  
  
     **COleClientDoc**只是這個命令中提供的更新命令 UI 處理常式。 如果剪貼簿不包含內嵌 OLE 項目/物件，此命令將停用。 您必須負責撰寫實際執行的實際貼上命令處理常式。 如果您的 OLE 應用程式也可以貼上其他格式，您應該提供您自己更新命令 UI 處理常式在檢視或文件中的 (也就是某個位置之前**COleClientDoc**命令目標路由中)。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
     取代標準 OLE 實作使用`COleClientItem::CanPaste`。  
  
-   ID_EDIT_PASTE_LINK 插入從目前的剪貼簿內容的連結。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `COleDocument`此命令，只是提供的更新命令 UI 處理常式。 如果剪貼簿不包含連結的 OLE 項目/物件，此命令將停用。 您必須負責撰寫實際執行的實際貼上命令處理常式。 如果您的 OLE 應用程式也可以貼上其他格式，您應該提供您自己更新命令 UI 處理常式在檢視或文件中的 (也就是某個位置之前`COleDocument`命令目標路由中)。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
     取代標準 OLE 實作使用`COleClientItem::CanPasteLink`。  
  
-   ID_EDIT_PASTE_SPECIAL 插入目前的剪貼簿內容與選項。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。 MFC 不提供此對話方塊。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_REPEAT 重複最後一項作業。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供此命令重複最後一個的尋找作業的實作。 可用的最後一個尋找的私用實作變數。 如果無法嘗試尋找，命令會停用。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_REPLACE 開始取代作業，取代非強制回應 對話方塊隨即開啟。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供此命令，就會呼叫實作 helper 函式的實作**OnEditFindReplace**使用，並將先前的尋找/取代設定儲存在私用實作變數。 `CFindReplaceDialog`類別用來管理非強制回應對話方塊，提示使用者。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_SELECT_ALL 選取整份文件。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供這個命令會選取所有文字文件中的實作。 如果沒有選取文字，則會停用命令。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_UNDO 復原上一個作業。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     `CEditView`提供的實作，這個命令，使用`CEdit::Undo`。 如果此命令會停用`CEdit::CanUndo`會傳回 FALSE。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_EDIT_REDO 重做上一個作業。  
  
     目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_WINDOW_NEW 開啟使用中文件的另一個視窗。  
  
     **CMDIFrameWnd::OnWindowNew**使用目前的文件的文件範本建立另一個包含目前文件的另一個檢視的框架會實作這個強大的功能。  
  
     大部分多個文件介面 (MDI) 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。  
  
     不建議使用此命令處理常式的自訂。 如果您想要提供建立額外的檢視或框架視窗的命令，您可能會比較好的方式 ¬ 您自己的命令。 您可以複製程式碼從**CMDIFrameWnd::OnWindowNew**並加以修改以您慣用的特定框架和檢視類別。  
  
-   在 MDI 視窗底部的 ID_WINDOW_ARRANGE 排列圖示。  
  
     `CMDIFrameWnd`實作 helper 函式以實作此標準的 MDI 命令**OnMDIWindowCmd**。 此協助程式將命令 Id 對應至 MDI 視窗訊息，因此會共用大量程式碼。  
  
     大部份 MDI 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_WINDOW_CASCADE 重疊顯示視窗重疊。  
  
     `CMDIFrameWnd`實作 helper 函式以實作此標準的 MDI 命令**OnMDIWindowCmd**。 此協助程式將命令 Id 對應至 MDI 視窗訊息，因此會共用大量程式碼。  
  
     大部份 MDI 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_WINDOW_TILE_HORZ 磚 windows 水平。  
  
     此命令中實作`CMDIFrameWnd`一樣**ID_WINDOW_CASCADE**、 但不同的 MDI 視窗訊息作業所用的。  
  
     您的應用程式，您就應該挑選預設的並排方向。 您可以藉由變更視窗 」 磚 功能表項目的 ID 為**ID_WINDOW_TILE_HORZ**或**ID_WINDOW_TILE_VERT**。  
  
-   ID_WINDOW_TILE_VERT 磚 windows 垂直。  
  
     此命令中實作`CMDIFrameWnd`一樣**ID_WINDOW_CASCADE**、 但不同的 MDI 視窗訊息作業所用的。  
  
     您的應用程式，您就應該挑選預設的並排方向。 您可以藉由變更視窗 」 磚 功能表項目的 ID 為**ID_WINDOW_TILE_HORZ**或**ID_WINDOW_TILE_VERT**。  
  
-   分隔器 ID_WINDOW_SPLIT 鍵盤介面。  
  
     `CView`處理此命令為`CSplitterWnd`實作。 如果檢視是分隔視窗的一部分，此命令會將實作函式委派`CSplitterWnd::DoKeyboardSplit`。 這可讓鍵盤使用者分割，或取消分隔視窗的分割模式中將用來分隔。  
  
     如果檢視不是分隔器，此命令會停用。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_APP_ABOUT 會叫用 [關於] 對話方塊。  
  
     沒有標準的實作應用程式的相關方塊。 預設 AppWizard 建立的應用程式會建立您的應用程式的自訂對話方塊類別並用它做為您的相關方塊。 AppWizard 也會撰寫簡單的命令處理常式處理這個命令，會叫用對話方塊。  
  
     您幾乎一律會實作此命令。  
  
-   ID_APP_EXIT 結束應用程式。  
  
     **CWinApp::OnAppExit**處理這個命令藉由傳送`WM_CLOSE`應用程式的主視窗的訊息。 正在關閉 （提示已變更的檔案，依此類推） 的應用程式的標準由`CFrameWnd`實作。  
  
     不建議使用此命令處理常式的自訂。 覆寫`CWinApp::SaveAllModified`或`CFrameWnd`建議關閉邏輯。  
  
     如果您選擇實作此命令，我們建議使用此命令識別碼。  
  
-   ID_HELP_INDEX 列出說明主題。HLP 檔案。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnHelpIndex`處理這個命令藉由兩者呼叫`CWinApp::WinHelp`。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_HELP_USING 顯示說明如何使用說明。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnHelpUsing`處理這個命令藉由兩者呼叫`CWinApp::WinHelp`。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_CONTEXT_HELP 在輸入 SHIFT-F1 說明模式。  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnContextHelp`處理這個命令藉由設定 [說明] 模式游標、 輸入強制回應迴圈並等候使用者選取要取得說明的視窗。 請參閱[技術附註 28](../mfc/tn028-context-sensitive-help-support.md)詳細說明 MFC 實作。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_HELP 提供目前內容的說明  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     `CWinApp::OnHelp`處理此命令取得目前應用程式內容的權限的說明內容。 這個方法會處理簡單的 F1 說明、 訊息方塊的說明，依此類推。 請參閱[技術附註 28](../mfc/tn028-context-sensitive-help-support.md) MFC 的詳細說明實作。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_DEFAULT_HELP 顯示預設說明內容  
  
    > [!NOTE]
    >  您必須連接為您`CWinApp`-衍生類別的訊息對應，若要啟用這項功能。  
  
     此命令通常會對應至`CWinApp::OnHelpIndex`。  
  
     如果想要使用預設的 說明與 說明 索引之間的差異，可以提供不同的命令處理常式。  
  
-   ID_NEXT_PANE 會移至下一個窗格  
  
     `CView`處理此命令為`CSplitterWnd`實作。 如果檢視是分隔視窗的一部分，此命令會將實作函式委派**CSplitterWnd::OnNextPaneCmd**。 這會將現用檢視表移到分隔器的下一個窗格。  
  
     如果檢視不是分隔器或移至沒有下一個窗格，此命令會停用。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_PREV_PANE 前往上一個窗格  
  
     `CView`處理此命令為`CSplitterWnd`實作。 如果檢視是分隔視窗的一部分，此命令會將實作函式委派**CSplitterWnd::OnNextPaneCmd**。 這會將上一個窗格中用來分隔移現用檢視表。  
  
     如果檢視不是分隔器或移至沒有上一個窗格，此命令會停用。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_OLE_INSERT_NEW 插入一個新的 OLE 物件  
  
     目前沒有任何標準的實作，此命令。 您必須實作此作業對於您`CView`-衍生的類別，在目前的選取範圍中插入新的 OLE 項目/物件。  
  
     所有的 OLE 用戶端應用程式應該實作此命令。 AppWizard，OLE 選項時，會建立基本架構實作**OnInsertObject**中檢視類別，您必須完成。  
  
     請參閱 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)此命令的完整實作的範例。  
  
-   ID_OLE_EDIT_LINKS 編輯 OLE 連結  
  
     `COleDocument`使用 MFC 提供實作的標準 OLE 連結 對話方塊，以處理此命令。 透過存取此對話方塊實作`COleLinksDialog`類別。 如果目前文件不包含任何連結，此命令會停用。  
  
     不建議使用此命令處理常式的自訂。  
  
-   ID_OLE_VERB_FIRST...OLE 指令動詞的最後一個識別碼範圍  
  
     `COleDocument`使用此命令 ID 範圍的目前選取的 OLE 項目/物件支援的動詞。 因為指定的 OLE 項目/物件型別可以支援零個或多個自訂動詞命令必須在範圍內。 在您的應用程式功能表中，您應該有一個功能表項目識別碼為**ID_OLE_VERB_FIRST**。 當程式執行時，功能表將會更新與適當的功能表動詞描述 （或有許多動詞命令的快顯功能表）。 OLE 功能表的管理由`AfxOleSetEditMenu`，此命令的更新命令 UI 處理常式中完成。  
  
     沒有明確的命令處理常式處理每個範圍中的命令 ID。 **COleDocument::OnCmdMsg**會覆寫以攔截這個範圍內的所有命令識別碼、 變成以零為起始的動詞命令的數字，並啟動該動詞命令的伺服器 (使用`COleClientItem::DoVerb`)。  
  
     不建議自訂或其他使用此命令識別碼範圍。  
  
-   ID_VIEW_TOOLBAR 切換工具列開啟 / 關閉  
  
     `CFrameWnd`處理這個命令，並更新命令 UI 處理常式來切換工具列的可見狀態。 工具列必須是子視窗框架的子視窗識別碼與`AFX_IDW_TOOLBAR`。 命令處理常式實際切換工具列視窗的可見性。 `CFrameWnd::RecalcLayout`用來重新繪製其新的狀態與工具列的框架視窗。 更新命令 UI 處理常式會檢查功能表項目，則工具列會顯示。  
  
     不建議使用此命令處理常式的自訂。 如果您想要新增其他工具列，您會想要複製和修改命令處理常式和更新命令 UI 處理常式，此命令。  
  
-   ID_VIEW_STATUS_BAR 會開啟和關閉切換狀態列  
  
     中實作此命令`CFrameWnd`一樣**ID_VIEW_TOOLBAR**，除非其他子視窗 ID (**AFX_IDW_STATUS_BAR**) 使用。  
  
## <a name="update-only-command-handlers"></a>僅更新命令處理常式  
 在狀態列中的指標用數種標準命令 Id。 這些使用的相同處理機制的更新命令 UI 以顯示其目前的視覺狀態在應用程式的閒置時間。 由於使用者無法選取 （也就是說，您無法發送狀態列窗格），則它沒有任何意義有`ON_COMMAND`這些命令 Id 的處理常式。  
  
-   **ID_INDICATOR_CAPS** : CAP 鎖定指示器。  
  
-   **ID_INDICATOR_NUM** : NUM lock 指標。  
  
-   **ID_INDICATOR_SCRL** : SCRL 鎖定指示器。  
  
-   **ID_INDICATOR_KANA** ： 假名鎖定指示器 （僅適用於日文系統）。  
  
 會實作所有三個**CFrameWnd::OnUpdateKeyIndicator**，對應至適當的虛擬索引鍵使用的命令 ID 的實作協助程式。 一般實作啟用或停用 （停用狀態窗格 = 沒有文字）`CCmdUI`根據是否適當的虛擬機碼，所以目前鎖定的物件。  
  
 不建議使用此命令處理常式的自訂。  
  
-   **ID_INDICATOR_EXT: EXT**結束選取的指標。  
  
-   **ID_INDICATOR_OVR： 關於**e**R**strike 指標。  
  
-   **ID_INDICATOR_REC： 應收帳**ording 指標。  
  
 目前沒有任何標準的實作，這些指標。  
  
 如果您選擇實作這些指示器，我們建議您使用這些標記識別碼以及維護自己的狀態列的指示器的順序 (也就是依此順序： EXT、 CAP、 NUM、 SCRL、 OVR、 REC)。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

