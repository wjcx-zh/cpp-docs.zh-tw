---
title: TN022:標準命令實作
ms.date: 11/04/2016
f1_keywords:
- vc.commands
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
ms.openlocfilehash: 8d568760cc75a4c1f2ddb6dd88108cc830783194
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775827"
---
# <a name="tn022-standard-commands-implementation"></a>TN022:標準命令實作

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示描述 MFC 2.0 所提供的標準命令實作。 讀取[技術提示 21](../mfc/tn021-command-and-message-routing.md)第一個因為它會說明用來實作許多標準命令的機制。

此描述會假設的 MFC 架構、 Api 和常見的程式設計做法的知識。 文件，以及未記載之 「 實作僅 」 會描述 Api。 這不是開始學習的功能或如何以 MFC 程式的地方。 視覺效果，請參閱C++如需詳細資訊以及記載的 Api 的詳細資料。

## <a name="the-problem"></a>問題

MFC 標頭檔 AFXRES 定義許多標準命令 Id。H. 這些命令的架構支援而異。 了解架構類別，以及如何處理這些命令不會只顯示您如何架構的內部運作，但如何自訂標準的實作，並教導您一些技術實作提供實用的資訊您自己的命令處理常式。

## <a name="contents-of-this-technical-note"></a>這個技術提示的內容

每個命令識別碼是由兩個各節所述：

- 標題： 以冒號分隔的命令 ID (例如 ID_FILE_SAVE) 的符號名稱，後面接著命令 （例如，"來儲存目前的文件 」） 的目的。

- 一或多個段落描述哪些類別實作的命令，以及預設實作的作用

大部分的預設命令實作被 prewired 架構的基底類別訊息對應中。 有一些需要明確的連接，在您的衍生類別中的命令實作。 說明在 < 注意事項 >。 如果您在 AppWizard 選擇適當的選項，這些預設處理常式將為您產生的基本架構應用程式中連線。

## <a name="naming-convention"></a>命名規範

標準命令，請依照下列簡單的命名慣例，我們建議您盡可能使用。 大部分的標準命令位於 應用程式的功能表列中的標準位置中。 此命令的符號名稱開頭 「 ID_"後面加上標準的快顯功能表名稱，後面接著功能表項目名稱。 符號名稱是以底線斷字法的大寫。 對於不會有標準的功能表項目名稱的命令，邏輯的命令定義名稱開頭為"ID_ 」 (比方說，ID_NEXT_PANE)。

我們會使用前置詞"ID_ 」 來表示設計用來繫結至功能表項目、 工具列按鈕或其他命令的使用者介面物件的命令。 處理 「 ID_"命令的命令處理常式應該使用 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 機制在 MFC 的命令架構。

我們建議您不遵循命令架構並需要特定功能表的程式碼，來啟用和停用這些功能表項目使用標準的 「 IDM_"前置詞。 當然功能表特定命令的數目應該很小因為遵循 MFC 命令架構不僅 （因為它們都可以使用工具列） 讓命令處理常式是更為強大，但可讓命令處理常式程式碼可重複使用。

## <a name="id-ranges"></a>識別碼範圍

請參閱[技術提示 20](../mfc/tn020-id-naming-and-numbering-conventions.md)如需詳細資訊，在 MFC 中的 識別碼範圍使用。

MFC 的標準命令落在範圍內以 0xEFFF 0xE000。 請不要依賴這些識別碼的特定值因為它們是在程式庫的未來版本中有所變更。

您的應用程式應該定義其命令，在範圍內 0x8000 至 0xDFFF。

## <a name="standard-command-ids"></a>標準命令 Id

每個命令識別碼，沒有標準訊息列提示字串，可在檔案的提示。RC。 該功能表提示字串 ID 必須是相同命令 id。

