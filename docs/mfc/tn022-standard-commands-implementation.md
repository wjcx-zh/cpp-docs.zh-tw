---
title: TN022：標準命令實作
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
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370388"
---
# <a name="tn022-standard-commands-implementation"></a>TN022：標準命令實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明描述了 MFC 2.0 提供的標準命令實現。 首先閱讀[技術說明 21,](../mfc/tn021-command-and-message-routing.md)因為它描述了用於實現許多標準命令的機制。

此描述假定瞭解 MFC 體系結構、API 和常見程式設計實踐。 介紹了文件記錄以及未記錄的"僅實現"API。 這不是開始學習 MFC 的功能或程式設計方式的地方。 有關更多一般資訊和文檔化 API 的詳細資訊,請參閱 Visual C++。

## <a name="the-problem"></a>問題

MFC 在標頭檔 AFXRES 中定義許多標準命令指示。H。 對這些命令的框架支援各不相同。 瞭解框架類處理這些命令的位置和方式不僅會向您展示框架內部工作原理,而且還會提供有關如何自定義標準實現的有用資訊,並教您實現自己的命令處理程式的一些技術。

## <a name="contents-of-this-technical-note"></a>本技術說明的內容

每個指令識別碼由兩部分組成:

- 標題:命令 ID 的符號名稱(例如,ID_FILE_SAVE),後跟命令的目的(例如,"保存當前文檔")用冒號分隔。

- 一個或多個段落,描述哪些類實現命令,以及默認實現的作用

大多數預設命令實現在框架的基類消息映射中預接。 派生類中有些命令實現需要顯式佈線。 這些在"說明"下描述。 如果在 AppWizard 中選擇正確的選項,這些預設處理程式將在生成的骨架應用程式中為您連接。

## <a name="naming-convention"></a>命名慣例

標準命令遵循一個簡單的命名約定,我們建議您盡可能使用。 大多數標準命令位於應用程式功能表欄中的標準位置。 命令的符號名稱以"ID_"開頭,後跟標準彈出功能表名稱,後跟菜單項名稱。 符號名稱在大寫中帶有下劃線單詞中斷。 對於沒有標準功能表項名稱的命令,邏輯命令名稱以"ID_"開頭定義(例如,ID_NEXT_PANE)。

我們使用首碼「ID_」來指示設計綁定到功能表項、工具列按鈕或其他命令使用者介面物件的命令。 處理「ID_」命令的命令處理程式應使用 MFC 命令體系結構ON_COMMAND和ON_UPDATE_COMMAND_UI機制。

對於不遵循命令體系結構且需要特定於功能表的代碼來啟用和禁用它們的功能表項,我們建議您使用標準的"IDM_"前綴。 當然,功能表特定命令的數量應該很小,因為遵循 MFC 命令體系結構不僅使命令處理程式更強大(因為它們將處理工具列),而且使命令處理程式代碼可重用。

## <a name="id-ranges"></a>ID 範圍

有關在 MFC 中使用 ID 範圍的更多詳細資訊,請參閱[技術說明 20。](../mfc/tn020-id-naming-and-numbering-conventions.md)

MFC 標準命令位於 0xE000 到 0xEFFF 範圍內。 請不要依賴這些指示器的特定值,因為它們可能會在庫的未來版本中更改。

應用程式應在 0x8000 到 0xDFFF 範圍內定義其命令。

## <a name="standard-command-ids"></a>標準命令指示

對於每個命令 ID,在檔 PROMPTS 中可以找到一個標準消息列提示符字串。鋼筋混凝土。 該選單提示符號的字串 ID 必須與命令 ID 的字串 ID 相同。

