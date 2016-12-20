---
title: "CWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CWindow"
  - "ATL::CWindow"
  - "CWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindow class"
ms.assetid: fefa00c8-f053-4bcf-87bc-dc84f5386683
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會管理  視窗的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CWindow  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWindow::CWindow](../Topic/CWindow::CWindow.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWindow::ArrangeIconicWindows](../Topic/CWindow::ArrangeIconicWindows.md)|讓所有最小化的子視窗。|  
|[CWindow::Attach](../Topic/CWindow::Attach.md)|附加至 `CWindow` 視窗物件。|  
|[CWindow::BeginPaint](../Topic/CWindow::BeginPaint.md)|準備用於繪製的視窗。|  
|[CWindow::BringWindowToTop](../Topic/CWindow::BringWindowToTop.md)|的疊置順序的最頂端視窗。|  
|[CWindow::CenterWindow](../Topic/CWindow::CenterWindow.md)|將視窗對指定的視窗。|  
|[CWindow::ChangeClipboardChain](../Topic/CWindow::ChangeClipboardChain.md)|從剪貼簿中來檢查程序鏈結中移除視窗。|  
|[CWindow::CheckDlgButton](../Topic/CWindow::CheckDlgButton.md)|變更指定之按鈕的選取狀態。|  
|[CWindow::CheckRadioButton](../Topic/CWindow::CheckRadioButton.md)|檢查指定的選項按鈕。|  
|[CWindow::ChildWindowFromPoint](../Topic/CWindow::ChildWindowFromPoint.md)|擷取包含指定點的子視窗。|  
|[CWindow::ChildWindowFromPointEx](../Topic/CWindow::ChildWindowFromPointEx.md)|擷取包含指定點的子視窗的特定型別。|  
|[CWindow::ClientToScreen](../Topic/CWindow::ClientToScreen.md)|篩選的座標轉換為工作區座標。|  
|[CWindow::Create](../Topic/CWindow::Create.md)|建立視窗。|  
|[CWindow::CreateCaret](../Topic/CWindow::CreateCaret.md)|建立系統游標新圖形。|  
|[CWindow::CreateGrayCaret](../Topic/CWindow::CreateGrayCaret.md)|建立系統游標的灰色矩形。|  
|[CWindow::CreateSolidCaret](../Topic/CWindow::CreateSolidCaret.md)|建立系統游標的實心矩形。|  
|[CWindow::DeferWindowPos](../Topic/CWindow::DeferWindowPos.md)|更新指定之視窗的指定多個視窗位置結構。|  
|[CWindow::DestroyWindow](../Topic/CWindow::DestroyWindow.md)|終結視窗與 `CWindow` 物件。|  
|[CWindow::Detach](../Topic/CWindow::Detach.md)|中斷連結 `CWindow` 物件的視窗。|  
|[CWindow::DlgDirList](../Topic/CWindow::DlgDirList.md)|以符合指定的路徑或檔名之所有檔案的名稱則填入清單方塊。|  
|[CWindow::DlgDirListComboBox](../Topic/CWindow::DlgDirListComboBox.md)|以符合指定的路徑或檔名之所有檔案的名稱填入下拉式方塊。|  
|[CWindow::DlgDirSelect](../Topic/CWindow::DlgDirSelect.md)|擷取從清單方塊中目前的選取範圍。|  
|[CWindow::DlgDirSelectComboBox](../Topic/CWindow::DlgDirSelectComboBox.md)|擷取從下拉式方塊中目前的選取範圍。|  
|[CWindow::DragAcceptFiles](../Topic/CWindow::DragAcceptFiles.md)|暫存器視窗是否接受拖曳的檔案。|  
|[CWindow::DrawMenuBar](../Topic/CWindow::DrawMenuBar.md)|重新繪製視窗的功能表列。|  
|[CWindow::EnableScrollBar](../Topic/CWindow::EnableScrollBar.md)|啟用或停用捲軸箭號。|  
|[CWindow::EnableWindow](../Topic/CWindow::EnableWindow.md)|啟用或停用項目。|  
|[CWindow::EndPaint](../Topic/CWindow::EndPaint.md)|標記繪製的。|  
|[CWindow::FlashWindow](../Topic/CWindow::FlashWindow.md)|一次閃爍視窗。|  
|[CWindow::GetClientRect](../Topic/CWindow::GetClientRect.md)|擷取工作區座標。|  
|[CWindow::GetDC](../Topic/CWindow::GetDC.md)|擷取工作區的裝置內容。|  
|[CWindow::GetDCEx](../Topic/CWindow::GetDCEx.md)|擷取工作區的裝置內容並允許裁剪選項。|  
|[CWindow::GetDescendantWindow](../Topic/CWindow::GetDescendantWindow.md)|擷取指定的子視窗。|  
|[CWindow::GetDlgControl](../Topic/CWindow::GetDlgControl.md)|擷取針對指定之控制項的介面。|  
|[CWindow::GetDlgCtrlID](../Topic/CWindow::GetDlgCtrlID.md)|擷取視窗的識別項 \(只適用於子視窗\)。|  
|[CWindow::GetDlgHost](../Topic/CWindow::GetDlgHost.md)|擷取指向介面加入至 ATL 控制項裝載容器。|  
|[CWindow::GetDlgItem](../Topic/CWindow::GetDlgItem.md)|擷取指定之的子視窗。|  
|[CWindow::GetDlgItemInt](../Topic/CWindow::GetDlgItemInt.md)|轉譯控制項的文字為整數。|  
|[CWindow::GetDlgItemText](../Topic/CWindow::GetDlgItemText.md)|擷取控制項的文字。|  
|[CWindow::GetExStyle](../Topic/CWindow::GetExStyle.md)|擷取延伸視窗樣式。|  
|[CWindow::GetFont](../Topic/CWindow::GetFont.md)|擷取視窗目前的字型。|  
|[CWindow::GetHotKey](../Topic/CWindow::GetHotKey.md)|判斷快速鍵與視窗。|  
|[CWindow::GetIcon](../Topic/CWindow::GetIcon.md)|擷取視窗的大圖示或小圖示。|  
|[CWindow::GetLastActivePopup](../Topic/CWindow::GetLastActivePopup.md)|擷取最近使用的快顯視窗。|  
|[CWindow::GetMenu](../Topic/CWindow::GetMenu.md)|擷取 Windows 功能表中的。|  
|[CWindow::GetNextDlgGroupItem](../Topic/CWindow::GetNextDlgGroupItem.md)|在控制項群組中擷取上一個或下一個控制項。|  
|[CWindow::GetNextDlgTabItem](../Topic/CWindow::GetNextDlgTabItem.md)|擷取與上一個或下一個控制項的 **WS\_TABSTOP** 樣式。|  
|[CWindow::GetParent](../Topic/CWindow::GetParent.md)|擷取直接父視窗。|  
|[CWindow::GetScrollInfo](../Topic/CWindow::GetScrollInfo.md)|擷取捲軸的參數。|  
|[CWindow::GetScrollPos](../Topic/CWindow::GetScrollPos.md)|擷取捲動方塊的位置。|  
|[CWindow::GetScrollRange](../Topic/CWindow::GetScrollRange.md)|擷取捲軸範圍。|  
|[CWindow::GetStyle](../Topic/CWindow::GetStyle.md)|擷取視窗樣式。|  
|[CWindow::GetSystemMenu](../Topic/CWindow::GetSystemMenu.md)|建立系統功能表的複本進行修改。|  
|[CWindow::GetTopLevelParent](../Topic/CWindow::GetTopLevelParent.md)|擷取最上層父視窗或主控視窗。|  
|[CWindow::GetTopLevelWindow](../Topic/CWindow::GetTopLevelWindow.md)|擷取最上層主控視窗。|  
|[CWindow::GetTopWindow](../Topic/CWindow::GetTopWindow.md)|擷取最上層子視窗。|  
|[CWindow::GetUpdateRect](../Topic/CWindow::GetUpdateRect.md)|擷取完全圍住更新區域最小矩形的座標。|  
|[CWindow::GetUpdateRgn](../Topic/CWindow::GetUpdateRgn.md)|擷取更新區域並將它複製到指定的區域。|  
|[CWindow::GetWindow](../Topic/CWindow::GetWindow.md)|擷取指定的視窗。|  
|[CWindow::GetWindowContextHelpId](../Topic/CWindow::GetWindowContextHelpId.md)|擷取視窗的說明主題代碼。|  
|[CWindow::GetWindowDC](../Topic/CWindow::GetWindowDC.md)|擷取整個視窗的裝置內容。|  
|[CWindow::GetWindowLong](../Topic/CWindow::GetWindowLong.md)|擷取 32 位元值中的指定位移至額外的視窗記憶體中。|  
|[CWindow::GetWindowLongPtr](../Topic/CWindow::GetWindowLongPtr.md)|擷取所指定之視窗的相關資訊，包括值中的指定位移至額外的視窗記憶體中。|  
|[CWindow::GetWindowPlacement](../Topic/CWindow::GetWindowPlacement.md)|擷取顯示狀態和位置。|  
|[CWindow::GetWindowProcessID](../Topic/CWindow::GetWindowProcessID.md)|擷取建立 Windows 處理序的識別項。|  
|[CWindow::GetWindowRect](../Topic/CWindow::GetWindowRect.md)|擷取視窗週框 \(Bounding 維度。|  
|[CWindow::GetWindowRgn](../Topic/CWindow::GetWindowRgn.md)|取得視窗的視窗區域的複本。|  
|[CWindow::GetWindowText](../Topic/CWindow::GetWindowText.md)|擷取視窗中的文字。|  
|[CWindow::GetWindowTextLength](../Topic/CWindow::GetWindowTextLength.md)|擷取視窗的文字長度。|  
|[CWindow::GetWindowThreadID](../Topic/CWindow::GetWindowThreadID.md)|擷取針對指定之視窗執行緒的識別項。|  
|[CWindow::GetWindowWord](../Topic/CWindow::GetWindowWord.md)|擷取 16 位元值中的指定位移至額外的視窗記憶體中。|  
|[CWindow::GotoDlgCtrl](../Topic/CWindow::GotoDlgCtrl.md)|設定鍵盤焦點設定在  對話方塊中的控制項。|  
|[CWindow::HideCaret](../Topic/CWindow::HideCaret.md)|隱藏系統游標。|  
|[CWindow::HiliteMenuItem](../Topic/CWindow::HiliteMenuItem.md)|從取得焦點或最上層的功能表項目移除反白顯示。|  
|[CWindow::Invalidate](../Topic/CWindow::Invalidate.md)|使整個工作區。|  
|[CWindow::InvalidateRect](../Topic/CWindow::InvalidateRect.md)|null 在指定矩形內的工作區。|  
|[CWindow::InvalidateRgn](../Topic/CWindow::InvalidateRgn.md)|null 在指定區域內的工作區。|  
|[CWindow::IsChild](../Topic/CWindow::IsChild.md)|判斷指定的視窗是否為子視窗。|  
|[CWindow::IsDialogMessage](../Topic/CWindow::IsDialogMessage.md)|判斷訊息是否為指定之對話方塊中使用。|  
|[CWindow::IsDlgButtonChecked](../Topic/CWindow::IsDlgButtonChecked.md)|決定按鈕的選取狀態。|  
|[CWindow::IsIconic](../Topic/CWindow::IsIconic.md)|判斷視窗最小化。|  
|[CWindow::IsParentDialog](../Topic/CWindow::IsParentDialog.md)|判斷控制項的父視窗是否為對話方塊視窗。|  
|[CWindow::IsWindow](../Topic/CWindow::IsWindow.md)|判斷指定的視窗控制代碼是否識別現有視窗。|  
|[CWindow::IsWindowEnabled](../Topic/CWindow::IsWindowEnabled.md)|決定  視窗是否為輸入啟用。|  
|[CWindow::IsWindowUnicode](../Topic/CWindow::IsWindowUnicode.md)|判斷指定的視窗是否為原生 Unicode 視窗。|  
|[CWindow::IsWindowVisible](../Topic/CWindow::IsWindowVisible.md)|決定視窗的可視性狀態。|  
|[CWindow::IsZoomed](../Topic/CWindow::IsZoomed.md)|決定  視窗是否為最大化。|  
|[CWindow::KillTimer](../Topic/CWindow::KillTimer.md)|會終結計時器事件。|  
|[CWindow::LockWindowUpdate](../Topic/CWindow::LockWindowUpdate.md)|停用或啟用  視窗中的繪圖。|  
|[CWindow::MapWindowPoints](../Topic/CWindow::MapWindowPoints.md)|將一組從視窗的座標空間轉換為另一個視窗座標空間。|  
|[CWindow::MessageBox](../Topic/CWindow::MessageBox.md)|顯示訊息方塊。|  
|[CWindow::ModifyStyle](../Topic/CWindow::ModifyStyle.md)|修改視窗樣式。|  
|[CWindow::ModifyStyleEx](../Topic/CWindow::ModifyStyleEx.md)|修改延伸視窗樣式。|  
|[CWindow::MoveWindow](../Topic/CWindow::MoveWindow.md)|變更視窗的大小和位置。|  
|[CWindow::NextDlgCtrl](../Topic/CWindow::NextDlgCtrl.md)|設定鍵盤焦點設定在  對話方塊中的下一個控制項。|  
|[CWindow::OpenClipboard](../Topic/CWindow::OpenClipboard.md)|開啟 \[剪貼簿\]。|  
|[CWindow::PostMessage](../Topic/CWindow::PostMessage.md)|在訊息佇列將訊息與建立 Windows Form 的執行緒。  沒有任何等候的執行緒傳回處理訊息。|  
|[CWindow::PrevDlgCtrl](../Topic/CWindow::PrevDlgCtrl.md)|設定鍵盤焦點設定在  對話方塊中的上一個控制項。|  
|[CWindow::Print](../Topic/CWindow::Print.md)|該要求的視窗在指定之裝置內容中繪製。|  
|[CWindow::PrintClient](../Topic/CWindow::PrintClient.md)|該要求的視窗工作區 \(Client Area\) 中指定之裝置內容中繪製。|  
|[CWindow::RedrawWindow](../Topic/CWindow::RedrawWindow.md)|更新指定的矩形或本機工作區中。|  
|[CWindow::ReleaseDC](../Topic/CWindow::ReleaseDC.md)|釋放裝置內容。|  
|[CWindow::ResizeClient](../Topic/CWindow::ResizeClient.md)|調整視窗大小。|  
|[CWindow::ScreenToClient](../Topic/CWindow::ScreenToClient.md)|轉換為工作區座標的螢幕座標。|  
|[CWindow::ScrollWindow](../Topic/CWindow::ScrollWindow.md)|移動指定的工作區。|  
|[CWindow::ScrollWindowEx](../Topic/CWindow::ScrollWindowEx.md)|移動與其他功能之指定的工作區。|  
|[CWindow::SendDlgItemMessage](../Topic/CWindow::SendDlgItemMessage.md)|傳送訊息至控制項。|  
|[CWindow::SendMessage](../Topic/CWindow::SendMessage.md)|將訊息傳送至視窗，而且不會傳回，直到的視窗程序來處理訊息。|  
|[CWindow::SendMessageToDescendants](../Topic/CWindow::SendMessageToDescendants.md)|將訊息傳送至指定的子視窗。|  
|[CWindow::SendNotifyMessage](../Topic/CWindow::SendNotifyMessage.md)|將訊息傳送至視窗。  如果視窗由呼叫執行緒建立， `SendNotifyMessage` 不傳回，直到的視窗程序來處理訊息。  否則，它會立即傳回。|  
|[CWindow::SetActiveWindow](../Topic/CWindow::SetActiveWindow.md)|啟動視窗。|  
|[CWindow::SetCapture](../Topic/CWindow::SetCapture.md)|傳送所輸入的任何後續滑鼠至視窗。|  
|[CWindow::SetClipboardViewer](../Topic/CWindow::SetClipboardViewer.md)|將視窗至剪貼簿來檢查程序鏈結。|  
|[CWindow::SetDlgCtrlID](../Topic/CWindow::SetDlgCtrlID.md)|變更視窗的識別項。|  
|[CWindow::SetDlgItemInt](../Topic/CWindow::SetDlgItemInt.md)|變更控制項的文字轉換成整數值的字串表示。|  
|[CWindow::SetDlgItemText](../Topic/CWindow::SetDlgItemText.md)|變更控制項的文字。|  
|[CWindow::SetFocus](../Topic/CWindow::SetFocus.md)|將輸入焦點至視窗。|  
|[CWindow::SetFont](../Topic/CWindow::SetFont.md)|變更視窗的目前字型。|  
|[CWindow::SetHotKey](../Topic/CWindow::SetHotKey.md)|關聯熱鍵使用視窗。|  
|[CWindow::SetIcon](../Topic/CWindow::SetIcon.md)|變更視窗的大圖示或小圖示。|  
|[CWindow::SetMenu](../Topic/CWindow::SetMenu.md)|變更視窗的目前功能表。|  
|[CWindow::SetParent](../Topic/CWindow::SetParent.md)|變更父視窗。|  
|[CWindow::SetRedraw](../Topic/CWindow::SetRedraw.md)|設定或清除重繪旗標。|  
|[CWindow::SetScrollInfo](../Topic/CWindow::SetScrollInfo.md)|設定捲軸的參數。|  
|[CWindow::SetScrollPos](../Topic/CWindow::SetScrollPos.md)|變更捲動方塊的位置。|  
|[CWindow::SetScrollRange](../Topic/CWindow::SetScrollRange.md)|變更捲軸範圍。|  
|[CWindow::SetTimer](../Topic/CWindow::SetTimer.md)|建立計時器事件。|  
|[CWindow::SetWindowContextHelpId](../Topic/CWindow::SetWindowContextHelpId.md)|設定視窗的說明主題代碼。|  
|[CWindow::SetWindowLong](../Topic/CWindow::SetWindowLong.md)|將 32 位元的值 \(在指定的位移額外的視窗記憶體中。|  
|[CWindow::SetWindowLongPtr](../Topic/CWindow::SetWindowLongPtr.md)|變更指定之視窗的屬性，以及設定此值在其他 Windows 記憶體的指定位移。|  
|[CWindow::SetWindowPlacement](../Topic/CWindow::SetWindowPlacement.md)|設定顯示狀態和位置。|  
|[CWindow::SetWindowPos](../Topic/CWindow::SetWindowPos.md)|設定的大小、位置和疊置順序。|  
|[CWindow::SetWindowRgn](../Topic/CWindow::SetWindowRgn.md)|設定視窗的視窗區域。|  
|[CWindow::SetWindowText](../Topic/CWindow::SetWindowText.md)|變更視窗中的文字。|  
|[CWindow::SetWindowWord](../Topic/CWindow::SetWindowWord.md)|將 16 位元的值 \(在指定的位移額外的視窗記憶體中。|  
|[CWindow::ShowCaret](../Topic/CWindow::ShowCaret.md)|顯示系統游標。|  
|[CWindow::ShowOwnedPopups](../Topic/CWindow::ShowOwnedPopups.md)|顯示或隱藏視窗主控的快顯視窗。|  
|[CWindow::ShowScrollBar](../Topic/CWindow::ShowScrollBar.md)|顯示或隱藏每個捲軸。|  
|[CWindow::ShowWindow](../Topic/CWindow::ShowWindow.md)|設定視窗的顯示狀態。|  
|[CWindow::ShowWindowAsync](../Topic/CWindow::ShowWindowAsync.md)|設定不同的執行緒上建立之視窗的顯示狀態。|  
|[CWindow::UpdateWindow](../Topic/CWindow::UpdateWindow.md)|更新工作區。|  
|[CWindow::ValidateRect](../Topic/CWindow::ValidateRect.md)|驗證指定之矩形內的工作區。|  
|[CWindow::ValidateRgn](../Topic/CWindow::ValidateRgn.md)|驗證在指定區域內的工作區。|  
|[CWindow::WinHelp](../Topic/CWindow::WinHelp.md)|啟動 Windows 說明。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CWindow::operator HWND](../Topic/CWindow::operator%20HWND.md)|將轉換成 `HWND`的 `CWindow` 物件。|  
|[CWindow::operator \=](../Topic/CWindow::operator%20=.md)|`HWND` `CWindow` 指派至物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWindow::m\_hWnd](../Topic/CWindow::m_hWnd.md)|視窗的控制代碼與 `CWindow` 物件。|  
|[CWindow::rcDefault](../Topic/CWindow::rcDefault.md)|包含預設視窗大小。|  
  
## 備註  
 `CWindow` 作業在 ATL 的視窗提供基底功能。  許多 `CWindow` 方法會包裝方法的其中一個 Win32 API 函式。  例如，比較 `CWindow::ShowWindow` 和 `ShowWindow`的原型:  
  
|CWindow 方法|Win32 函式。|  
|----------------|---------------|  
|**BOOL ShowWindow\( int**  `nCmdShow`\);|**BOOL ShowWindow\( HWND**  `hWnd` **, int**  `nCmdShow`\);|  
  
 `CWindow::ShowWindow` 傳遞 `CWindow::m_hWnd` 呼叫 Win32 函式 `ShowWindow` 做為第一個參數。  直接包裝 Win32 函式的每 `CWindow` 方法傳遞 `m_hWnd` 成員;因此，許多 `CWindow` 文件將指引您到 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  並非所有視窗相關的 Win32 函式。 `CWindow`並不是每一個 `CWindow` 方法包裝包裝 Win32 函式。  
  
 `CWindow::m_hWnd` 儲存識別一個視窗的 `HWND` 。  `HWND` 附加至物件，當您:  
  
-   指定 `HWND` 在 `CWindow` 的建構函式。  
  
-   請呼叫 `CWindow::Attach`。  
  
-   使用 `CWindow` 的 **operator \=**。  
  
-   建立或子類別會使用 `CWindow`從衍生的類別之一的視窗:  
  
     [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 可讓您建立新的 Windows 或子類別現有視窗。  
  
     [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 實作在另一個物件內所包含的視窗。  您可以建立新的 Windows 或子類別現有視窗。  
  
     [CDialogImpl](../../atl/reference/cdialogimpl-class.md) 允許您建立強制回應或非強制回應對話方塊。  
  
 如需視窗的詳細資訊，請參閱 [視窗](http://msdn.microsoft.com/library/windows/desktop/ms632595) 和後續的主題。 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  如需使用  視窗的詳細資訊，請參閱 ATL 本文 [ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)