---
title: "TN022：標準命令實作 | Microsoft Docs"
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
  - "vc.commands"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令, 標準"
  - "ID_APP_ABOUT 命令"
  - "ID_APP_EXIT 命令"
  - "ID_CONTEXT_HELP 命令"
  - "ID_DEFAULT_HELP 命令"
  - "ID_EDIT_CLEAR 命令"
  - "ID_EDIT_CLEAR_ALL 命令"
  - "ID_EDIT_COPY 命令"
  - "ID_EDIT_CUT 命令"
  - "ID_EDIT_FIND 命令"
  - "ID_EDIT_PASTE 命令"
  - "ID_EDIT_PASTE_LINK 命令"
  - "ID_EDIT_PASTE_SPECIAL 命令"
  - "ID_EDIT_REDO 命令"
  - "ID_EDIT_REPEAT 命令"
  - "ID_EDIT_REPLACE 命令"
  - "ID_EDIT_SELECT_ALL 命令"
  - "ID_EDIT_UNDO 命令"
  - "ID_FILE_CLOSE 命令"
  - "ID_FILE_NEW 命令"
  - "ID_FILE_OPEN 命令"
  - "ID_FILE_PAGE_SETUP 命令"
  - "ID_FILE_PRINT 命令"
  - "ID_FILE_PRINT_PREVIEW 命令"
  - "ID_FILE_PRINT_SETUP 命令"
  - "ID_FILE_SAVE 命令"
  - "ID_FILE_SAVE_AS 命令"
  - "ID_FILE_SAVE_COPY_AS 命令"
  - "ID_FILE_UPDATE 命令"
  - "ID_HELP 命令"
  - "ID_HELP_INDEX 命令"
  - "ID_HELP_USING 命令"
  - "ID_INDICATOR_CAPS 命令"
  - "ID_INDICATOR_EXT 命令"
  - "ID_INDICATOR_KANA 命令"
  - "ID_INDICATOR_NUM 命令"
  - "ID_INDICATOR_OVR 命令"
  - "ID_INDICATOR_REC 命令"
  - "ID_INDICATOR_SCRL 命令"
  - "ID_NEXT_PANE 命令"
  - "ID_OLE_EDIT_LINKS 命令"
  - "ID_OLE_INSERT_NEW 命令"
  - "ID_OLE_VERB_FIRST 命令"
  - "ID_PREV_PANE 命令"
  - "ID_VIEW_STATUS_BAR 命令"
  - "ID_VIEW_TOOLBAR 命令"
  - "ID_WINDOW_ARRANGE 命令"
  - "ID_WINDOW_CASCADE 命令"
  - "ID_WINDOW_NEW 命令"
  - "ID_WINDOW_SPLIT 命令"
  - "ID_WINDOW_TILE_HORZ 命令"
  - "ID_WINDOW_TILE_VERT 命令"
  - "標準命令"
  - "TN022"
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN022：標準命令實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個摘要說明 MFC 2.0 所提供的標準命令實作。  因為它描述用來實作許多標準命令的機制，請參閱 [Technical Note 21](../mfc/tn021-command-and-message-routing.md) 。  
  
 這說明假設擁有 MFC 架構、API 和一般程式設計實務的知識。  會述及已記載以及未記載的「實作」API 。  這不是開始學習如何以 MFC 的功能編程的地方。  參考 Visual C\+\+ 一般詳細資訊以及與文件之 API 的詳細資料。  
  
## 問題  
 MFC 會在標頭檔 AFXRES.H 定義許多標準命令 ID。  框架支援這些命令變更。  了解架構類別在哪以及如何處理這些命令的方式不僅會顯示您架構如何在內部運作，且提供關於如何自訂標準實作並教您實作自己的命令處理常式的一些技術的有用資訊。  
  
## 這個技術的內容  
 每個命令 ID 在兩個部分說明:  
  
-   標題: 命令 ID 的符號名稱，例如 \( **ID\_FILE\_SAVE**\) 後面跟著命令的用途 \(例如， 「儲存目前檔案」\) ，以冒號分隔。  
  