- ID_FILE_NEW 創建新/空文檔。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnFileNew`根據應用程式中的文檔範本數量,以不同的方式實現此命令。 如果只有一個`CDocTemplate`,`CWinApp::OnFileNew`將建立該類型的新文件,以及適當的框架和檢視類。

   如果有多個`CDocTemplate`,`CWinApp::OnFileNew`將提示使用者使用對話框 (AFX_IDD_NEWTYPEDLG),讓他們選擇要使用的文件類型。 所選`CDocTemplate`文件用於創建文檔。

   ID_FILE_NEW的一個常見自定義是提供不同且更圖形化的文檔類型選擇。 在這種情況下,您可以實現自己的`CMyApp::OnFileNew`,並將其放置在消息映射中,`CWinApp::OnFileNew`而不是 。 無需調用基類實現。

   ID_FILE_NEW的另一個常見自定義是提供用於創建每種類型文檔的單獨命令。 在這種情況下,應定義新的命令指示,例如ID_FILE_NEW_CHART和ID_FILE_NEW_SHEET。

- ID_FILE_OPEN 打開現有文檔。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnFileOpen`具有非常簡單的調用`CWinApp::DoPromptFileName`實現,然後`CWinApp::OpenDocumentFile`是 要打開的檔或路徑名稱。 實現`CWinApp`例`DoPromptFileName`程 將彈出標準 FileOpen 對話框,並將其填充從當前文檔範本獲取的檔副檔名。

   ID_FILE_OPEN的一個常見自定義是自定義文件打開對話方塊或添加其他文件篩選器。 自訂此項的建議方法是將預設實現替換為您自己的 FileOpen 對話方塊,然後使用文`CWinApp::OpenDocumentFile`檔的檔或 路徑名稱調用。 無需調用基類。

- ID_FILE_CLOSE關閉當前打開的文檔。

   `CDocument::OnFileClose`呼叫`CDocument::SaveModified`以提示使用者保存文檔(如果文檔已被修改,`OnCloseDocument`然後調用 )。 所有關閉邏輯(包括銷毀文檔)都在例程`OnCloseDocument`中 完成。

    > [!NOTE]
    >  ID_FILE_CLOSE的行為與發送到文檔框架視窗的WM_CLOSE消息或SC_CLOSE系統命令不同。 僅當文件是顯示文件的最後一個框架視窗時,關閉視窗才會關閉該文檔。 用ID_FILE_CLOSE關閉文檔不僅會關閉文檔,還將關閉顯示文檔的所有框架視窗。

- ID_FILE_SAVE保存當前文檔。

   實作使用協助程式的程式,`CDocument::DoSave`該程式設計用於`OnFileSave``OnFileSaveAs`與 。 如果保存以前未保存的文檔(即,它沒有路徑名稱,如 FileNew),或者從唯讀文件讀取的`OnFileSave`文檔, 則邏輯將類似於ID_FILE_SAVE_AS命令,並要求使用者提供新的檔案名。 打開檔並執行保存的實際過程是通過虛擬函數`OnSaveDocument`完成的。

   自定義ID_FILE_SAVE有兩個常見原因。 對於不保存的文檔,只需從使用者介面中刪除ID_FILE_SAVE功能表項和工具列按鈕即可。 還要確保永遠不會弄髒文檔(即從不調用`CDocument::SetModifiedFlag`),並且框架永遠不會導致文檔被保存。 對於保存到磁碟檔以外的某個位置的文檔,請為該操作定義一個新命令。

   在的情況下,ID_FILE_SAVE`COleServerDoc`既用於檔保存(對於普通文檔)又用於檔更新(對於嵌入文檔)。

   如果文件資料儲存在單一磁碟檔案中,但不希望使用預設`CDocument`序列化實現,則應重`CDocument::OnSaveDocument`寫`OnFileSave`而不是 。

- ID_FILE_SAVE_AS將當前文件保存在不同的檔名下。

   使用`CDocument::OnFileSaveAs`與相同的`CDocument::DoSave`說明程式例程式`OnFileSave`。 如果`OnFileSaveAs`文件在保存之前沒有檔名,則該命令的處理方式與ID_FILE_SAVE相同。 `COleServerDoc::OnFileSaveAs`實現用於保存普通文件資料檔或將表示嵌入在其他某個應用程式中的 OLE 物件的伺服器文件作為單獨的檔實現邏輯。

   如果自定義ID_FILE_SAVE的邏輯,則可能需要以類似方式自定義ID_FILE_SAVE_AS,或者"保存為"的操作可能不適用於文檔。 如果需要,可以從菜單欄中刪除功能表項。

