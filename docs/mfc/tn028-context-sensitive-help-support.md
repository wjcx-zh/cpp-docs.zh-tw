---
title: "TN028：即時線上說明支援 | Microsoft Docs"
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
  - "vc.help"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "即時線上說明, MFC 應用程式"
  - "資源識別項, 即時線上說明"
  - "TN028"
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN028：即時線上說明支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註在 MFC 描述指派的說明內容 ID 和其他說明問題的規則。  即時線上說明支援需要適用於 Visual C\+\+ 的說明編譯器。  
  
> [!NOTE]
>  除了實作使用 WinHelp 的即時線上說明之外，使用 HTML 的 MFC 支援也說明。  如需這項支援和程式設計的詳細資訊在 HTML 說明，請參閱 [HTML 說明:您的程式的即時線上說明。](../mfc/html-help-context-sensitive-help-for-your-programs.md)。  
  
## 類型的說明支援  
 在 Windows 應用程式實作的即時線上說明的兩種型別。  第一，稱為 F1 說明涉及啟動 WinHelp 與根據目前作用中物件的適當的內容。  第二個是「Shift\+ F1」模式。  在此模式中，滑鼠游標變成說明游標和使用者可按一下物件。  此時， WinHelp 啟動給使用者按一下物件的說明。  
  
 Microsoft Foundation Class 實作說明這兩種形式。  此外，架構支援兩個簡單說明命令，說明索引和使用說明。  
  
## 說明檔  
 Microsoft Foundation Class 假設單一說明檔。  說明檔必須與路徑與應用程式相同。  例如，在中，如果可執行檔是 C:\\MyApplication\\MyHelp.exe 說明檔必須是 C:\\MyApplication\\MyHelp.hlp。  您將路徑透過 [CWinApp Class](../mfc/reference/cwinapp-class.md)的 `m_pszHelpFilePath` 成員變數。  
  
## 說明內容範圍  
 MFC 的預設實作需要有程式遵循對說明內容 ID 的工作的某些規則。  這些規則是 ID 範圍被指派到特定控制項。  您可以提供各種說明相關的成員函式的不同實作覆寫這些規則。  
  