-   一或多個段落中描述哪些類別實作命令，以及預設的實作  
  
 大部分的預設命令實作與事先設定框架的基底類別訊息對應。  一些命令實作需要在您的衍生類別明確連接。  這些會描述在「摘要」下。  如果您在 AppWizard 選取正確的選項，產生基本架構應用程式的這些預設處理常式會為您連接。  
  
## 命名規範  
 標準命令後面接著我們建議您盡可能使用的簡單的命名慣例。  大部分的標準命令位於應用程式的功能表列的標準位置。  命令的符號名稱開頭為「標準快顯功能表名稱」後面接著 ID\_，後面接著功能表項目名稱。  符號名稱為大寫與底線斷字。  對於沒有標準的命令功能表項目命名，邏輯命令命令名稱定義為開頭為「ID\_」\(例如， **ID\_NEXT\_PANE**\)。  
  
 我們使用前置詞「ID\_」值表示繫結至功能表項目，工具列按鈕或其他命令使用者介面物件的命令。  處理「ID\_」命令的命令處理常式應該使用 `ON_COMMAND` ，而 MFC 的 `ON_UPDATE_COMMAND_UI` 機制命令結構。  
  
 我們建議您針對未遵循命令結構並需要功能表特定程式碼啟用和停用的功能表項目使用標準「IDM\_」前置詞。  當然功能表特定命令的數量應該不多，因為跟著 MFC 命令結構不僅可讓命令處理常式更強大 \(因為它們與工具列一起使用\)，但可讓命令處理常式程式碼重複使用。  
  
## ID 範圍  
 如需詳細資訊請參閱 [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) 中 MFC 中使用的 ID 範圍。  
  
 MFC 標準命令在範圍 0xE000 至 0xEFFF。  因為它們可能會在程式庫的未來的版本中變更，不要依賴這些 ID 的特定值。  
  
 您的應用程式的命令應該定義其介於 0x8000 到 0xDFFF。  
  
## 標準命令 ID  
 對於每個命令 ID，您可以在檔案 PROMPTS.RC 找到的標準訊息提示的字串。  這個功能表的提示字串 ID 必須是相同的命令 ID 的。  
  
-   ID\_FILE\_NEW 建立新\/空白文件。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     `CWinApp::OnFileNew` 根據應用程式的資料範本數目以不同方法實作這個命令。  如果只有一個 `CDocTemplate`， `CWinApp::OnFileNew` 會建立該型別的新文件，以及適當的框架和檢視類別。  
  
     如果有多個 `CDocTemplate`， `CWinApp::OnFileNew` 將提示讓使用者選擇使用哪些資料型別的對話方塊 \(**AFX\_IDD\_NEWTYPEDLG**\) 供使用者選取。  選取的 `CDocTemplate` 用來建立文件。  
  
     `ID_FILE_NEW` 中的一般自訂用以提供不同且更圖形化選擇的資料型別。  在這種情況可以實作自己的 **CMyApp::OnFileNew** 並置於訊息對應檔案中而不是 `CWinApp::OnFileNew`。  不需要呼叫基底類別實作。  
  
     `ID_FILE_NEW` 的另一種常見的自訂是針對每個型別的文件提供不同的命令。  此時您應該定義新的命令 ID，例如 ID\_FILE\_NEW\_CHART 和 ID\_FILE\_NEW\_SHEET。  
  
-   ID\_FILE\_OPEN 開啟現有的文件。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     `CWinApp::OnFileOpen` 有呼叫 **CWinApp::DoPromptFileName** 的簡單實作後面接著 `CWinApp::OpenDocumentFile` 與要開啟的檔案或路徑名稱。  `CWinApp` 實作常式 **DoPromptFileName** 提出標準 FileOpen 對話方塊和以目前文件範本取得的副檔名填充它。  
  
     `ID_FILE_OPEN` 的一般自訂是自訂 FileOpen 對話方塊或加入其他檔案篩選條件。  自訂這個的建議方法為用自己的 FileOpen 對話方塊取代預設實作，並以檔案或路徑名稱呼叫 `CWinApp::OpenDocumentFile` 。  不需要呼叫基底類別。  
  