- ID_FILE_SAVE_COPY_AS將當前複本保存在新名稱下。

   實現`COleServerDoc::OnFileSaveCopyAs`與`CDocument::OnFileSaveAs`非常相似 ,只是文檔物件在保存後未'附加到"基礎檔。 也就是說,如果記憶體中的文檔在保存之前被"修改",它仍然是"修改的"。 此外,此命令對存儲在文檔中的路徑名稱或標題沒有影響。

- ID_FILE_UPDATE通知容器保存嵌入的文檔。

   實現`COleServerDoc::OnUpdateDocument`只是通知容器應保存嵌入。 然後,容器調用適當的 OLE API 以保存嵌入的物件。

- ID_FILE_PAGE_SETUP調用特定於應用程式的頁面設置/佈局對話方塊。

   目前沒有此對話框的標準,並且框架沒有此命令的預設實現。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_FILE_PRINT_SETUP調用標準列印設置對話方塊。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   此命令調用標準列印設置對話框,允許使用者至少為本文檔或最多此應用程式中的所有文檔自定義印表機和列印設置。 您必須使用「控制面板」更改整個系統的預設印表機設定。

   `CWinApp::OnFilePrintSetup`具有創建`CPrintDialog`對象並調用實現函數的`CWinApp::DoPrintDialog`非常簡單的 實現。 這將設置應用程式預設印表機設置。

   自定義此命令的常見需要是允許每個文檔的印表機設置,這些設置在保存時應隨文檔一起存儲。 為此,應在`CDocument`類中添加一個消息映射處理程式,該處理程式創建一`CPrintDialog`個 物件,使用適當的印表機屬性(通常*為 hDevMode*和*hDevNames)* 初始化它`CPrintDialog::DoModal`,調用 呼叫,並保存已更改的印表機設置。 對於可靠的實現,您應該查看`CWinApp::DoPrintDialog`用於檢測錯誤和`CWinApp::UpdatePrinterSelection`處理 合理的預設值和處理系統範圍印表機更改的實現。

- ID_FILE_PRINT 目前文件的標準列印

    > [!NOTE]
    >  您必須將其連接到`CView`派生類的消息映射才能啟用此功能。

   此命令列印當前文檔,或者更正確地啟動列印過程,這涉及調用標準列印對話方塊並運行列印引擎。

   `CView::OnFilePrint`實現此命令和主列印迴圈。 它調用虛擬`CView::OnPreparePrinting`以提示使用者使用列印對話方塊。 然後,它將輸出 DC 準備轉到印表機,啟動列印進度對話方塊(AFX_IDD_PRINTDLG),然後將`StartDoc`轉義器發送到印表機。 `CView::OnFilePrint`還包含面向頁面的主列印迴圈。 對於每個頁面,它調用虛擬`CView::OnPrepareDC`,後跟`StartPage`一 個轉義`CView::OnPrint`,並調用該頁的虛擬。 完成後,將調用虛擬`CView::OnEndPrinting`,並關閉列印進度對話方塊。

   MFC 列印架構旨在以許多不同的方式進行列印和列印預覽。 您通常會發現各種`CView`可重寫功能足以執行任何面向頁面的列印任務。 僅當應用程式使用印表機進行非面向頁面的輸出時,您才應發現需要替換ID_FILE_PRINT實現。

- ID_FILE_PRINT_PREVIEW輸入當前文件的列印預覽模式。

    > [!NOTE]
    >  您必須將其連接到`CView`派生類的消息映射才能啟用此功能。

   `CView::OnFilePrintPreview`通過調用記錄的説明程式函數`CView::DoPrintPreview`啟動列印預覽模式。 `CView::DoPrintPreview`是列印預覽迴圈的主引擎,就像列印迴圈的主引擎`OnFilePrint`一樣。

   列印預覽操作可以通過將不同的參數傳遞`DoPrintPreview`給 來以多種方式進行自定義。 請參閱[技術說明30,](../mfc/tn030-customizing-printing-and-print-preview.md)其中討論了列印預覽的一些細節以及如何自定義它。