```  
0x00000000 - 0x0000FFFF : user defined  
0x00010000 - 0x0001FFFF : commands (menus/command buttons)  
   0x00010000 + ID_  
   (note: 0x18000-> 0x1FFFF is the practical range since command IDs are >=0x8000)  
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
  
## 簡單的「Help」命令  
 一個或多個 Microsoft Foundation Classes 實作的兩個簡單說明命令:  
  
-   由 [CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)實作的 ID\_HELP\_INDEX  
  
-   由 [CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)實作的 ID\_HELP\_USING  
  
 第一個命令會顯示應用程式的說明索引。  第二部分則示範在使用 WinHelp 程式的使用者說明。  
  
## 即時線上說明\(F1 說明\)。  
 F1 鍵通常會轉譯成命令與 `ID_HELP` ID 加速器置於主視窗的快速鍵對應表。  `ID_HELP` 命令可能會有 `ID_HELP` ID 的按鈕也會在主視窗或對話方塊。  
  
 不論 `ID_HELP` 命令如何產生，它會將當做一般命令，直到到達命令處理常式。  如需 MFC 命令傳送結構的詳細資訊，請參閱 [Technical Note 21](../mfc/tn021-command-and-message-routing.md)。  如果應用程式有說明允許， `ID_HELP` 命令將由 [CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)處理。  應用程式物件收到說明訊息然後適當地傳送命令。  因為預設命令傳送為判斷最特定的內容，而非完整這是必要的。  
  
 `CWinApp::OnHelp` 嘗試啟動會依照下列順序 WinHelp:  
  
1.  現用 `AfxMessageBox` 呼叫的檢查與說明 ID.  如果訊息方塊目前作用中， WinHelp 啟動適當內容到該訊息方塊。  
  
2.  WM\_COMMANDHELP 資訊傳送至使用中視窗。  如果該視窗不會啟動 WinHelp 回應相同的資訊，然後傳送至該視窗的祖系，直到訊息處理或目前視窗是最上層視窗。  
  
3.  ID\_DEFAULT\_HELP 傳送命令到主視窗。  這會叫用預設的說明。  這個命令通常會對應至 `CWinApp::OnHelpIndex`。  
  
 全域覆寫預設 ID 基底值 \(也就是命令的資源的 0x10000 和 0x20000 例如對話方塊\)，應用程式應該覆寫 [CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md)。  
  
 若要覆寫這項功能和說明內容來決定的方法，您應該處理 WM\_COMMANDHELP 訊息。  您的架構可以提供要提供特定的說明路由，，因為它只移至相同深度與目前 MDI 子視窗。  您也可以提供特定的說明為特定視窗或對話方塊，或根據該物件目前的狀態或在對話方塊內的現用控制項。  
  
## WM\_COMMANDHELP  
  
```  
  
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
```  
  
 WM\_COMMANDHELP 是使用中視窗所收到的私用視窗 MFC 訊息，同時協助要求時。  當視窗收到這個訊息時，可能會以符合 Windows 的內部狀態的內容的 `CWinApp::WinHelp` 。  
  
 `lParam`  
 包含目前可用的說明內容。  如果無法判斷，`lParam` 是零說明內容。  `OnCommandHelp` 的實作在 `lParam` 使用內容 ID 識別不同的內容或可以將它加入至 `CWinApp::WinHelp`。  
  
 `wParam`  
 沒有使用和為零。  
  
 如果 `OnCommandHelp` 函式呼叫 `CWinApp::WinHelp`，則應該傳回 `TRUE`。  傳回 `TRUE` 停止此命令傳送至其他類別和連結至其他視窗。  
  
## 說明模式 \(Shift\+F1 說明\)  
 這是即時線上說明第二個表單。  通常，這個方式輸入傳入 SHIFT\+F1 或透過功能表和工具列。  它會實作為命令 \(**ID\_CONTEXT\_HELP**\)。  訊息篩選條件攔截不是用來轉譯這個命令時，強制回應對話方塊或功能表在作用中時，因此這個命令只提供給使用者，當應用程式執行的主要訊息幫浦 \(`CWinApp::Run`\)。  
  
 在輸入模式之後，說明滑鼠游標會顯示在所有應用程式區域，，即使應用程式通常會顯示該區域的游標 \(例如在視窗周圍之縮放邊框\)。  使用者可以使用滑鼠或鍵盤選取命令。  而不是執行命令，該命令的說明主題隨即出現。  此外，使用者可以在螢幕上按一下一個可見的物件，例如在工具列上的按鈕，然後說明該物件會顯示。  `CWinApp::OnContextHelp`提供說明模式。  
  
 在這個迴圈執行期間，所有輸入為非現用，除了存取功能表的索引鍵。  此外，命令轉譯透過 `PreTranslateMessage` 仍然會允許使用者按快速鍵和取得該命令的說明。  
  
 如果有特定轉譯或發生在 SHIFT\+F1 說明模式期間，不應該發生的 `PreTranslateMessage` 的動作生效，您應該在執行這些作業前檢查 `CWinApp` 的 `m_bHelpMode` 成員。  `PreTranslateMessage` \(例如 `CDialog` 實作在呼叫 `IsDialogMessage`之前檢查此，。  在 SHIFT\+F1 模式下，這會停用對話方塊在非強制回應對話方塊的巡覽」索引鍵。  此外，在這個迴圈期間， `CWinApp::OnIdle` 仍會呼叫。  
  
 如果使用者從功能表選取命令，它被視為該命令的說明 \(透過 **WM\_COMMANDHELP**，請參閱以下內容\)。  如果使用者按一下應用程式視窗的可見區域，判斷中是否為非用戶端按一下或用戶端按一下。  `OnContextHelp` 控制項對應至用戶端的非用戶端按一下自動按一下。  如果是用戶端按一下，然後傳送到 **WM\_HELPHITTEST** 按下的視窗。  如果該視窗會傳回非零的值，該值會用來做為內容的說明。  如果傳回零， `OnContextHelp` 表示也會嘗試搜尋父視窗 \(和失敗時，它的父代，依此類推\)。  如果說明內容無法判斷的，預設是傳送 **ID\_DEFAULT\_HELP** 命令到主視窗， \(\) 通常會對應至 `CWinApp::OnHelpIndex`。  
  
## WM\_HELPHITTEST  
  
```  
  