-   ID\_FILE\_CLOSE 關閉目前開啟的文件。  
  
     **CDocument::OnFileClose** 呼叫 `CDocument::SaveModified` 提示使用者如果已修改的儲存文件，接著呼叫 `OnCloseDocument`。  所有關閉的邏輯，包括終結文件，在 `OnCloseDocument` 常式完成。  
  
    > [!NOTE]
    >  **ID\_FILE\_CLOSE** 與 `WM_CLOSE` 訊息或 **SC\_CLOSE** 系統命令傳送到文件框架視窗行為不同。  如果這是顯示文件的最後的框架視窗，關閉視窗會關閉文件。  以 **ID\_FILE\_CLOSE** 關閉文件不僅會關閉文件，還會停止所有顯示文件的框架視窗。  
  
-   ID\_FILE\_SAVE 儲存目前的文件。  
  
     實作使用在 **OnFileSave** 和 **OnFileSaveAs**使用的 Helper 常式 **CDocument::DoSave** 。  如果您儲存之前尚未儲存的文件 \(它沒有路徑名稱，在 FileNew 情況下\) 或儲存從唯讀資料讀取的檔案， **OnFileSave** 邏輯會如同 **ID\_FILE\_SAVE\_AS** 命令並要求使用者提供新的檔案名稱。  開啟檔案來進行儲存實際的流程透過虛擬函式 `OnSaveDocument`完成。  
  
     有兩個自訂 **ID\_FILE\_SAVE** 的原因。  對於未儲存的文件，則簡單地從使用者介面移除 **ID\_FILE\_SAVE** 功能表項目和工具列按鈕。  請確定您不會變更您的文件 \(絕不會呼叫 `CDocument::SetModifiedFlag`\)，而且架構不會造成儲存文件。  對於儲存文件在磁碟檔以外其他位置，定義該作業的新命令。  
  
     在 `COleServerDoc`的情況下， **ID\_FILE\_SAVE** 為檔案儲存為文件 \(一般\) 和檔案更新使用 \(為嵌入文件\)。  
  
     如果您的文件資料儲存在各自的磁片檔案中，但是您不想要使用預設 **CDocument** 序列化實作，您應該覆寫 `CDocument::OnSaveDocument` 而非 **OnFileSave**。  
  
-   ID\_FILE\_SAVE\_AS 儲存目前文件是存放在不同的檔案名稱下。  
  
     **CDocument::OnFileSaveAs** 實作使用和 **OnFileSave** 相同的 **CDocument::DoSave** Helper 常式。  如果文件在儲存前沒有檔案名稱， **OnFileSaveAs** 命令與 **ID\_FILE\_SAVE** 動作相同。  **COleServerDoc::OnFileSaveAs** 實作儲存一般資料檔案或儲存表示 OLE 物件內嵌在其他應用程式做為個別檔案的伺服器資料的邏輯。  
  
     如果您自訂 **ID\_FILE\_SAVE**邏輯，您可能會想要以相同的方式自訂 **ID\_FILE\_SAVE\_AS** 不然另存新檔作業不可套用至文件。  如果不需要，您可以從您的功能表列移除功能表項目。  
  
-   ID\_FILE\_SAVE\_COPY\_AS 以新的名稱儲存目前文件的副本。  
  
     **COleServerDoc::OnFileSaveCopyAs** 實作非常類似於 **CDocument::OnFileSaveAs**，不過，文件物件沒有在儲存後對基礎檔案附加。  也就是說，如果記憶體中的文件在保存之前「已修改」，仍然為「已修改」。  此外，這個命令對文件或標題的作用中的路徑名稱無效果。  
  