- ID_FILE_MRU_FILE1...FILE16 檔案 MRU 清單的指令指示數**範圍**。

   `CWinApp::OnUpdateRecentFileMenu`是更新命令 UI 處理程式,它是ON_UPDATE_COMMAND_UI機制的更高級用途之一。 在選單資源中,只需定義具有 ID ID_FILE_MRU_FILE1的單個功能表項。 該功能表項最初保持禁用狀態。

   隨著 MRU 清單的增長,更多的功能表項將添加到清單中。 標準`CWinApp`實現預設為四個最近使用的文件的標準限制。 可以通過使用較大或更小的值調`CWinApp::LoadStdProfileSettings`用 來更改預設值。 MRU 清單儲存在應用程式的中。INI 檔。 如果呼叫`LoadStdProfileSettings`,則清單將載入到應用程式`InitInstance`的 函數中,並在應用程式退出時保存。 MRU 更新命令 UI 處理程式還將將絕對路徑轉換為相對路徑,以便顯示在檔案選單上。

   `CWinApp::OnOpenRecentFile`是執行實際命令的ON_COMMAND處理程式。 它只是從 MRU 清單和`CWinApp::OpenDocumentFile`呼叫 中獲取檔名,它執行打開檔和更新 MRU 清單的所有工作。

   不建議自定義此命令處理程式。

- ID_EDIT_CLEAR 清除目前選取

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`使用`CEdit::Clear`提供此命令的實現。 如果沒有當前選擇,則禁用該命令。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_CLEAR_ALL清除整個文檔。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   如果選擇實現此命令,我們建議您使用此命令 ID。 有關實現範例,請參閱 MFC 教程範例[SCRIBBLE。](../overview/visual-cpp-samples.md)

- ID_EDIT_COPY將當前選擇複製到剪貼簿。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此指令的實作,這個指令將目前選取的文字複製到剪貼簿,CF_TEXT`CEdit::Copy`使用 。 如果沒有當前選擇,則禁用該命令。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_CUT將當前選擇剪切到剪貼簿。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此指令的實作,這個指令將目前選取的文字剪下到剪貼簿,CF_TEXT`CEdit::Cut`使用 。 如果沒有當前選擇,則禁用該命令。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_FIND 開始查找操作,則啟動無模式查找對話方塊。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此命令的實現,該命令調用實現説明器函數`OnEditFindReplace`,以便在私有實現變數中使用和存儲以前的查找/替換設置。 類別`CFindReplaceDialog`用於管理用於提示使用者的無模式對話方塊。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_PASTE 插入目前剪貼簿內容。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此命令的實現,該命令使用`CEdit::Paste`複製當前剪貼簿數據,替換選取的文字。 如果剪貼簿中沒有**CF_TEXT,** 則禁用該命令。

   `COleClientDoc`只是為此命令提供更新命令 UI 處理程式。 如果剪貼簿不包含可嵌入的 OLE 項/物件,則該命令將被禁用。 您負責為實際命令編寫處理程式以執行實際粘貼。 如果 OLE 應用程式還可以貼上其他格式,則應在檢視或文件中(即命令目標路由`COleClientDoc`之前的某個位置)中提供您自己的更新命令 UI 處理程式。

   如果選擇實現此命令,我們建議您使用此命令 ID。

   要取代標準 OLE`COleClientItem::CanPaste`來使用 。

- ID_EDIT_PASTE_LINK從當前剪貼簿內容插入連結。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `COleDocument`只是為此命令提供更新命令 UI 處理程式。 如果剪貼簿不包含可連結的 OLE 項/物件,則該命令將被禁用。 您負責為實際命令編寫處理程式以執行實際粘貼。 如果 OLE 應用程式還可以貼上其他格式,則應在檢視或文件中(即命令目標路由`COleDocument`之前的某個位置)中提供您自己的更新命令 UI 處理程式。

   如果選擇實現此命令,我們建議您使用此命令 ID。

   要取代標準 OLE`COleClientItem::CanPasteLink`來使用 。

- ID_EDIT_PASTE_SPECIAL使用選項插入當前剪貼簿內容。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。 MFC 不提供此對話方塊。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_REPEAT重複最後一個操作。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此命令的實現以重複最後一個尋找操作。 使用最後一個查找的私有實現變數。 如果無法嘗試查找,則該命令將禁用。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_REPLACE 開始替換操作,請啟動無模式替換對話方塊。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此命令的實現,該命令調用實現説明器函數`OnEditFindReplace`,以便在私有實現變數中使用和存儲以前的查找/替換設置。 類別`CFindReplaceDialog`用於管理提示使用者的無模式對話框。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_SELECT_ALL 選擇整個文檔。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`提供此命令的實現,該命令選擇文檔中的所有文本。 如果沒有要選擇的文本,則禁用該命令。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_UNDO撤消最後一個操作。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   `CEditView`使用此 指令的`CEdit::Undo`完整 。 如果返回 FALSE,`CEdit::CanUndo`則該命令將禁用。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_EDIT_REDO重做最後一個操作。

   目前沒有此命令的標準實現。 您必須為每個`CView`派生類實現此。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_WINDOW_NEW 在活動文件上打開另一個視窗。

   `CMDIFrameWnd::OnWindowNew`通過使用當前文件的文檔範本創建包含當前文檔的另一個檢視的另一個框架,實現這一強大的功能。

   與大多數多個文檔介面 (MDI) 視窗功能表命令一樣,如果沒有活動的 MDI 子視窗,則禁用該命令。

   不建議自定義此命令處理程式。 如果要提供創建其他檢視或框架視窗的命令,最好創建自己的命令。 可以從複製程式碼`CMDIFrameWnd::OnWindowNew`並將其修改為特定框架並查看您喜歡的類。

