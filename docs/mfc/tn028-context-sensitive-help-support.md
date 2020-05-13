---
title: TN028：即時線上說明支援
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370334"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028：即時線上說明支援

此提示描述在 MFC 中指派 [說明] 內容 ID 和其他說明議題的規則。 即時線上說明支援需要可用於 Visual C++ 的說明編譯器。

> [!NOTE]
> 除了使用 WinHelp 實作即時線上說明之外，MFC 也支援使用 HTML [說明]。 有關此支援與 HTML 說明程式的詳細資訊,請參考[HTML 說明:程式中文敏感說明](../mfc/html-help-context-sensitive-help-for-your-programs.md)。

## <a name="types-of-help-supported"></a>支援的說明類型

在 Windows 應用程式實作的兩種即時線上說明類型。 第一，「F1 說明」涉及根據目前作用中物件啟動具適當內容的 WinHelp。 第二是「Shift+ F1」模式。 在此模式中，滑鼠游標會變成說明游標，讓使用者繼續點按物件。 此時，會啟動 WinHelp 以提供使用者按選之物件的說明。

Microsoft Foundation Classes 會實作這兩種形式的說明。 此外，架構支援兩個簡單說明命令、說明索引和使用說明。

## <a name="help-files"></a>說明檔

MFC 採用單一說明檔。 說明檔必須具有與應用程式相同的名稱和路徑。 例如，在中，如果可執行檔是 C:\MyApplication\MyHelp.exe，說明檔必須是 C:\MyApplication\MyHelp.hlp。 通過[CWinApp 類](../mfc/reference/cwinapp-class.md)的*m_pszHelpFilePath*成員變數設置路徑。

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