- ID_FILE_NEW 建立新的/空白文件。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnFileNew` 應用程式中實作此命令，以不同的方式是根據文件範本的數目。 如果只有一個`CDocTemplate`，`CWinApp::OnFileNew`會建立該型別，以及在適當的框架和檢視類別的新文件。

   如果有一個以上`CDocTemplate`，`CWinApp::OnFileNew`會對使用者提示對話方塊 (AFX_IDD_NEWTYPEDLG) 讓他們選取哪些文件使用的型別。 所選`CDocTemplate`用來建立文件。

   ID_FILE_NEW 的一個常見的自訂是要提供不同與更多的圖形化選擇的文件類型。 在此情況下您可以實作您自己`CMyApp::OnFileNew`並將它放在您的訊息對應，而不是`CWinApp::OnFileNew`。 沒有需要呼叫基底類別實作。

   ID_FILE_NEW 的另一個常見的自訂是提供個別的命令來建立每個類型的文件。 在此情況下，您應該定義新的命令識別碼，例如 ID_FILE_NEW_CHART 和 ID_FILE_NEW_SHEET。

- ID_FILE_OPEN 開啟現有文件。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnFileOpen` 已呼叫的簡單實作`CWinApp::DoPromptFileName`後面接著`CWinApp::OpenDocumentFile`来開啟之檔案的檔案或路徑名稱。 `CWinApp`實作常式`DoPromptFileName`會顯示標準的 [開啟舊檔] 對話方塊，並填入取自目前的文件範本的副檔名。

   ID_FILE_OPEN 的一個常見的自訂是來自訂 [開啟舊檔] 對話方塊或新增額外的檔案篩選器。 若要自訂此建議的方式是取代您自己的 FileOpen 對話方塊中，並呼叫的預設實作`CWinApp::OpenDocumentFile`文件的檔案或路徑名稱。 沒有需要呼叫基底類別。

- ID_FILE_CLOSE 關閉目前開啟的文件。

   `CDocument::OnFileClose` 呼叫`CDocument::SaveModified`提示使用者儲存文件，如果它已經過修改，然後呼叫`OnCloseDocument`。 全部關閉邏輯，包括破壞文件，都在`OnCloseDocument`常式。

    > [!NOTE]
    >  ID_FILE_CLOSE 行為不同於 WM_CLOSE 訊息或傳送到文件框架視窗 SC_CLOSE 系統命令。 這是顯示文件的最後一個框架視窗時，才關閉視窗會關閉文件。 關閉文件與 ID_FILE_CLOSE 才不會關閉文件，但所有顯示的文件的框架視窗會關閉。

- ID_FILE_SAVE 儲存目前的文件。

   此實作會使用協助程式常式`CDocument::DoSave`它用於同時`OnFileSave`和`OnFileSaveAs`。 如果您儲存之前尚未儲存的文件 （也就是它並沒有為路徑名稱，如果是 FileNew） 或已從唯讀的文件，讀取`OnFileSave`邏輯就像 ID_FILE_SAVE_AS 命令，並要求使用者提供新的檔案名稱. 開啟檔案，並執行儲存的實際程序透過虛擬函式`OnSaveDocument`。

   有兩個常見的原因，若要自訂 ID_FILE_SAVE。 對於沒有儲存的文件，只要移除 ID_FILE_SAVE 功能表項目和工具列按鈕從您的使用者介面。 也請確定您永遠不會中途文件 (也就是永遠不會呼叫`CDocument::SetModifiedFlag`) 和架構永遠不會造成要儲存的文件。 對於某處儲存到磁碟檔案以外的文件，定義新的命令，該作業。

   如果是`COleServerDoc`，ID_FILE_SAVE 用於儲存的檔案 （適用於一般的文件） 及更新檔 （適用於內嵌的文件）。

   如果您的文件資料會儲存在個別的磁碟檔案，但不想使用預設值`CDocument`序列化實作，您應該覆寫`CDocument::OnSaveDocument`而不是`OnFileSave`。

- ID_FILE_SAVE_AS 儲存目前的文件，以不同的檔案名稱。

   `CDocument::OnFileSaveAs`實作會使用相同`CDocument::DoSave`協助程式常式做為`OnFileSave`。 `OnFileSaveAs`如果文件不有任何檔案名稱，在儲存之前就如同 ID_FILE_SAVE 處理命令。 `COleServerDoc::OnFileSaveAs` 實作儲存標準文件資料檔案，或在儲存代表做為個別檔案的某些其他應用程式中內嵌之 OLE 物件的伺服器文件的邏輯。

   如果您自訂的 ID_FILE_SAVE 邏輯時，您可能會想要以類似的方式自訂 ID_FILE_SAVE_AS 或者 「 另存新檔 」 的作業可能不適用於您的文件。 如果不需要您可以從功能表列移除功能表項目。