- ID_WINDOW_ARRANGE排列 MDI 視窗底部的圖示。

   `CMDIFrameWnd`在實現説明器函數`OnMDIWindowCmd`中實現此標準 MDI 命令。 此幫助程式將命令 ID 映射到 MDI Windows 消息,因此可以共用大量代碼。

   與大多數 MDI 視窗功能表命令一樣,如果沒有活動的 MDI 子視窗,則該命令將禁用。

   不建議自定義此命令處理程式。

- ID_WINDOW_CASCADE級聯視窗,以便它們重疊。

   `CMDIFrameWnd`在實現説明器函數`OnMDIWindowCmd`中實現此標準 MDI 命令。 此幫助程式將命令 ID 映射到 MDI Windows 消息,因此可以共用大量代碼。

   與大多數 MDI 視窗功能表命令一樣,如果沒有活動的 MDI 子視窗,則該命令將禁用。

   不建議自定義此命令處理程式。

- ID_WINDOW_TILE_HORZ水準磁貼視窗。

   此命令在ID_WINDOW_CASCADE中`CMDIFrameWnd`實現,但操作使用不同的 MDI Windows 消息。

   應為應用程式選擇預設磁貼方向。 為此,可以將視窗"Tile"功能表項的ID更改為ID_WINDOW_TILE_HORZ或ID_WINDOW_TILE_VERT。

- ID_WINDOW_TILE_VERT垂直磁貼視窗。

   此命令在ID_WINDOW_CASCADE中`CMDIFrameWnd`實現,但操作使用不同的 MDI Windows 消息。

   應為應用程式選擇預設磁貼方向。 為此,可以將視窗"Tile"功能表項的ID更改為ID_WINDOW_TILE_HORZ或ID_WINDOW_TILE_VERT。

