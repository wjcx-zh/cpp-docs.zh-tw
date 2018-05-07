---
title: TN028： 即時線上說明支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.help
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58caed14e6b7080405cceb30cfb90623d28dc83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn028-context-sensitive-help-support"></a>TN028：即時線上說明支援
此提示描述在 MFC 中指派 [說明] 內容 ID 和其他說明議題的規則。 即時線上說明支援需要可用於 Visual C++ 的說明編譯器。  
  
> [!NOTE]
>  除了使用 WinHelp 實作即時線上說明之外，MFC 也支援使用 HTML [說明]。 如需有關這項支援和 HTML 說明以程式設計的詳細資訊，請參閱[HTML 說明： 程式的即時線上說明](../mfc/html-help-context-sensitive-help-for-your-programs.md)。  
  
## <a name="types-of-help-supported"></a>支援的說明類型  
 在 Windows 應用程式實作的兩種即時線上說明類型。 第一，「F1 說明」涉及根據目前作用中物件啟動具適當內容的 WinHelp。 第二是「Shift+ F1」模式。 在此模式中，滑鼠游標會變成說明游標，讓使用者繼續點按物件。 此時，會啟動 WinHelp 以提供使用者按選之物件的說明。  
  
 Microsoft Foundation Classes 會實作這兩種形式的說明。 此外，架構支援兩個簡單說明命令、說明索引和使用說明。  
  
## <a name="help-files"></a>說明檔  
 MFC 採用單一說明檔。 說明檔必須具有與應用程式相同的名稱和路徑。 例如，在中，如果可執行檔是 C:\MyApplication\MyHelp.exe，說明檔必須是 C:\MyApplication\MyHelp.hlp。 您設定透過路徑`m_pszHelpFilePath`成員變數[CWinApp 類別](../mfc/reference/cwinapp-class.md)。  
  
## <a name="help-context-ranges"></a>說明主題範圍  
 MFC 的預設實作需要程式遵循指派說明主題 ID 的一些規則。 這些規則是一些配置給特定控制項的 ID。 您可以藉由提供各種 [說明] 相關的成員函式的不同實作來覆寫這些規則。  
  
```  
0x00000000 - 0x0000FFFF : user defined  
0x00010000 - 0x0001FFFF : commands (menus/command buttons)  
0x00010000 + ID_  
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)  
0x00020000 - 0x0002FFFF : windows and dialogs  
0x00020000 + IDR_  
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)  
0x00030000 - 0x0003FFFF : error messages (based on error string ID)  
0x00030000 + IDP_  
0x00040000 - 0x0004FFFF : special purpose (non-client areas)  
0x00040000 + HitTest area  
0x00050000 - 0x0005FFFF : controls (those that are not commands)  
0x00040000 + IDW_  
```  
  
## <a name="simple-help-commands"></a>簡單的「Help」命令  
 Microsoft Foundation Classes 實作的兩個簡單 [說明] 命令：  
  
-   實作的 ID_HELP_INDEX [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)  
  
-   實作的 ID_HELP_USING [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)  
  
 第一個命令顯示應用程式的 [說明] 索引。 第二個命令則顯示有關使用 WinHelp 程式的使用者說明。  
  
## <a name="context-sensitive-help-f1-help"></a>即時線上說明 (F1 說明)  
 F1 鍵通常會轉譯成含 `ID_HELP` ID 的命令，方式是將加速器置於主視窗的快速鍵對應表。 `ID_HELP` 命令可能由主視窗或對話方塊上，某個含 `ID_HELP` ID 的按鈕所產生。  
  
 不論 `ID_HELP` 命令如何產生，它會像一般命令一樣路由轉送，直到觸及命令處理常式。 如需 MFC 命令路由架構的詳細資訊，請參閱[技術提示 21](../mfc/tn021-command-and-message-routing.md)。 如果應用程式啟用，[說明]`ID_HELP`命令處理[CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp)。 應用程式物件收到說明訊息，然後適當地路由轉送命令。 這是必要的，因為只靠預設命令路由仍不足以判斷最特定的內容。  
  
 `CWinApp::OnHelp` 嘗試依下列順序啟動 WinHelp：  
  