-   ID\_FILE\_UPDATE 告知容器儲存嵌入文件。  
  
     `COleServerDoc::OnUpdateDocument` 實作單純通知容器應該保存內嵌。  容器會呼叫適當的 OLE API 提供儲存內嵌物件。  
  
-   ID\_FILE\_PAGE\_SETUP 叫用特定的版面設定\/設定對話方塊。  
  
     尚未有這個對話方塊的標準，因此，架構沒有這個命令的預設實作。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_FILE\_PRINT\_SETUP 叫用標準列印設定對話方塊。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     這個命令叫用標準列印設定對話方塊，可讓使用者至少對這份文件或至多對所有文件自訂於此應用程式的印表機和列印設定。  您必須使用控制台變更整個系統的預設印表機設定。  
  
     `CWinApp::OnFilePrintSetup` 會建立 `CPrintDialog` 物件和呼叫 **CWinApp::DoPrintDialog** 實作函式的簡單實作。  這個設定應用程式的預設印表機印表機設置。  
  
     對自訂這個命令的一般需要為允許每個文件的印表機設定，當儲存時應該與文件一同儲存。  若要做到這點應該加入訊息對應處理常式至您建立 `CPrintDialog` 物件的 **CDocument** 類別    以適當的印表機屬性 \(通常為 **hDevMode** 和 **hDevNames**\) 初始化，呼叫 **CPrintDialog::DoModal** 並儲存變更的印表機設定。  對於強固的實作，您應該參閱 **CWinApp::DoPrintDialog** 的實作來偵測錯誤和 **CWinApp::UpdatePrinterSelection** 處理合理的預設和追蹤全系統印表機變更。  
  
-   ID\_FILE\_PRINT 目前文件的標準列印  
  
    > [!NOTE]
    >  您必須連接至您的 `CView` 衍生類別以啟用這項功能的訊息對應。  
  
     這個命令列印目前的文件，或更加正確地，開始列印處理序，這會叫用標準列印對話方塊並執行列印引擎。  
  
     **CView::OnFilePrint** 實作此命令和主要列印迴圈。  它會呼叫虛擬 `CView::OnPreparePrinting` 以列印對話方塊提示使用者。  然後準備輸出 DC 到印表機，引發列印進度對話方塊 \(**AFX\_IDD\_PRINTDLG**\)，並傳送 `StartDoc` 逸出至印表機。  **CView::OnFilePrint** 也包含主版頁面導向列印迴圈。  對於每個頁面，它會呼叫虛擬 `CView::OnPrepareDC` 加上 `StartPage` 逸出和對該頁面呼叫實際 `CView::OnPrint` 。  完成時，呼叫虛擬 `CView::OnEndPrinting` 和關閉列印進度對話方塊。  
  
     MFC 列印結構是設計來掛勾列印和預覽列印的許多不同的方式。  您通常會發現各種 `CView` 可覆寫的函式用於所有頁面導向的列印工作。  只在使用印表機對非頁面放置輸出的應用程式案例中，會發現需要取代 **ID\_FILE\_PRINT** 的實作。  
  
-   ID\_FILE\_PRINT\_PREVIEW 進入目前文件的預覽列印模式。  
  
    > [!NOTE]
    >  您必須連接至您的 `CView` 衍生類別以啟用這項功能的訊息對應。  
  
     **CView::OnFilePrintPreview** 呼叫文件的 Helper 函式 **CView::DoPrintPreview** 啟動預覽列印模式。  正如同 **OnFilePrint** 是列印迴圈的主要引擎，**CView::DoPrintPreview** 是預覽列印迴圈的主要引擎。  
  
     預覽列印作業可以以各種方式自訂，透過傳遞不同參數至 **DoPrintPreview** 來進行。  請參閱 [Technical Note 30](../mfc/tn030-customizing-printing-and-print-preview.md)，討論特定預覽列印詳細資料以及如何自訂。  
  