- ID_FILE_SAVE_COPY_AS 儲存複製目前文件以新名稱。

   `COleServerDoc::OnFileSaveCopyAs`實作是非常類似於`CDocument::OnFileSaveAs`，不同之處在於文件物件沒有 「 附加 」 基礎檔案儲存後。 也就是說，如果記憶體中的文件的 「 修改 」 在儲存之前，它是仍然 「 修改 」。 此外，這個命令會有不會影響路徑名稱或儲存在文件的標題。

- ID_FILE_UPDATE 通知來儲存內嵌的文件容器。

   `COleServerDoc::OnUpdateDocument`實作只要 notifiies 應該儲存內嵌的容器。 然後，容器會呼叫適當 OLE Api 來儲存內嵌的物件。

- ID_FILE_PAGE_SETUP 叫用的特定應用程式頁面設定/配置 對話方塊。

   目前沒有標準的這個對話方塊中，而架構這個命令沒有預設實作。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_FILE_PRINT_SETUP 叫用標準 [列印設定] 對話方塊。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   此命令會叫用標準列印設定 對話方塊，可讓使用者自訂印表機和列印設定至少這份文件或最多的所有文件在此應用程式。 您必須使用控制台中變更整個系統的預設印表機設定。

   `CWinApp::OnFilePrintSetup` 具有非常簡單的實作，建立`CPrintDialog`物件並呼叫`CWinApp::DoPrintDialog`實作函式。 這會設定應用程式的預設印表機設定。

   常見的需求自訂此命令可讓每個文件的印表機設定，應該儲存在儲存時的文件。 若要這樣做，您應該加入中的訊息對應處理常式您`CDocument`建立的類別`CPrintDialog`物件，初始化具有適當的印表機屬性 (通常*hDevMode*和*hDevNames*)，呼叫`CPrintDialog::DoModal`，並儲存變更的印表機設定。 健全的實作，您應該查看的實作`CWinApp::DoPrintDialog`偵測錯誤和`CWinApp::UpdatePrinterSelection`處理合理的預設值，以及追蹤整個系統的印表機的變更。

- ID_FILE_PRINT 標準列印目前文件的功能

    > [!NOTE]
    >  您也必須將此選項可連接您`CView`-衍生類別的訊息對應，以啟用此功能。

   此命令會列印目前文件，或更正確開始列印程序，這牽涉到叫用標準的列印對話方塊，並執行列印的引擎。

   `CView::OnFilePrint` 會實作這個命令，並在主要的列印迴圈。 它會呼叫虛擬`CView::OnPreparePrinting`到命令提示字元 [列印] 對話方塊的使用者。 它會準備要移至印表機的輸出 DC、 顯示列印的進度對話方塊 (AFX_IDD_PRINTDLG)，然後傳送`StartDoc`到印表機的逸出。 `CView::OnFilePrint` 也包含主要頁面導向列印迴圈。 針對每個頁面中，它會呼叫虛擬`CView::OnPrepareDC`後面接著`StartPage`逸出，然後呼叫虛擬`CView::OnPrint`該頁面。 完成時，虛擬`CView::OnEndPrinting`呼叫時，並列印的進度對話方塊已關閉。

   MFC 列印架構被設計來連結中列印和預覽列印的許多不同的方式。 您通常會發現各種`CView`適合任何頁面導向的列印工作的可覆寫函式。 只有在使用印表機的非網頁導向輸出的應用程式，萬一您發現需要取代 ID_FILE_PRINT 實作。