- [由 CWinApp 實現的ID_HELP_INDEX::在説明索引上](../mfc/reference/cwinapp-class.md#onhelpindex)

- [由 CWinApp 實現的ID_HELP_USING:在説明使用](../mfc/reference/cwinapp-class.md#onhelpusing)

第一個命令顯示應用程式的 [說明] 索引。 第二個命令則顯示有關使用 WinHelp 程式的使用者說明。

## <a name="context-sensitive-help-f1-help"></a>即時線上說明 (F1 說明)

F1 鍵通常透過放置在主視窗的加速器表中的加速器轉換為 ID 為 ID_HELP的命令。 ID_HELP命令也可以由主視窗或對話方塊上 ID 為 ID_HELP的按鈕生成。

無論ID_HELP命令的生成方式如何,它都會作為常規命令進行路由,直到到達命令處理程式。 有關 MFC 命令路由體系結構的詳細資訊,請參閱[技術說明 21](../mfc/tn021-command-and-message-routing.md)。 如果應用程式啟用了説明,[則 cWinApp::onHelp](../mfc/reference/cwinapp-class.md#onhelp)將處理ID_HELP命令。 應用程式物件收到說明訊息，然後適當地路由轉送命令。 這是必要的，因為只靠預設命令路由仍不足以判斷最特定的內容。

`CWinApp::OnHelp` 嘗試依下列順序啟動 WinHelp：

1. 利用說明 ID 檢查作用中 `AfxMessageBox` 呼叫。 如果訊息方塊目前在作用中，WinHelp 會啟動適合該訊息方塊的內容。

1. 將 WM_COMMANDHELP 訊息傳送到使用中視窗。 如果啟動 WinHelp 後該視窗未有回應，就會將相同訊息傳送到該視窗的上階，直到訊息被處理或目前視窗成為最上層視窗。

1. 將 ID_DEFAULT_HELP 命令傳送到主視窗。 這會叫用預設的 [說明]。 這個命令通常會對應到 `CWinApp::OnHelpIndex`。

要全域覆蓋預設 ID 基本值 (例如指令的 0x10000 和對於對話框等資源 0x20000),應用程式應覆蓋[CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp)。

若要覆寫這項功能和判定說明內容的方法，您應該處理 WM_COMMANDHELP 訊息。 您可能會想要提供比架構所提供更具體的 [說明] 路由，因為它的深度只到目前的 MDI 子視窗。 您也會想要提供某特定視窗或對話方塊的更具體說明，或許會以該物件目前的內部狀態或對話方塊內的現用控制項為主。

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP 是一種私用 Windows MFC 訊息，當提出 [說明] 要求時，使用中視窗便會接收到這種訊息。 當視窗收到這個訊息時，可能會以含符合視窗內部狀態的內容來呼叫 `CWinApp::WinHelp`。

*lParam*<br/>
包含目前可用的說明內容。 如果未確定説明上下文,*則 lParam*為零。 的`OnCommandHelp`使用*lParam*中的內容的文字代碼來確定不同的功能,也可以將其傳遞給`CWinApp::WinHelp`。

*wParam*<br/>
未使用且將為零。

如果`OnCommandHelp`函數呼`CWinApp::WinHelp`叫 ,則應傳回**TRUE**。 返回**TRUE**將停止此命令路由到其他類和其他視窗。

## <a name="help-mode-shiftf1-help"></a>說明模式 (Shift+F1 說明)

這是第二種即時線上說明格式。 通常，這種模可藉由按下 SHIFT+F1 或透過功能表和工具列來輸入。 它當成命令來實作 (ID_CONTEXT_HELP)。 當強制回應對話方塊或功能表在作用中時，訊息篩選條件攔截程序不是用來轉譯這個命令，因此，當應用程式在執行主要訊息提取時，這個命令只能供使用者使用 (`CWinApp::Run`)。

在輸入此模式後，[說明] 滑鼠游標會顯示在應用程式的所有區域，即使應用程式通常只會顯示該區域的游標 (例如，視窗周圍的縮放邊框)。 使用者可以使用滑鼠或鍵盤選取命令。 不需執行命令，該命令的 [說明] 就會出現。 此外，使用者可以在畫面上按一下可見的物件 (例如工具列上的按鈕)，然後就會顯示該物件的 [說明]。 此 [說明] 模式由 `CWinApp::OnContextHelp`提供。

在執行這個迴圈的期間，除了存取功能表的按鍵，所有鍵盤輸入都是非現用。 此外，透過 `PreTranslateMessage` 仍然會執行命令轉譯，允許使用者按快速鍵，並取得該命令的說明。

如果`PreTranslateMessage`函數中發生的特定轉換或操作不應在 SHIFT_F1 幫助模式期間發生,則應在執行這些操作`CWinApp`之前檢查 m_bHelpMode*成員。* 在呼叫 `CDialog` 之前，`PreTranslateMessage` 的 `IsDialogMessage` 實作會檢查這部分。 在 SHIFT+F1 模式期間，這會停用非強制回應對話方塊上的「對話方塊巡覽」鍵。 此外，在這個迴圈期間仍會呼叫 `CWinApp::OnIdle`。

如果使用者從功能表選取命令，它會被處理為該命令的說明 (透過 WM_COMMANDHELP，請參閱以下內容)。 如果使用者按一下應用程式視窗的可見區域，便會判斷其是否為非用戶端點按或用戶端點按。 `OnContextHelp` 會自動處理非用戶端點按與用戶端點按的對應。 如果是用戶端點按，接著會將 WM_HELPHITTEST 傳送到被按下的視窗。 如果該視窗傳回非零值，該值便會用做說明的內容。 如果傳回零，`OnContextHelp` 會嘗試父視窗 (若失敗，再嘗試其父代，依此類推)。 如果無法確定說明中, 則預設是向主視窗傳送ID_DEFAULT_HELP命令,主視窗(通常)映射`CWinApp::OnHelpIndex`到 。

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST 是 SHIFT+F1 說明模式期間按下之使用中視窗所接收到的 MFC 私用視窗訊息。 當視窗收到此消息時,它將返回一個**DWORD**幫助 ID 供 WinHelp 使用。

LOWORD(lParam) 包含 X 軸設備座標,其中滑鼠相對於視窗的工作區按一下。

HIWORD(lParam)包含 Y 軸座標。

*wParam*<br/>
未使用且將為零。 如果傳回值為非零，會以該內容呼叫 WinHelp。 如果傳回值為零，會查詢父視窗的說明。

在大部分情況下，您可以應用您可能已經擁有的點擊測試碼。 有關處理WM_HELPHITTEST消息`CToolBar::OnHelpHitTest`的範例,請參閱 的實現(代碼利用了`CControlBar`在中的 按鈕和工具提示中使用的命中測試代碼)。

## <a name="mfc-application-wizard-support-and-makehm"></a>MFC 應用程式精靈支援和 MAKEHM

MFC 應用程式精靈可建立必要的檔案來建置說明檔 (.cnt 和 .hpj 檔)。 其也包含由 Microsoft 說明編譯器接受的預先建置 .rtf 檔。 許多主題都已經完成，但有一些需要針對特定應用程式作修改。

MAKEHM 公用程式支援自動建立「說明對應」檔案。 MAKEHM 公用程式可以將應用程式的 RESOURCE.H 檔案轉譯為說明對應檔。 例如：

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

MAKEHM 的原始碼在 MFC 編程實用程式範例[MAKEHM](../overview/visual-cpp-samples.md)中可用。

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

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