-   命令 ID 的**ID\_FILE\_MRU\_FILE1**…**FILE16**  MRU `list` 檔案的範圍。  
  
     **CWinApp::OnUpdateRecentFileMenu** 是 `ON_UPDATE_COMMAND_UI` 機制的更進階使用方式之一的更新命令 UI 處理常式。  在您的功能表資源，您不只需要以 ID **ID\_FILE\_MRU\_FILE1** 定義單一功能表項目。  功能表項目維持最初停用。  
  
     當 MRU 清單成長時，多個功能表項目加入至清單。  標準 `CWinApp` 實作為四個最近使用的檔案的標準限制的預設。  您也可以使用更大或更小值的 `CWinApp::LoadStdProfileSettings` 變更預設值。  MRU 清單在應用程式的 .INI 檔儲存。  如果呼叫 `LoadStdProfileSettings` 並當應用程式結束時儲存，清單在您的應用程式的 `InitInstance` 函式中列出。  MRU 更新命令 UI 處理常式也會在文件功能表轉換成絕對路徑顯示的相對路徑。  
  
     **CWinApp::OnOpenRecentFile** 是執行實際命令的 `ON_COMMAND` 處理常式。  它會從 MRU 清單取得檔案名稱並呼叫 `CWinApp::OpenDocumentFile`，它完成開啟檔案並更新 MRU 清單中的所有工作。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_EDIT\_CLEAR 清除目前的選取範圍  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     使用 `CEdit::Clear`，`CEditView` 提供這個命令的實作。  如果目前沒有選取範圍，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_CLEAR\_ALL 清除整個文件。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  如需範例實作參閱 MFC 教學課程 [Scribble](../top/visual-cpp-samples.md) 範例。  
  
-   ID\_EDIT\_COPY 將目前選取的範圍複製到剪貼簿。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，使用 `CEdit::Copy` 以 CF\_TEXT 複製目前選取的文字複製到剪貼簿。  如果目前沒有選取範圍，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_CUT 剪下目前選取範圍並放入剪貼簿。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，使用 `CEdit::Cut` 以 CF\_TEXT 剪下目前選取的文字複製到剪貼簿。  如果目前沒有選取範圍，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_FIND 開始尋找作業，則引發非強制回應的尋找對話方塊。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，它會呼叫實作 Helper 函式 **OnEditFindReplace** 以使用並儲存先前尋找\/取代在私用實作變數的設定。  `CFindReplaceDialog` 類別用於處理提示使用者的非強制回應對話方塊。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_PASTE 插入目前的剪貼簿內容。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，使用 `CEdit::Paste` 複製目前剪貼簿資料取代選取的文字。  如果剪貼簿上沒有 **CF\_TEXT**，命令停用。  
  
     **COleClientDoc** 只為這個命令提供更新命令 UI 處理常式。  如果剪貼簿不包含可內嵌的 OLE 項目\/物件，命令將會停用。  您必須負責撰寫處理常式實際命令才能進行實際貼上。  如果您的 OLE 應用程式也可以貼上其他格式，就應該提供您的檢視或文件的更新命令 UI 處理常式 \(在命令目標路由中 **COleClientDoc** 之前的任何地方\)。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
     對於取代標準 OLE 實作，請使用 `COleClientItem::CanPaste`。  
  
-   ID\_EDIT\_PASTE\_LINK 從目前的剪貼簿內容插入連結。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `COleDocument` 只為這個命令提供更新命令 UI 處理常式。  如果剪貼簿不包含可連結的 OLE 項目\/物件，命令將會停用。  您必須負責撰寫處理常式實際命令才能進行實際貼上。  如果您的 OLE 應用程式也可以貼上其他格式，就應該提供您的檢視或文件的更新命令 UI 處理常式 \(在命令目標路由中 `COleDocument` 之前的任何地方\)。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
     對於取代標準 OLE 實作，請使用 `COleClientItem::CanPasteLink`。  
  