- ID_FILE_PRINT_PREVIEW 輸入目前文件的預覽列印模式。

    > [!NOTE]
    >  您也必須將此選項可連接您`CView`-衍生類別的訊息對應，以啟用此功能。

   `CView::OnFilePrintPreview` 藉由呼叫記錄協助程式函式啟動預覽列印模式`CView::DoPrintPreview`。 `CView::DoPrintPreview` 就如同是預覽列印迴圈的主要引擎`OnFilePrint`是列印迴圈的主要引擎。

   預覽列印作業可以藉由傳遞不同的參數，以自訂的各種不同的方式`DoPrintPreview`。 請參閱[技術的附註 30](../mfc/tn030-customizing-printing-and-print-preview.md)，其中討論了一些的預覽列印的詳細資料，以及如何加以自訂。

- ID_FILE_MRU_FILE1...FILE16 檔案最近使用的命令 Id 的範圍**清單**。

   `CWinApp::OnUpdateRecentFileMenu` 已更新命令 UI 處理常式是其中一個較進階的 ON_UPDATE_COMMAND_UI 機制的用法。 在您的功能表資源中，您只需要使用識別碼 ID_FILE_MRU_FILE1，以定義單一功能表項目。 該功能表項目會保留原先停用。

   為 MRU 清單成長，更多的功能表項目加入至清單。 標準`CWinApp`實作預設為標準的四個最近使用過的檔案限制。 您可以變更預設值，藉由呼叫`CWinApp::LoadStdProfileSettings`變大或較小的值。 MRU 清單會儲存在應用程式。INI 檔案。 在您的應用程式中載入清單`InitInstance`函式，如果您呼叫`LoadStdProfileSettings`，且會儲存您的應用程式結束時。 MRU 更新命令 UI 處理常式也會將轉換的絕對路徑顯示在 [檔案] 功能表上的相對路徑。

   `CWinApp::OnOpenRecentFile` 是執行實際的命令 ON_COMMAND 處理常式。 它只會從 MRU 清單及呼叫取得的檔案名稱`CWinApp::OpenDocumentFile`，開啟檔案並更新 MRU 清單的所有作業。

   不建議使用此命令處理常式的自訂。

- ID_EDIT_CLEAR 清除目前的選取範圍

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作此命令使用`CEdit::Clear`。 如果沒有目前的選取範圍，則會停用的命令。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_CLEAR_ALL 清除整份文件。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。 請參閱 MFC 教學課程範例[SCRIBBLE](../overview/visual-cpp-samples.md)如需範例實作。

- ID_EDIT_COPY 會將目前的選取範圍複製到剪貼簿。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作此命令，將目前選取的文字複製到剪貼簿作為 CF_TEXT 使用`CEdit::Copy`。 如果沒有目前的選取範圍，則會停用的命令。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_CUT 剪下目前的選取範圍至剪貼簿。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作此命令，將目前選取的文字剪下到剪貼簿 CF_TEXT 使用`CEdit::Cut`。 如果沒有目前的選取範圍，則會停用的命令。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_FIND 開始尋找作業，會帶出 [非強制回應尋找] 對話方塊。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作 helper 函式會呼叫此命令的實作`OnEditFindReplace`使用，並將先前的尋找/取代設定儲存在私用實作變數。 `CFindReplaceDialog`類別用來管理非強制回應對話方塊，提示使用者。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_PASTE 插入目前的剪貼簿內容。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作這個命令中，它將會複製目前的剪貼簿資料取代選取的文字使用`CEdit::Paste`。 如果沒有，命令會停用沒有**CF_TEXT**剪貼簿中。

   `COleClientDoc` 此命令，只是提供的更新命令 UI 處理常式。 如果剪貼簿不包含可內嵌 OLE 項目/物件，此命令將會停用。 您負責撰寫實際的命令，以執行實際的貼上的處理常式。 如果您的 OLE 應用程式也可以貼上其他格式，您應該提供您的檢視或文件中您自己更新命令 UI 處理常式 (也就是某處之前`COleClientDoc`命令目標路由)。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

   取代標準的 OLE 實作使用`COleClientItem::CanPaste`。