- ID_WINDOW_SPLIT鍵盤介面到拆分器。

   `CView`處理實現的此`CSplitterWnd`命令。 如果檢視是分割器視窗的一部分,則此命令將委派給實現函數`CSplitterWnd::DoKeyboardSplit`。 這將將拆分器置於允許鍵盤使用者拆分或取消拆分拆分視窗的模式。

   如果視圖不在拆分器中,則禁用此命令。

   不建議自定義此命令處理程式。

- ID_APP_ABOUT調用"關於"對話方塊。

   應用程式"關於"框沒有標準實現。 默認 AppWizard 創建的應用程式將為應用程式創建自定義對話方塊類,並將其用作"關於"框。 AppWizard 還將編寫處理此命令並調用對話框的瑣碎命令處理程式。

   您幾乎總是實現此命令。

- ID_APP_EXIT退出應用程式。

   `CWinApp::OnAppExit`通過向應用程式的主視窗發送WM_CLOSE消息來處理此命令。 應用程式的標準關閉(提示臟檔等)由`CFrameWnd`實現處理。

   不建議自定義此命令處理程式。 建議重寫`CWinApp::SaveAllModified``CFrameWnd`或 關閉邏輯。

   如果選擇實現此命令,我們建議您使用此命令 ID。

- ID_HELP_INDEX 清單 從 中提供幫助主題。HLP 檔。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnHelpIndex`通過瑣碎地調用`CWinApp::WinHelp`來處理此命令。

   不建議自定義此命令處理程式。

- ID_HELP_USING 顯示有關如何使用幫助的説明。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnHelpUsing`通過瑣碎地調用`CWinApp::WinHelp`來處理此命令。

   不建議自定義此命令處理程式。