-   ID\_EDIT\_PASTE\_SPECIAL 插入目前的剪貼簿內容加上選項。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  MFC 不提供這個對話方塊。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_REPEAT 重複最後一個作業。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作重複最後尋找作業。  使用最後尋找的私用實作變數。  如果尋找嘗試失敗，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_REPLACE 開始取代作業，開啟非強制回應取代對話方塊。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，它會呼叫實作 Helper 函式 **OnEditFindReplace** 以使用並儲存先前尋找\/取代在私用實作變數的設定。  `CFindReplaceDialog` 類別用於處理提示使用者的非強制回應對話方塊。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_SELECT\_ALL 選取整個文件。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     `CEditView` 提供這個命令的實作，選取文件中的所有文字。  如果沒有選取文字，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_UNDO 取消上一項作業。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     使用 `CEdit::Undo`，`CEditView` 提供這個命令的實作。  如果 `CEdit::CanUndo` 傳回 false，命令會停用。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_EDIT\_REDO 復原上一個作業。  
  
     目前沒有這個命令的標準實作。  您必須實作每個 `CView`的衍生類別。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_WINDOW\_NEW 開啟現用文件的另一個視窗。  
  
     **CMDIFrameWnd::OnWindowNew** 使用目前文件的文件範本建立包含目前文件的另一個檢視的另一個框架實作這項強大功能。  
  
     像大部分的多文件介面 \(MDI\) 視窗功能表命令，如果沒有現用 MDI 子視窗，命令會停用。  
  
     不建議自訂這個命令處理常式。  如果您希望提供建立其他檢視或框架視窗的命令，您可能發明您的命令會更好。  您可以從 **CMDIFrameWnd::OnWindowNew** 複製程式碼並以您的偏好修改成特定架構和檢視類別。  
  
-   ID\_WINDOW\_ARRANGE 排列會出現在 MDI 視窗底端的圖示。  
  
     `CMDIFrameWnd` 在實作 Helper 函式 **OnMDIWindowCmd** 實作這個標準 MDI 命令。  這個 Helper 將命令 ID 對應至 MDI 視窗訊息，並可以共用許多程式碼。  
  
     與大多數 MDI 視窗功能表命令相同，如果沒有現用 MDI 子視窗，命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_WINDOW\_CASCADE 層疊視窗，使它們重疊。  
  
     `CMDIFrameWnd` 在實作 Helper 函式 **OnMDIWindowCmd** 實作這個標準 MDI 命令。  這個 Helper 將命令 ID 對應至 MDI 視窗訊息，並可以共用許多程式碼。  
  
     與大多數 MDI 視窗功能表命令相同，如果沒有現用 MDI 子視窗，命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_WINDOW\_TILE\_HORZ 水平並排顯示視窗。  
  
     這個命令在 `CMDIFrameWnd` 實作如 **ID\_WINDOW\_CASCADE**，不過，不同的 MDI 視窗訊息用於此作業。  
  
     您應該挑選應用程式預設的並排方向。  您可以變更 Windows 「並排」顯示功能表項目的 ID 達成 **ID\_WINDOW\_TILE\_HORZ** 或 **ID\_WINDOW\_TILE\_VERT**。  
  
-   ID\_WINDOW\_TILE\_VERT 垂直並排顯示視窗。  
  
     這個命令在 `CMDIFrameWnd` 實作如 **ID\_WINDOW\_CASCADE**，不過，不同的 MDI 視窗訊息用於此作業。  
  
     您應該挑選應用程式預設的並排方向。  您可以變更 Windows 「並排」顯示功能表項目的 ID 達成 **ID\_WINDOW\_TILE\_HORZ** 或 **ID\_WINDOW\_TILE\_VERT**。  
  
-   ID\_WINDOW\_SPLIT 分隔器的鍵盤介面。  
  
     `CView` 為  `CSplitterWnd` 實作處理這個命令。  如果檢視是分隔視窗的一部分，這個命令會委派給實作函式 `CSplitterWnd::DoKeyboardSplit`。  這會將分隔器切換到允許鍵盤使用者分割或取消分割分隔視窗的模式。  
  
     如果檢視不在分隔器，這個命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_APP\_ABOUT 叫用關於對話方塊。  
  
     沒有應用程式的標準以實作關於對話方塊。  預設 AppWizard 建立的應用程式將建置應用程式的自訂對話方塊類別並將它當做您的方塊。  AppWizard 也會寫入處理這個命令並叫用對話方塊的一般命令處理常式。  
  
     您幾乎一定會實作這個命令。  
  