- ID_EDIT_PASTE_LINK 插入從目前的剪貼簿內容的連結。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `COleDocument` 此命令，只是提供的更新命令 UI 處理常式。 如果剪貼簿不包含可連結的 OLE 項目/物件，此命令將會停用。 您負責撰寫實際的命令，以執行實際的貼上的處理常式。 如果您的 OLE 應用程式也可以貼上其他格式，您應該提供您的檢視或文件中您自己更新命令 UI 處理常式 (也就是某處之前`COleDocument`命令目標路由)。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

   取代標準的 OLE 實作使用`COleClientItem::CanPasteLink`。

- ID_EDIT_PASTE_SPECIAL 插入目前的剪貼簿內容與選項。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。 MFC 不提供此對話方塊。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_REPEAT 會重複上一個作業。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供此命令來重複最後一個尋找作業的實作。 會使用最後一個尋找的私用實作變數。 如果無法嘗試尋找，命令會停用。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_REPLACE 開始取代作業，會帶出取代非強制回應對話方塊。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作 helper 函式會呼叫此命令的實作`OnEditFindReplace`使用，並將先前的尋找/取代設定儲存在私用實作變數。 `CFindReplaceDialog`類別用來管理非強制回應對話方塊，提示使用者。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_SELECT_ALL 選取整份文件。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供的實作，此命令會選取文件中的所有文字。 如果不沒有選取任何文字，則會停用的命令。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_UNDO 復原最後一個作業。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   `CEditView` 提供實作，這個命令，並使用`CEdit::Undo`。 如果此命令會停用`CEdit::CanUndo`會傳回 FALSE。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_EDIT_REDO 重做上一個作業。

   目前沒有任何標準的實作，此命令。 您必須針對每個實作此`CView`-衍生的類別。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- ID_WINDOW_NEW 會開啟另一個使用中文件的視窗。

   `CMDIFrameWnd::OnWindowNew` 使用目前的文件的文件範本來建立另一個框架，其中包含目前的文件的另一個檢視，會實作這個功能強大的功能。

   大部分多個文件介面 (MDI) 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。

   不建議使用此命令處理常式的自訂。 如果您想要提供建立額外的檢視或框架視窗的命令，您可能會比較理想的選擇發明自己的命令。 您可以複製的程式碼`CMDIFrameWnd::OnWindowNew`並修改它以您的喜好的特定框架和檢視類別。

- 在 MDI 視窗底部的 ID_WINDOW_ARRANGE 排列圖示。

   `CMDIFrameWnd` 實作 helper 函式中實作此標準的 MDI 命令`OnMDIWindowCmd`。 此協助程式會將命令 Id 對應至 MDI Windows 訊息，而且可以因此共用大量程式碼。

   大部分的 MDI 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。

   不建議使用此命令處理常式的自訂。

- ID_WINDOW_CASCADE 串聯，windows 才會重疊。

   `CMDIFrameWnd` 實作 helper 函式中實作此標準的 MDI 命令`OnMDIWindowCmd`。 此協助程式會將命令 Id 對應至 MDI Windows 訊息，而且可以因此共用大量程式碼。

   大部分的 MDI 視窗功能表命令，例如命令已停用，如果沒有任何作用中的 MDI 子視窗。

   不建議使用此命令處理常式的自訂。

- ID_WINDOW_TILE_HORZ 磚 windows 水平。

   此命令實作在`CMDIFrameWnd`一樣 ID_WINDOW_CASCADE，除了作業使用不同的 MDI Windows 訊息。

   您的應用程式，您應該挑選預設的並排顯示方向。 您可以變更視窗的 [磚] 功能表項目的 ID ID_WINDOW_TILE_HORZ 或 ID_WINDOW_TILE_VERT 來執行這項操作。

- ID_WINDOW_TILE_VERT 磚 windows 垂直。

   此命令實作在`CMDIFrameWnd`一樣 ID_WINDOW_CASCADE，除了作業使用不同的 MDI Windows 訊息。

   您的應用程式，您應該挑選預設的並排顯示方向。 您可以變更視窗的 [磚] 功能表項目的 ID ID_WINDOW_TILE_HORZ 或 ID_WINDOW_TILE_VERT 來執行這項操作。