1.  利用說明 ID 檢查作用中 `AfxMessageBox` 呼叫。 如果訊息方塊目前在作用中，WinHelp 會啟動適合該訊息方塊的內容。  
  
2.  將 WM_COMMANDHELP 訊息傳送到使用中視窗。 如果啟動 WinHelp 後該視窗未有回應，就會將相同訊息傳送到該視窗的上階，直到訊息被處理或目前視窗成為最上層視窗。  
  
3.  將 ID_DEFAULT_HELP 命令傳送到主視窗。 這會叫用預設的 [說明]。 這個命令通常會對應到 `CWinApp::OnHelpIndex`。  
  
 若要全域覆寫預設識別碼基底值 （例如 0x10000 命令和 0x20000 的資源，例如對話方塊），應用程式應該覆寫[CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp)。  
  
 若要覆寫這項功能和判定說明內容的方法，您應該處理 WM_COMMANDHELP 訊息。 您可能會想要提供比架構所提供更具體的 [說明] 路由，因為它的深度只到目前的 MDI 子視窗。 您也會想要提供某特定視窗或對話方塊的更具體說明，或許會以該物件目前的內部狀態或對話方塊內的現用控制項為主。  
  
## <a name="wmcommandhelp"></a>WM_COMMANDHELP  
  
```  
 
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
 
```  
  
 WM_COMMANDHELP 是一種私用 Windows MFC 訊息，當提出 [說明] 要求時，使用中視窗便會接收到這種訊息。 當視窗收到這個訊息時，可能會以含符合視窗內部狀態的內容來呼叫 `CWinApp::WinHelp`。  
  
 `lParam`  
 包含目前可用的說明內容。 如果未判斷出說明內容，`lParam` 便為零。 `OnCommandHelp` 的實作可在 `lParam` 使用內容 ID，以判斷出不同的內容，或可將它傳遞到 `CWinApp::WinHelp`。  
  
 `wParam`  
 未使用且將為零。  
  
 如果 `OnCommandHelp` 函式呼叫 `CWinApp::WinHelp`，則應傳回 `TRUE`。 傳回 `TRUE` 會停止此命令路由至其他類別及其他視窗。  
  
## <a name="help-mode-shiftf1-help"></a>說明模式 (Shift+F1 說明)  
 這是第二種即時線上說明格式。 通常，這種模可藉由按下 SHIFT+F1 或透過功能表和工具列來輸入。 它會實作為命令 (**ID_CONTEXT_HELP**)。 當強制回應對話方塊或功能表在作用中時，訊息篩選條件攔截程序不是用來轉譯這個命令，因此，當應用程式在執行主要訊息提取時，這個命令只能供使用者使用 (`CWinApp::Run`)。  
  
 在輸入此模式後，[說明] 滑鼠游標會顯示在應用程式的所有區域，即使應用程式通常只會顯示該區域的游標 (例如，視窗周圍的縮放邊框)。 使用者可以使用滑鼠或鍵盤選取命令。 不需執行命令，該命令的 [說明] 就會出現。 此外，使用者可以在畫面上按一下可見的物件 (例如工具列上的按鈕)，然後就會顯示該物件的 [說明]。 此 [說明] 模式由 `CWinApp::OnContextHelp`提供。  
  
 在執行這個迴圈的期間，除了存取功能表的按鍵，所有鍵盤輸入都是非現用。 此外，透過 `PreTranslateMessage` 仍然會執行命令轉譯，允許使用者按快速鍵，並取得該命令的說明。  
  
 在 SHIFT+F1 說明模式期間，如果 `PreTranslateMessage` 函式中發生不應該發生的特定轉譯或動作，您應該在執行這些作業前檢查 `m_bHelpMode` 的 `CWinApp` 成員。 在呼叫 `CDialog` 之前，`PreTranslateMessage` 的 `IsDialogMessage` 實作會檢查這部分。 在 SHIFT+F1 模式期間，這會停用非強制回應對話方塊上的「對話方塊巡覽」鍵。 此外，在這個迴圈期間仍會呼叫 `CWinApp::OnIdle`。  
  
 如果使用者從功能表選擇命令，就會處理該命令的說明 (透過**WM_COMMANDHELP**，請參閱下文)。 如果使用者按一下應用程式視窗的可見區域，便會判斷其是否為非用戶端點按或用戶端點按。 `OnContextHelp` 會自動處理非用戶端點按與用戶端點按的對應。 如果用戶端按一下，然後將傳送**WM_HELPHITTEST**已按下的視窗。 如果該視窗傳回非零值，該值便會用做說明的內容。 如果傳回零，`OnContextHelp` 會嘗試父視窗 (若失敗，再嘗試其父代，依此類推)。 如果無法判斷說明內容，預設不會傳送**ID_DEFAULT_HELP**命令到主視窗，接著 （通常） 對應到`CWinApp::OnHelpIndex`。  
  