- ID_CONTEXT_HELP進入 SHIFT-F1 説明模式。

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnContextHelp`通過設置説明模式游標、輸入模式迴圈並等待使用者選擇視窗以獲取有關幫助來處理此命令。 有關 MFC 幫助實施的更多資訊[,請參閱技術說明 28。](../mfc/tn028-context-sensitive-help-support.md)

   不建議自定義此命令處理程式。

- ID_HELP 在目前上下文上提供説明

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   `CWinApp::OnHelp`通過獲取當前應用程式上下文的正確説明上下文來處理此命令。 這將處理簡單的 F1 説明、消息框上的説明等。 有關 MFC 幫助實施的更多詳細資訊,請參閱[技術說明 28。](../mfc/tn028-context-sensitive-help-support.md)

   不建議自定義此命令處理程式。

- ID_DEFAULT_HELP 顯示內容的預設說明

    > [!NOTE]
    >  您必須將其連接到`CWinApp`派生類的消息映射才能啟用此功能。

   此指令通常映射到`CWinApp::OnHelpIndex`。

   如果需要默認幫助和説明索引之間的區別,則可以提供不同的命令處理程式。

- ID_NEXT_PANE轉到下一個窗格

   `CView`處理實現的此`CSplitterWnd`命令。 如果檢視是分割器視窗的一部分,則此命令將委派給實現函數`CSplitterWnd::OnNextPaneCmd`。 這將將活動檢視移動到分割器中的下一個窗格。

   如果檢視不在拆分器中,或者沒有下一個窗格可轉到,則禁用此命令。

   不建議自定義此命令處理程式。

- ID_PREV_PANE 移至上一個窗格

   `CView`處理實現的此`CSplitterWnd`命令。 如果檢視是分割器視窗的一部分,則此命令將委派給實現函數`CSplitterWnd::OnNextPaneCmd`。 這將將活動檢視移動到分割器中的上一個窗格。

   如果檢視不在拆分器中,或者沒有要轉到的上一個窗格,則禁用此命令。

   不建議自定義此命令處理程式。

- ID_OLE_INSERT_NEW插入新的 OLE 物件

   目前沒有此命令的標準實現。 您必須為`CView`派生類實現此目的,才能在當前選擇中插入新的 OLE 項/物件。

   所有 OLE 用戶端應用程式都應實現此命令。 使用 OLE 選項的 AppWizard`OnInsertObject`將在檢視類 中創建您必須完成的骨架實現。

   有關此命令的完整實現,請參閱 MFC OLE[範例 OCLIENT](../overview/visual-cpp-samples.md)範例。

- ID_OLE_EDIT_LINKS編輯 OLE 連結

   `COleDocument`使用提供 MFC 的標準 OLE 連結對話框的實現來處理此命令。 此對話框的實現通過`COleLinksDialog`類訪問。 如果當前文檔不包含任何連結,則該命令將禁用。

   不建議自定義此命令處理程式。

- ID_OLE_VERB_FIRST...OLE 動詞的識別碼範圍

   `COleDocument`對於當前選定的 OLE 項/物件支援的謂詞,使用此命令 ID 範圍。 這必須是一個範圍,因為給定的 OLE 項/物件類型可以支援零個或多個自定義謂詞。 在應用程式的功能表中,應該有一個帶有ID_OLE_VERB_FIRST ID 的功能表項。 運行程式時,功能表將使用適當的菜單謂詞描述(或包含許多動詞的彈出式功能表)進行更新。 OLE 選單的管理`AfxOleSetEditMenu`由 處理,由在此命令的更新命令 UI 處理程式中完成。

   在此範圍內,沒有用於處理每個命令 ID 的顯式命令處理程式。 `COleDocument::OnCmdMsg`重寫以捕獲此範圍內的所有命令指示,將它們轉換為零基動詞數位,並啟動該謂詞的伺服器(使用`COleClientItem::DoVerb`)。

   不建議自定義或使用此命令 ID 範圍。

- ID_VIEW_TOOLBAR開啟與關閉工具列

   `CFrameWnd`處理此命令和更新命令 UI 處理程式以切換工具列的可見狀態。 工具列必須是框架的子視窗,其子視窗 ID 為 AFX_IDW_TOOLBAR。 命令處理程序實際上切換工具列視窗的可見性。 `CFrameWnd::RecalcLayout`用於使用處於新狀態的工具列重繪框架視窗。 當工具列可見時,更新命令 UI 處理程式將檢查功能表項。

   不建議自定義此命令處理程式。 如果要添加其他工具列,將希望克隆和修改此命令的命令處理程式和更新命令 UI 處理程式。

- ID_VIEW_STATUS_BAR開啟與關閉狀態列

   此命令在ID_VIEW_TOOLBAR中`CFrameWnd`實現,但使用不同的子視窗 ID (AFX_IDW_STATUS_BAR)。

## <a name="update-only-command-handlers"></a>只更新指令處理程式

多個標準命令指示號用作狀態列中的指示器。 它們使用相同的更新命令 UI 處理機制來在應用程式空閒期間顯示其當前可視狀態。 由於使用者無法選擇它們(即不能推送狀態欄窗格),因此對這些命令的 ON_COMMAND處理程序沒有意義。

- ID_INDICATOR_CAPS :CAP 鎖指示燈。

- ID_INDICATOR_NUM :NUM 鎖定指示器。

- ID_INDICATOR_SCRL : SCRL 鎖定指示燈。

- ID_INDICATOR_KANA : KANA 鎖定指示器(僅適用於日本系統)。

這三個功能都在`CFrameWnd::OnUpdateKeyIndicator`中實現,一個使用命令 ID 映射到相應虛擬密鑰的實現説明程式。 公共實現啟用或禁用(對於禁用的狀態窗格 = 無文本`CCmdUI`), 具體取決於相應的虛擬密鑰當前是否鎖定。

不建議自定義此命令處理程式。

- ID_INDICATOR_EXT : EX"選擇指標"

- ID_INDICATOR_OVR : OVeR 打擊指示器。

- ID_INDICATOR_REC : 重新調整指示器。

目前,這些指標沒有標準實施。

如果您選擇實現這些指標,我們建議您使用這些指標 ID 並保持狀態列中的指標順序(即按此順序排列:EXT、CAP、NUM、SCRL、OVR、REC)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