- ID_WINDOW_SPLIT 鍵盤介面，用以分隔器。

   `CView` 此命令會處理`CSplitterWnd`實作。 如果分隔器視窗的部分檢視，此命令會將實作函式委派`CSplitterWnd::DoKeyboardSplit`。 這會將分隔器模式，讓鍵盤使用者，將分割或解除分隔器視窗。

   如果檢視表不在分隔器，此命令會停用。

   不建議使用此命令處理常式的自訂。

- ID_APP_ABOUT 叫用 [關於] 對話方塊。

   不會有標準實作應用程式的相關方塊。 預設 AppWizard 建立的應用程式會建立您的應用程式的自訂對話方塊類別，並使用它作為您相關的方塊。 AppWizard 也會撰寫簡單的命令處理常式，它會處理此命令，並叫用對話方塊。

   您幾乎一律會實作這個命令。

- ID_APP_EXIT 結束應用程式。

   `CWinApp::OnAppExit` 處理此命令的方式傳送 WM_CLOSE 訊息給應用程式的主視窗。 正在關閉 （提示已變更的檔案，依此類推） 的應用程式的標準由`CFrameWnd`實作。

   不建議使用此命令處理常式的自訂。 覆寫`CWinApp::SaveAllModified`或`CFrameWnd`建議關閉邏輯。

   如果您選擇實作這個命令，我們建議使用這個命令識別碼。

- 從的 ID_HELP_INDEX 列出說明主題。HLP 檔案。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnHelpIndex` 處理這個命令透過極簡方式呼叫`CWinApp::WinHelp`。

   不建議使用此命令處理常式的自訂。

- ID_HELP_USING 顯示說明如何使用說明。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnHelpUsing` 處理這個命令透過極簡方式呼叫`CWinApp::WinHelp`。

   不建議使用此命令處理常式的自訂。