## <a name="wmhelphittest"></a>WM_HELPHITTEST  
  
```  
 
afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)  
```  
  
 **WM_HELPHITTEST** MFC 私人 windows 訊息接收已按下 SHIFT + F1 說明模式期間，使用中視窗。 當視窗收到這個訊息時，它會傳回 DWORD 說明 ID 供 WinHelp 使用。  
  
 LOWORD (lParam)  
 包含相對於視窗用戶端區域點按滑鼠的 X 軸裝置座標。  
  
 HIWORD(lParam)  
 包含 Y 軸座標。  
  
 `wParam`  
 未使用且將為零。 如果傳回值為非零，會以該內容呼叫 WinHelp。 如果傳回值為零，會查詢父視窗的說明。  
  
 在大部分情況下，您可以應用您可能已經擁有的點擊測試碼。 請參閱實作**Wm_helphittest**處理的範例， **WM_HELPHITTEST**訊息 (程式碼會利用上按鈕和工具提示中的使用的點擊測試程式碼`CControlBar`)。  
  
## <a name="mfc-application-wizard-support-and-makehm"></a>MFC 應用程式精靈支援和 MAKEHM  
 MFC 應用程式精靈可建立必要的檔案來建置說明檔 (.cnt 和 .hpj 檔)。 其也包含由 Microsoft 說明編譯器接受的預先建置 .rtf 檔。 許多主題都已經完成，但有一些需要針對特定應用程式作修改。  
  
 MAKEHM 公用程式支援自動建立「說明對應」檔案。 MAKEHM 公用程式可以將應用程式的 RESOURCE.H 檔案轉譯為說明對應檔。 例如:   
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 將轉譯成：  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 這種格式與說明編譯器的功能相容，可內容 ID (右邊的數字) 與主題名稱 (左邊的符號)。  
  
 MAKEHM 的原始程式碼可在 MFC 程式開發公用程式範例[MAKEHM](../visual-cpp-samples.md)。  
  
## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>執行 MFC 應用程式精靈後加入說明支援  
 建立應用程式之前，將說明加入至您的應用程式的最好方式是，檢查 MFC 應用程式精靈 [進階功能] 頁面的 [即時線上說明] 選項。 如此，MFC 應用程式精靈會自動將必要的訊息對應項目加入至 `CWinApp` 衍生類別以支援 [說明]。  
  
## <a name="help-on-message-boxes"></a>訊息方塊的說明  
 訊息方塊的說明 (有時稱為警示) 可透過 `AfxMessageBox` 函式 (`MessageBox` Windows API 的包裝函式) 來提供相關支援。  
  
 `AfxMessageBox` 有兩種版本，一種與字串 ID 搭配使用，另一種則與字串指標 (`LPCSTR`) 搭配使用：  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```  
  
 這兩種都具有選擇性說明 ID。  
  
 在第一個方塊，nIDHelp 預設為 0，表示此訊息方塊沒有提供說明。 如果使用者按下 F1 的同時，訊息方塊正在使用中，則使用者將無法取得 [說明] (即使應用程式支援 [說明])。 如果需要的不是這個，應該為 nIDHelp 提供說明 ID。  
  
 在第二個方塊，nIDHelp 的預設值為 -1，表示說明 ID 與 nIDPrompt 相同。 [說明] 當然只能在應用程式已啟用說明功能時運作。 如果您不希望訊息方塊有說明支援，則須為 nIDHelp 提供 0。 如果您希望訊息有啟用 [說明]，但想要一個 nIDPrompt 以外的不同說明 ID 時，只需為 nIDHelp 提供一個不同於 nIDPrompt 的正值。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