afx_msg LRESULT CWnd::OnHelpHitTest(  
WPARAM, LPARAM lParam)  
```  
  
 **WM\_HELPHITTEST** 是 SHIFT\+F1 說明模式期間按下的使用中視窗所收到的 MFC 私用 Windows 訊息。  當視窗收到這個訊息時，它會傳回 DWORD 說明 ID 供 WinHelp 使用。  
  
 LOWORD \(lParam\)  
 包含滑鼠按一下相對於視窗的工作區的 X 軸裝置座標。  
  
 HIWORD \(lParam\)  
 包含 Y 軸座標。  
  
 `wParam`  
 沒有被使用且為零。  如果傳回值為零， WinHelp 呼叫該內容。  如果傳回值為零，父視窗為說明查詢。  
  
 在大部分情況下，您可以備份您可能已經具有的點擊測試程式碼。  為處理 **WM\_HELPHITTEST** 訊息的範例參閱 **CToolBar::OnHelpHitTest** 的實作 \(程式碼支援在按鈕上和工具提示的點擊測試程式碼在 `CControlBar`\)。  
  
## MFC 應用程式精靈支援和 MAKEHM  
 MFC 應用程式精靈建立必要的檔案建立說明檔 \(.cnt 和 .hpj 檔\)。  它也包含由 Microsoft 說明編譯器接受的預先建置 .rtf 檔。  許多主題完成的，不過，有些可能需要針對特定應用程式被修改。  
  
 「說明對應」檔案的自動建立由呼叫 MAKEHM 公用程式的支援。  MAKEHM 公用程式可以轉譯應用程式的 RESOURCE.H 檔案為說明對應檔。  例如：  
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 要轉譯成:  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 這個格式與說明編譯器的功能相容，將內容 ID \(右邊的數字\) 與主題名稱 \(左邊的符號\)。  
  
 MAKEHM 的原始程式碼可在程式設計公用程式 [MAKEHM](../top/visual-cpp-samples.md)範例的 MFC。  
  
## 將說明支援在執行 MFC 應用程式精靈之後  
 最好的方式將說明加入至您的應用程式會檢查在 MFC 應用程式精靈的進階功能 Page 「即時線上說明」選項在建立應用程式。  以這種方式 MFC 應用程式精靈會自動將必要的訊息對應項目加入至 `CWinApp`\-對支援說明的衍生類別。  
  
## 在訊息方塊的說明  
 在訊息方塊的說明 \(有時稱為警示\) 透過 `AfxMessageBox` 函式， `MessageBox` 在 Windows 應用程式開發介面的包裝函式支援。  
  
 有 `AfxMessageBox`，則為與字串 ID 的和類別的兩個版本以與指標字串 \(`LPCSTR`\):  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText, UINT nType, UINT nIDHelp);  
int AFXAPI AfxMessageBox(UINT nIDPrompt, UINT nType, UINT nIDHelp);  
```  
  
 在這兩種情況下，具有選擇性說明 ID.  
  
 在第一個方塊，預設 nIDHelp 的為 0，表示此訊息方塊的說明。  如果使用者按下 F1 時，例如訊息方塊作用中時，使用者將無法取得說明 \(即使應用程式支援說明\)。  如果這不是適當的，應該為 nIDHelp 提供說明 ID。  
  
 在第二個方塊，預設值 nIDHelp 的為 \-1，表示說明 ID 與 nIDPrompt。  說明將運作，只有在應用程式是說明允許，當然\)。  您應該為 nIDHelp 提供 0，如果您希望訊息方塊沒有說明支援。  如果您要 nIDPrompt 要訊息是說明允許，不過，需要不同的說明 ID，為 nIDHelp 提供正值與該 nIDPrompt 不同。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)