- ID_CONTEXT_HELP 進入 SHIFT-F1 說明模式。

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnContextHelp` 透過設定 [說明] 模式游標、 輸入強制回應迴圈並等候使用者選取來取得 [說明] 視窗中處理這個命令。 請參閱[技術提示 28](../mfc/tn028-context-sensitive-help-support.md)如需詳細資訊，幫助的 MFC 實作。

   不建議使用此命令處理常式的自訂。

- ID_HELP 提供目前內容的說明

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   `CWinApp::OnHelp` 處理此命令取得目前的應用程式內容的權限的說明內容。 這個方法會處理簡單的 F1 說明、 訊息方塊的說明，依此類推。 請參閱[技術提示 28](../mfc/tn028-context-sensitive-help-support.md) MFC 的更多有關協助實作。

   不建議使用此命令處理常式的自訂。

- ID_DEFAULT_HELP 顯示預設說明內容

    > [!NOTE]
    >  您也必須將此選項可連接您`CWinApp`-衍生類別的訊息對應，以啟用此功能。

   此命令通常會對應至`CWinApp::OnHelpIndex`。

   如果想要使用預設的 說明與 說明 索引之間的差異，可以提供不同的命令處理常式。

- ID_NEXT_PANE 會移至下一個窗格

   `CView` 此命令會處理`CSplitterWnd`實作。 如果分隔器視窗的部分檢視，此命令會將實作函式委派`CSplitterWnd::OnNextPaneCmd`。 這會將現用檢視表移至下一個窗格分隔器中。

   如果分隔器不是檢視，或是沒有任何下一步 窗格，即可移至，則會停用此命令。

   不建議使用此命令處理常式的自訂。

- ID_PREV_PANE 前往上一個窗格

   `CView` 此命令會處理`CSplitterWnd`實作。 如果分隔器視窗的部分檢視，此命令會將實作函式委派`CSplitterWnd::OnNextPaneCmd`。 這會將現用檢視表移到上一個窗格分隔器中。

   如果分隔器不是檢視，或是沒有任何先前的窗格，即可移至，則會停用此命令。

   不建議使用此命令處理常式的自訂。

- ID_OLE_INSERT_NEW 插入一個新的 OLE 物件

   目前沒有任何標準的實作，此命令。 您必須實作此項目，您`CView`-衍生類別，以在目前的選取範圍中插入新的 OLE 項目/物件。

   所有的 OLE 用戶端應用程式應該實作這個命令。 AppWizard，使用 [OLE] 選項中，將會建立基本架構實作`OnInsertObject`您您必須完成的檢視類別中。

   請參閱 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)此命令的完整實作的範例。

- ID_OLE_EDIT_LINKS 編輯 OLE 連結

   `COleDocument` 使用標準的 OLE 連結 對話方塊的 MFC 提供實作，以處理此命令。 透過存取此對話方塊實作`COleLinksDialog`類別。 如果目前文件不包含任何連結，此命令會停用。

   不建議使用此命令處理常式的自訂。

- ID_OLE_VERB_FIRST...OLE 動詞命令的最後一個識別碼範圍

   `COleDocument` 使用這個命令 ID 範圍的目前選取的 OLE 項目/物件所支援的動詞命令。 這必須是範圍，因為指定的 OLE 項目] / [物件類型都可以支援零個或多個自訂動詞命令。 在您的應用程式功能表中，您應該有一個功能表項目 ID_OLE_VERB_FIRST 的識別碼。 當程式執行時，功能表將會更新具有適當的功能表動詞描述 （或有許多的動詞命令的快顯功能表）。 OLE 功能表的管理由`AfxOleSetEditMenu`，此命令更新命令 UI 處理常式中完成。

   沒有明確的命令處理常式處理每個在此範圍中的命令 ID。 `COleDocument::OnCmdMsg` 會覆寫以攔截這個範圍內的所有命令識別碼、 將它們轉換成以零為起始的動詞命令的數字，並啟動該動詞命令的伺服器 (使用`COleClientItem::DoVerb`)。

   不建議自訂或其他使用此命令 ID 範圍。

- ID_VIEW_TOOLBAR 在開啟和關閉切換工具列

   `CFrameWnd` 處理此命令，並更新命令 UI 處理常式切換工具列的可見狀態。 工具列必須是具有子視窗框架的子視窗的 AFX_IDW_TOOLBAR 識別碼。 命令處理常式實際上會切換 [工具列] 視窗的可見性。 `CFrameWnd::RecalcLayout` 用來與工具列的框架視窗重新繪製它的新狀態。 當工具列為可見時，更新命令 UI 處理常式會檢查功能表項目。

   不建議使用此命令處理常式的自訂。 如果您想要新增額外的工具列，您會想要複製並修改命令處理常式和更新命令 UI 處理常式，此命令。

- ID_VIEW_STATUS_BAR 切換狀態列上，開啟和關閉

   此命令實作在`CFrameWnd`一樣 ID_VIEW_TOOLBAR，除了識別碼 (AFX_IDW_STATUS_BAR) 會使用不同的子視窗。

## <a name="update-only-command-handlers"></a>僅限更新命令處理常式

數個標準命令 Id 做為在狀態列中的指標。 這些使用的相同處理機制的更新命令 UI 以顯示其目前的視覺狀態在應用程式閒置時間。 因為使用者無法選取 （也就是說，您無法發送狀態列窗格），則它沒有任何意義有 ON_COMMAND 處理常式，這些命令識別碼。

- ID_INDICATOR_CAPS:CAP 鎖定指示器。

- ID_INDICATOR_NUM:NUM lock 指標。

- ID_INDICATOR_SCRL:SCRL 鎖定指示器。

- ID_INDICATOR_KANA:假名鎖定 （僅適用於日文的系統） 的指標。

在中實作這三種`CFrameWnd::OnUpdateKeyIndicator`，對應至適當的虛擬機碼中使用的命令 ID 的實作協助程式。 常見的實作啟用或停用 （停用的狀態窗格 = 沒有文字）`CCmdUI`取決於是否適當的虛擬按鍵目前已鎖定的物件。

不建議使用此命令處理常式的自訂。

- ID_INDICATOR_EXT:擴充選取的指標。

- ID_INDICATOR_OVR:覆寫指標。

- ID_INDICATOR_REC:記錄指標。

目前沒有任何標準的實作，這些指標。

如果您選擇實作這些指示器，我們建議您使用這些指標的識別碼，並維護自己的狀態列的指示器的順序 (也就是依此順序：EXT、 CAP、 NUM、 SCRL、 OVR、 REC）。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