-   ID\_APP\_EXIT 結束應用程式。  
  
     **CWinApp::OnAppExit** 要經由傳送的 `WM_CLOSE` 訊息處理到應用程式的主視窗處理這個命令。  標準關閉應用程式 \(變更檔案的提示等等\) 由 `CFrameWnd` 實作來處理。  
  
     不建議自訂這個命令處理常式。  建議覆寫 `CWinApp::SaveAllModified` 或 `CFrameWnd` 關閉邏輯。  
  
     如果您選擇實作這個命令，我們建議您使用這個命令 ID.  
  
-   ID\_HELP\_INDEX 從 .HLP 檔案列出說明主題。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     傳遞`CWinApp::OnHelpIndex` 時不能呼叫 `CWinApp::WinHelp`處理這個命令。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_HELP\_USING 顯示關於如何使用說明。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     傳遞`CWinApp::OnHelpUsing` 時不能呼叫 `CWinApp::WinHelp`處理這個命令。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_CONTEXT\_HELP 進入 SHIFT\-F1 說明模式。  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     `CWinApp::OnContextHelp` 以設定說明模式游標，輸入強制回應迴圈和等候使用者選取視窗處理這個命令取得說明。  如需 MFC 說明實作的詳細資訊，請參閱 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md)。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_HELP 給目前內容的說明  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     透過`CWinApp::OnHelp` 取得目前應用程式內容的說明內容處理這個命令。  這處理簡單的 F1 說明，訊息方塊的說明等等。  如需 MFC 說明實作的詳細資訊，請參閱 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md)。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_DEFAULT\_HELP 顯示預設內容的說明  
  
    > [!NOTE]
    >  您必須連接至您的 `CWinApp` 衍生類別以啟用這項功能的訊息對應。  
  
     這個命令通常會對應至 `CWinApp::OnHelpIndex`。  
  
     如果需要與預設說明及說明索引之間有差異，可以提供不同的命令處理常式。  
  
-   ID\_NEXT\_PANE 移至下一個窗格  
  
     `CView` 為  `CSplitterWnd` 實作處理這個命令。  如果檢視是分隔視窗的一部分，這個命令會委派給實作函式 **CSplitterWnd::OnNextPaneCmd**。  這會移動現用檢視表到分隔器的下一個窗格。  
  
     如果檢視不在分隔器或沒有下一個窗格可去，這個命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_PREV\_PANE 移至上一個窗格  
  
     `CView` 為  `CSplitterWnd` 實作處理這個命令。  如果檢視是分隔視窗的一部分，這個命令會委派給實作函式 **CSplitterWnd::OnNextPaneCmd**。  這會移動現用檢視表到分隔器的前一個窗格。  
  
     如果檢視不在分隔器或沒有前一個窗格可去，這個命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_OLE\_INSERT\_NEW 插入新的 OLE 物件。  
  
     目前沒有這個命令的標準實作。  您必須實作這個給自己的 `CView` 的衍生類別以插入新的 OLE 項目\/物件至目前的選取範圍。  
  
     所有 OLE 用戶端應用程式應該實作這個命令。  AppWizard，與 OLE 選項，在您的檢視類別將建立需要完成的 **OnInsertObject** 的基本架構實作。  
  
     參閱 MFC OLE 範例 [OCLIENT](../top/visual-cpp-samples.md) 範例為這個命令的完整實作。  
  
-   ID\_OLE\_EDIT\_LINKS 編輯 OLE 連結。  
  
     `COleDocument` 使用 MFC 提供的標準 OLE 連結對話方塊的實作處理這個命令。  這個對話方塊的實作透過 `COleLinksDialog` 類別來存取。  如果目前文件不包含任何連結，命令會停用。  
  
     不建議自訂這個命令處理常式。  
  
-   ID\_OLE\_VERB\_FIRST...LAST OLE 動詞命令的一個 ID 範圍  
  
     `COleDocument` 為目前選取的 OLE 項目\/物件支援的動詞命令使用這個命令 ID 範圍。  這必須是範圍，因為指定之 OLE 項目\/物件型別可以支援零或多個自訂動詞命令。  在應用程式的功能表，您應該要有 ID 為 **ID\_OLE\_VERB\_FIRST**的功能表項目。  當程式執行時，功能表會以適當的動詞命令描述更新 \(或有許多動詞命令的快顯功能表\)。  OLE 功能表的管理由 `AfxOleSetEditMenu`處理，在這個命令的更新命令 UI 處理常式。  
  
     沒有一個明確的命令處理常式處理在範圍內的每一個命令 ID。  **COleDocument::OnCmdMsg** 被覆寫以截獲範圍中所有命令 ID，將它們變更為以零起始的動作數目和啟動該動詞命令的伺服器 \(使用 `COleClientItem::DoVerb`\)。  
  
     不建議使用自訂或在其他用途使用這個命令 ID 範圍。  
  
-   ID\_VIEW\_TOOLBAR 切換工具列  
  
     `CFrameWnd` 處理這個命令和更新命令 UI 處理常式切換工具列的可見狀態。  工具列必須是有 `AFX_IDW_TOOLBAR`子視窗 ID 的框架的子視窗。  命令處理常式實際切換工具列工具視窗的可見度。  `CFrameWnd::RecalcLayout` 用來重新繪製有工具列的框架視窗至其新的狀態。  表示工具列為可見時，更新命令 UI 處理常式檢查目前功能表項目。  
  
     不建議自訂這個命令處理常式。  如果您要加入額外的工具列，您會想要複製和修改這個命令的命令處理常式和更新命令 UI 處理常式。  
  
-   ID\_VIEW\_STATUS\_BAR 切換狀態列  
  
     這個命令在 `CFrameWnd` 實作如 **ID\_VIEW\_TOOLBAR**，不同的是，使用不同的子視窗 ID \(**AFX\_IDW\_STATUS\_BAR**\)。  
  
## 更新命令處理常式  
 許多標準命令 ID 做為狀態列的指示器。  在應用程式閒置時間，這些使用同一個更新命令 UI 處理機制來顯示其目前的可見狀態。  由於無法由使用者選擇 \(即您無法推入狀態列窗格\)，讓這些命令 ID 擁有 `ON_COMMAND` 處理常式變的沒有意義。  
  
-   **ID\_INDICATOR\_CAPS** :CAP LOCK 指示器。  
  
-   **ID\_INDICATOR\_NUM** :NUM LOCK 指示器。  
  
-   **ID\_INDICATOR\_SCRL** :SCRL LOCK 指示器。  
  
-   **ID\_INDICATOR\_KANA** :假名鎖定指示器 \(僅適用於日文系統\)。  
  
 這三個全部在 **CFrameWnd::OnUpdateKeyIndicator** 實做，使用命令 ID 對應到適當的虛擬按鍵的 Helper 實作。  一般實作啟用或停用 \(停用狀態窗格 \= 沒有文字\) `CCmdUI` 物件根據適當的虛擬按鍵是否為已鎖定。  
  
 不建議自訂這個命令處理常式。  
  
-   **ID\_INDICATOR\_EXT : EXT** 關閉選取指示器。  
  
-   **ID\_INDICATOR\_OVR : OV**e**R** 鍵擊指示器。  
  
-   **ID\_INDICATOR\_REC : REC** ording 指示器。  
  
 目前沒有這些指示器的標準實作。  
  
 如果您選擇實作這些指示器，我們建議您在狀態列使用這些指示器 ID 和維護指示器的定序 \(即順序如下:EXT，CAP，NUM，SCRL，OVR，REC\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)