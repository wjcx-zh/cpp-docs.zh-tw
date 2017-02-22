---
title: "CWnd 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 類別"
  - "window objects [C++]"
  - "windows [C++]"
ms.assetid: 49a832ee-bc34-4126-88b3-bc1d9974f6c4
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CWnd 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 MFC 程式庫中所有視窗類別的基本功能。  
  
## 語法  
  
```  
class CWnd : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWnd::CWnd](../Topic/CWnd::CWnd.md)|建構 `CWnd` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWnd::accDoDefaultAction](../Topic/CWnd::accDoDefaultAction.md)|由架構呼叫以執行物件的預設動作。|  
|[CWnd::accHitTest](../Topic/CWnd::accHitTest.md)|由架構呼叫以擷取畫面中給定點的子項目或子物件。|  
|[CWnd::accLocation](../Topic/CWnd::accLocation.md)|由架構呼叫以擷取指定物件目前畫面的位置。|  
|[CWnd::accNavigate](../Topic/CWnd::accNavigate.md)|由架構呼叫以便於周遊容器內的另一使用者介面項目並擷取物件 \(如果可能\)。|  
|[CWnd::accSelect](../Topic/CWnd::accSelect.md)|由架構呼叫以修改選取或移動指定物件的鍵盤焦點。|  
|[CWnd::AnimateWindow](../Topic/CWnd::AnimateWindow.md)|建立相關聯的視窗物件的動畫。|  
|[CWnd::ArrangeIconicWindows](../Topic/CWnd::ArrangeIconicWindows.md)|排列所有最小化 \(圖示\) 子視窗。|  
|[CWnd::Attach](../Topic/CWnd::Attach.md)|將 Windows 控制代碼附加至 `CWnd` 物件。|  
|[CWnd::BeginModalState](../Topic/CWnd::BeginModalState.md)|呼叫此成員函式以製作框架視窗強制回應。|  
|[CWnd::BeginPaint](../Topic/CWnd::BeginPaint.md)|準備 `CWnd` 進行繪製。|  
|[CWnd::BindDefaultProperty](../Topic/CWnd::BindDefaultProperty.md)|將呼叫物件的預設簡單繫結屬性 \(在類型程式庫中標示\)，繫結至資料來源控制項相關聯的游標。|  
|[CWnd::BindProperty](../Topic/CWnd::BindProperty.md)|將資料繫結控制項上的游標繫結屬性繫結至資料來源控制項，並註冊該關聯性與 MFC 繫結管理員。|  
|[CWnd::BringWindowToTop](../Topic/CWnd::BringWindowToTop.md)|將 `CWnd` 帶到重疊視窗堆疊的最上層。|  
|[CWnd::CalcWindowRect](../Topic/CWnd::CalcWindowRect.md)|呼叫可從用戶端矩形計算視窗矩形。|  
|[CWnd::CancelToolTips](../Topic/CWnd::CancelToolTips.md)|停用工具提示控制項。|  
|[CWnd::CenterWindow](../Topic/CWnd::CenterWindow.md)|將相對於其父系的視窗置中。|  
|[CWnd::ChangeClipboardChain](../Topic/CWnd::ChangeClipboardChain.md)|從剪貼簿檢視器的鏈結中移除 `CWnd`。|  
|[CWnd::CheckDlgButton](../Topic/CWnd::CheckDlgButton.md)|在按鈕控制項旁放置核取記號，或從中移除核取記號。|  
|[CWnd::CheckRadioButton](../Topic/CWnd::CheckRadioButton.md)|檢查指定的選項按鈕，及移除指定的按鈕群組中所有其他選項按鈕的核取記號。|  
|[CWnd::ChildWindowFromPoint](../Topic/CWnd::ChildWindowFromPoint.md)|判斷 \(如果有的話\) 是否有子視窗包含指定的點。|  
|[CWnd::ClientToScreen](../Topic/CWnd::ClientToScreen.md)|將畫面上指定的點或矩形的用戶端座標，轉換為螢幕座標。|  
|[CWnd::CloseWindow](../Topic/CWnd::CloseWindow.md)|將視窗最小化。|  
|[CWnd::ContinueModal](../Topic/CWnd::ContinueModal.md)|繼續視窗的強制回應狀態。|  
|[CWnd::Create](../Topic/CWnd::Create.md)|建立並初始化 `CWnd` 物件相關聯的子視窗。|  
|[CWnd::CreateAccessibleProxy](../Topic/CWnd::CreateAccessibleProxy.md)|建立指定物件的 Active Accessibility Proxy。|  
|[CWnd::CreateCaret](../Topic/CWnd::CreateCaret.md)|建立系統游標的新形狀，並取得插入號的擁有權。|  
|[CWnd::CreateControl](../Topic/CWnd::CreateControl.md)|建立將由 `CWnd` 物件在 MFC 程式中表示的 ActiveX 控制項。|  
|[CWnd::CreateEx](../Topic/CWnd::CreateEx.md)|建立 Windows 重疊、快顯視窗或子視窗，並將其附加至 `CWnd` 物件。|  
|[CWnd::CreateGrayCaret](../Topic/CWnd::CreateGrayCaret.md)|建立系統游標的灰色區塊，並取得插入號的擁有權。|  
|[CWnd::CreateSolidCaret](../Topic/CWnd::CreateSolidCaret.md)|建立系統游標的實心區塊，並取得插入號的擁有權。|  
|[CWnd::DeleteTempMap](../Topic/CWnd::DeleteTempMap.md)|由 `CWinApp` 閒置時間處理常式自動呼叫，並刪除 `FromHandle` 建立的任何暫存 `CWnd` 物件。|  
|[CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md)|終結附加的 Windowd 視窗。|  
|[CWnd::Detach](../Topic/CWnd::Detach.md)|從 `CWnd` 物件卸離 Windows 控制代碼，並傳回控制代碼。|  
|[CWnd::DlgDirList](../Topic/CWnd::DlgDirList.md)|使用檔案或目錄清單填入清單方塊。|  
|[CWnd::DlgDirListComboBox](../Topic/CWnd::DlgDirListComboBox.md)|使用檔案或目錄清單來填入下拉式方塊的清單方塊。|  
|[CWnd::DlgDirSelect](../Topic/CWnd::DlgDirSelect.md)|從清單方塊擷取目前的選取範圍。|  
|[CWnd::DlgDirSelectComboBox](../Topic/CWnd::DlgDirSelectComboBox.md)|從下拉式方塊的清單方塊中擷取目前的選取範圍。|  
|[CWnd::DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md)|指出視窗將接受拖曳的檔案。|  
|[CWnd::DragDetect](../Topic/CWnd::DragDetect.md)|擷取滑鼠並追蹤其移動，直到使用者放開左側按鈕、按下 ESC 鍵，或將滑鼠移到指定點周圍的拖曳矩形外。|  
|[CWnd::DrawAnimatedRects](../Topic/CWnd::DrawAnimatedRects.md)|繪製框線矩形，並以動畫效果呈現它來指出圖示的開頭，或最小化或最大化視窗。|  
|[CWnd::DrawCaption](../Topic/CWnd::DrawCaption.md)|繪製標題。|  
|[CWnd::DrawMenuBar](../Topic/CWnd::DrawMenuBar.md)|重新繪製功能表列。|  
|[CWnd::EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md)|啟用使用者定義的 `Active Accessibility` 函式。|  
|[CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md)|可在使用者調整視窗大小時，動態調整子視窗的位置與大小。|  
|[CWnd::EnableD2DSupport](../Topic/CWnd::EnableD2DSupport.md)|啟用或停用視窗 `D2D` 支援。  初始化主視窗之前先呼叫這個方法。|  
|[CWnd::EnableScrollBar](../Topic/CWnd::EnableScrollBar.md)|啟用或停用一個捲軸的一或兩個箭號。|  
|[CWnd::EnableScrollBarCtrl](../Topic/CWnd::EnableScrollBarCtrl.md)|啟用或停用同層級捲軸控制項。|  
|[CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md)|啟用工具提示控制項。|  
|[CWnd::EnableTrackingToolTips](../Topic/CWnd::EnableTrackingToolTips.md)|啟用追蹤模式中的工具提示控制項。|  
|[CWnd::EnableWindow](../Topic/CWnd::EnableWindow.md)|啟用或停用滑鼠和鍵盤輸入。|  
|[CWnd::EndModalLoop](../Topic/CWnd::EndModalLoop.md)|結束視窗的強制回應狀態。|  
|[CWnd::EndModalState](../Topic/CWnd::EndModalState.md)|呼叫此成員函式，將框架視窗從強制回應變更為非強制回應。|  
|[CWnd::EndPaint](../Topic/CWnd::EndPaint.md)|標記繪製的結束。|  
|[CWnd::ExecuteDlgInit](../Topic/CWnd::ExecuteDlgInit.md)|初始化對話方塊資源。|  
|[CWnd::FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md)|擷取對話方塊中控制項相關聯的標題或文字。|  
|[CWnd::FindWindow](../Topic/CWnd::FindWindow.md)|傳回由其視窗名稱和視窗類別識別的視窗控制代碼。|  
|[CWnd::FindWindowEx](../Topic/CWnd::FindWindowEx.md)|傳回由其視窗名稱和視窗類別識別的視窗控制代碼。|  
|[CWnd::FlashWindow](../Topic/CWnd::FlashWindow.md)|閃爍視窗一次。|  
|[CWnd::FlashWindowEx](../Topic/CWnd::FlashWindowEx.md)|閃爍視窗與其他功能。|  
|[CWnd::FromHandle](../Topic/CWnd::FromHandle.md)|將控制代碼提供給視窗時，將指標傳回至 `CWnd` 物件。  如果 `CWnd` 物件沒有附加至控制代碼，會建立並附加暫存 `CWnd` 物件。|  
|[CWnd::FromHandlePermanent](../Topic/CWnd::FromHandlePermanent.md)|將控制代碼提供給視窗時，將指標傳回至 `CWnd` 物件。  如果 `CWnd` 物件沒有附加至控制代碼，會建立並附加暫存 `CWnd` 物件。|  
|[CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)|由架構呼叫以擷取指定子系的 `IDispatch` 介面位址。|  
|[CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)|由架構呼叫以擷取屬於此物件的子物件數目。|  
|[CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)|由架構呼叫以擷取具有物件預設動作描述的字串。|  
|[CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)|由架構呼叫以擷取含有指定物件的視覺外觀描述的字串。|  
|[CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)|由架構呼叫以擷取具有鍵盤焦點的物件。|  
|[CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)|由架構呼叫以擷取物件的 **Help** 屬性字串。|  
|[CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)|由架構呼叫以擷取 `WinHelp` 檔 \(與指定物件和該檔案中適切主題的識別項關聯\) 的完整路徑。|  
|[CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)|由架構呼叫以擷取指定物件的快速鍵或便捷鍵。|  
|[CWnd::get\_accName](../Topic/CWnd::get_accName.md)|由架構呼叫以擷取指定物件的名稱。|  
|[CWnd::get\_accParent](../Topic/CWnd::get_accParent.md)|由架構呼叫以擷取物件之父代的 `IDispatch` 介面。|  
|[CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)|由架構呼叫以擷取含有指定物件的角色描述資訊。|  
|[CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)|由架構呼叫以擷取此物件的選取子物件。|  
|[CWnd::get\_accState](../Topic/CWnd::get_accState.md)|由架構呼叫以擷取指定物件的目前狀態。|  
|[CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)|由架構呼叫以擷取指定物件的值。|  
|[CWnd::GetActiveWindow](../Topic/CWnd::GetActiveWindow.md)|擷取使用中視窗。|  
|[CWnd::GetAncestor](../Topic/CWnd::GetAncestor.md)|擷取指定視窗的上階視窗物件。|  
|[CWnd::GetCapture](../Topic/CWnd::GetCapture.md)|擷取具有滑鼠捕捉的 `CWnd`。|  
|[CWnd::GetCaretPos](../Topic/CWnd::GetCaretPos.md)|擷取插入號之目前位置的用戶端座標。|  
|[CWnd::GetCheckedRadioButton](../Topic/CWnd::GetCheckedRadioButton.md)|傳回按鈕群組中目前核取的選項按鈕的識別碼。|  
|[CWnd::GetClientRect](../Topic/CWnd::GetClientRect.md)|取得 `CWnd` 工作區的維度。|  
|[CWnd::GetClipboardOwner](../Topic/CWnd::GetClipboardOwner.md)|擷取剪貼簿的目前擁有者的指標。|  
|[CWnd::GetClipboardViewer](../Topic/CWnd::GetClipboardViewer.md)|擷取剪貼簿檢視器鏈結中的第一個視窗的指標。|  
|[CWnd::GetControlUnknown](../Topic/CWnd::GetControlUnknown.md)|擷取至未知 ActiveX 控制項的指標。|  
|[CWnd::GetDC](../Topic/CWnd::GetDC.md)|擷取工作區的顯示內容。|  
|[CWnd::GetDCEx](../Topic/CWnd::GetDCEx.md)|擷取工作區的顯示內容，並在繪製時啟用裁剪。|  
|[CWnd::GetDCRenderTarget](../Topic/CWnd::GetDCRenderTarget.md)|擷取裝置內容 \(DC\) 會呈現 `CWnd` 視窗的目標。|  
|[CWnd::GetDescendantWindow](../Topic/CWnd::GetDescendantWindow.md)|搜尋所有下階視窗，並傳回具有指定識別碼的視窗。|  
|[CWnd::GetDesktopWindow](../Topic/CWnd::GetDesktopWindow.md)|擷取 Windows 桌面視窗。|  
|[CWnd::GetDlgCtrlID](../Topic/CWnd::GetDlgCtrlID.md)|如果 `CWnd` 是子視窗，呼叫這個函式會傳回它的識別碼值。|  
|[CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md)|從指定的對話方塊中擷取具有指定識別碼的控制項。|  
|[CWnd::GetDlgItemInt](../Topic/CWnd::GetDlgItemInt.md)|將指定對話方塊中的控制項文字轉譯成整數值。|  
|[CWnd::GetDlgItemText](../Topic/CWnd::GetDlgItemText.md)|擷取與控制項相關聯的標題或文字。|  
|[CWnd::GetDSCCursor](../Topic/CWnd::GetDSCCursor.md)|擷取料來源控制項的 DataSource、UserName、Password 和 SQL 屬性所定義之基礎游標的指標。|  
|[CWnd::GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md)|擷取動態配置管理員物件的指標。|  
|[CWnd::GetExStyle](../Topic/CWnd::GetExStyle.md)|傳回視窗的延伸樣式。|  
|[CWnd::GetFocus](../Topic/CWnd::GetFocus.md)|擷取目前具有輸入焦點的 `CWnd`。|  
|[CWnd::GetFont](../Topic/CWnd::GetFont.md)|擷取目前的字型。|  
|[CWnd::GetForegroundWindow](../Topic/CWnd::GetForegroundWindow.md)|讓指標回到前景視窗 \(使用者目前使用的最上層視窗\)。|  
|[CWnd::GetIcon](../Topic/CWnd::GetIcon.md)|擷取圖示的控制代碼。|  
|[CWnd::GetLastActivePopup](../Topic/CWnd::GetLastActivePopup.md)|判斷 `CWnd` 擁有的快顯視窗哪一個是最近啟用的。|  
|[CWnd::GetLayeredWindowAttributes](../Topic/CWnd::GetLayeredWindowAttributes.md)|擷取分層視窗的不透明和透明色鍵。|  
|[CWnd::GetMenu](../Topic/CWnd::GetMenu.md)|擷取指定功能表的指標。|  
|[CWnd::GetNextDlgGroupItem](../Topic/CWnd::GetNextDlgGroupItem.md)|搜尋控制項群組內的下一個 \(或上一個\) 控制項。|  
|[CWnd::GetNextDlgTabItem](../Topic/CWnd::GetNextDlgTabItem.md)|使用指定控制項的下一個 \(或上一個\) [WS\_TABSTOP](../../mfc/reference/window-styles.md) 樣式來擷取第一個控制項 。|  
|[CWnd::GetNextWindow](../Topic/CWnd::GetNextWindow.md)|傳回視窗管理員清單中的下一個 \(或上一個\) 視窗。|  
|[CWnd::GetOleControlSite](../Topic/CWnd::GetOleControlSite.md)|擷取指定的 ActiveX 控制項的自訂網站。|  
|[CWnd::GetOpenClipboardWindow](../Topic/CWnd::GetOpenClipboardWindow.md)|擷取目前已開啟剪貼簿的視窗指標。|  
|[CWnd::GetOwner](../Topic/CWnd::GetOwner.md)|擷取 `CWnd` 擁有者的指標。|  
|[CWnd::GetParent](../Topic/CWnd::GetParent.md)|擷取 `CWnd` 的父視窗 \(如果有的話\)。|  
|[CWnd::GetParentFrame](../Topic/CWnd::GetParentFrame.md)|擷取 `CWnd` 物件的父框架視窗。|  
|[CWnd::GetParentOwner](../Topic/CWnd::GetParentOwner.md)|傳回子視窗的父視窗指標。|  
|[CWnd::GetProperty](../Topic/CWnd::GetProperty.md)|擷取 ActiveX 控制項屬性。|  
|[CWnd::GetRenderTarget](../Topic/CWnd::GetRenderTarget.md)|取得與此視窗相關聯的呈現目標。|  
|[CWnd::GetSafeHwnd](../Topic/CWnd::GetSafeHwnd.md)|傳回 `m_hWnd`；或如果 `this` 指標為 `NULL` 則傳回 `NULL`。|  
|[CWnd::GetSafeOwner](../Topic/CWnd::GetSafeOwner.md)|擷取給定視窗的安全擁有者。|  
|[CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)|傳回一個同層級捲軸控制項。|  
|[CWnd::GetScrollBarInfo](../Topic/CWnd::GetScrollBarInfo.md)|擷取所指定之捲軸的相關資訊。|  
|[CWnd::GetScrollInfo](../Topic/CWnd::GetScrollInfo.md)|擷取 `SCROLLINFO` 結構維護的捲軸相關資訊。|  
|[CWnd::GetScrollLimit](../Topic/CWnd::GetScrollLimit.md)|擷取捲軸的限制。|  
|[CWnd::GetScrollPos](../Topic/CWnd::GetScrollPos.md)|擷取捲動方塊的目前位置。|  
|[CWnd::GetScrollRange](../Topic/CWnd::GetScrollRange.md)|複製給定捲軸目前的最小和最大捲軸位置。|  
|[CWnd::GetStyle](../Topic/CWnd::GetStyle.md)|傳回目前的視窗樣式。|  
|[CWnd::GetSystemMenu](../Topic/CWnd::GetSystemMenu.md)|可讓應用程式存取控制功能表以進行複製和修改。|  
|[CWnd::GetTitleBarInfo](../Topic/CWnd::GetTitleBarInfo.md)|擷取指定之標題列的相關資訊。|  
|[CWnd::GetTopLevelFrame](../Topic/CWnd::GetTopLevelFrame.md)|擷取視窗的最上層框架視窗。|  
|[CWnd::GetTopLevelOwner](../Topic/CWnd::GetTopLevelOwner.md)|擷取最上層視窗。|  
|[CWnd::GetTopLevelParent](../Topic/CWnd::GetTopLevelParent.md)|擷取視窗的最上層父代。|  
|[CWnd::GetTopWindow](../Topic/CWnd::GetTopWindow.md)|傳回屬於 `CWnd` 的第一個子視窗。|  
|[CWnd::GetUpdateRect](../Topic/CWnd::GetUpdateRect.md)|擷取完全圍住 `CWnd` 更新區域的最小矩形座標。|  
|[CWnd::GetUpdateRgn](../Topic/CWnd::GetUpdateRgn.md)|擷取 `CWnd` 更新區域。|  
|[CWnd::GetWindow](../Topic/CWnd::GetWindow.md)|傳回與此視窗具有指定關聯性的視窗。|  
|[CWnd::GetWindowContextHelpId](../Topic/CWnd::GetWindowContextHelpId.md)|擷取說明內容識別碼。|  
|[CWnd::GetWindowDC](../Topic/CWnd::GetWindowDC.md)|擷取整個視窗的顯示內容，包括標題列、功能表和捲軸。|  
|[CWnd::GetWindowedChildCount](../Topic/CWnd::GetWindowedChildCount.md)|傳回相關聯子視窗的數目。|  
|[CWnd::GetWindowInfo](../Topic/CWnd::GetWindowInfo.md)|傳回視窗的相關資訊。|  
|[CWnd::GetWindowlessChildCount](../Topic/CWnd::GetWindowlessChildCount.md)|傳回相關聯的無視窗子視窗數目。|  
|[CWnd::GetWindowPlacement](../Topic/CWnd::GetWindowPlacement.md)|擷取視窗的顯示狀態和一般 \(還原\)、最小化和最大化位置。|  
|[CWnd::GetWindowRect](../Topic/CWnd::GetWindowRect.md)|取得 `CWnd` 的螢幕座標。|  
|[CWnd::GetWindowRgn](../Topic/CWnd::GetWindowRgn.md)|擷取視窗的視窗區域複本。|  
|[CWnd::GetWindowText](../Topic/CWnd::GetWindowText.md)|傳回視窗文字或標題 \(如果有的話\)。|  
|[CWnd::GetWindowTextLength](../Topic/CWnd::GetWindowTextLength.md)|傳回視窗的文字或標題的長度。|  
|[CWnd::HideCaret](../Topic/CWnd::HideCaret.md)|藉由從顯示畫面移除插入號來隱藏該插入號。|  
|[CWnd::HiliteMenuItem](../Topic/CWnd::HiliteMenuItem.md)|反白顯示或從最上層 \(功能表列\) 的功能表項目中移除反白顯示。|  
|[CWnd::HtmlHelp](../Topic/CWnd::HtmlHelp.md)|呼叫以初始化 HTMLHelp 應用程式。|  
|[CWnd::Invalidate](../Topic/CWnd::Invalidate.md)|使整個工作區失效。|  
|[CWnd::InvalidateRect](../Topic/CWnd::InvalidateRect.md)|將矩形加入至目前的更新區域，使給定矩形內的工作區失效。|  
|[CWnd::InvalidateRgn](../Topic/CWnd::InvalidateRgn.md)|將區域加入至目前的更新區域，使給定區域內的工作區失效。|  
|[CWnd::InvokeHelper](../Topic/CWnd::InvokeHelper.md)|叫用 ActiveX 控制項方法或屬性。|  
|[CWnd::IsChild](../Topic/CWnd::IsChild.md)|指出 `CWnd` 是子視窗，還是指定視窗的其他直屬下階。|  
|[CWnd::IsD2DSupportEnabled](../Topic/CWnd::IsD2DSupportEnabled.md)|決定是否啟用 `D2D` 支援。|  
|[CWnd::IsDialogMessage](../Topic/CWnd::IsDialogMessage.md)|判斷指定的訊息是否適用於非強制回應對話方塊，若是則處理它。|  
|[CWnd::IsDlgButtonChecked](../Topic/CWnd::IsDlgButtonChecked.md)|決定是否核取按鈕控制項。|  
|[CWnd::IsDynamicLayoutEnabled](../Topic/CWnd::IsDynamicLayoutEnabled.md)|決定是否在這個視窗上啟用動態配置。  如果啟用動態配置時，則使用者可在調整父視窗大小時變更子視窗的位置與大小。|  
|[CWnd::IsIconic](../Topic/CWnd::IsIconic.md)|決定是否將 `CWnd` 降到最低 \(圖示\)。|  
|[CWnd::IsTouchWindow](../Topic/CWnd::IsTouchWindow.md)|指定 `CWnd` 是否有觸控支援。|  
|[CWnd::IsWindowEnabled](../Topic/CWnd::IsWindowEnabled.md)|決定是否為滑鼠和鍵盤輸入啟用視窗。|  
|[CWnd::IsWindowVisible](../Topic/CWnd::IsWindowVisible.md)|決定視窗是否可見。|  
|[CWnd::IsZoomed](../Topic/CWnd::IsZoomed.md)|決定是否將 `CWnd` 最大化。|  
|[CWnd::KillTimer](../Topic/CWnd::KillTimer.md)|刪除系統計時器。|  
|[CWnd::LockWindowUpdate](../Topic/CWnd::LockWindowUpdate.md)|停用或重新啟用在給定視窗中繪製。|  
|[CWnd::MapWindowPoints](../Topic/CWnd::MapWindowPoints.md)|將一組點從 `CWnd` 的座標空間轉換 \(對應\) 至另一個視窗的座標空間。|  
|[CWnd::MessageBox](../Topic/CWnd::MessageBox.md)|建立並顯示視窗，其中包含應用程式提供的訊息和標題。|  
|[CWnd::ModifyStyle](../Topic/CWnd::ModifyStyle.md)|修改目前的視窗樣式。|  
|[CWnd::ModifyStyleEx](../Topic/CWnd::ModifyStyleEx.md)|修改視窗的延伸樣式。|  
|[CWnd::MoveWindow](../Topic/CWnd::MoveWindow.md)|變更 `CWnd` 的位置和維度。|  
|[CWnd::NotifyWinEvent](../Topic/CWnd::NotifyWinEvent.md)|表示發生預先定義之事件的系統。|  
|[CWnd::OnAmbientProperty](../Topic/CWnd::OnAmbientProperty.md)|實作環境屬性值。|  
|[CWnd::OnDrawIconicThumbnailOrLivePreview](../Topic/CWnd::OnDrawIconicThumbnailOrLivePreview.md)|需要取得點陣圖，在 Windows 7 索引標籤上顯示為縮圖時，或顯示在用戶端上以查看應用程式時，由架構呼叫。|  
|[CWnd::OnHelp](../Topic/CWnd::OnHelp.md)|在應用程式 \(使用目前的內容\) 中處理 F1 說明。|  
|[CWnd::OnHelpFinder](../Topic/CWnd::OnHelpFinder.md)|處理 `ID_HELP_FINDER` 和 `ID_DEFAULT_HELP` 命令。|  
|[CWnd::OnHelpIndex](../Topic/CWnd::OnHelpIndex.md)|處理 `ID_HELP_INDEX` 命令並提供預設的說明主題。|  
|[CWnd::OnHelpUsing](../Topic/CWnd::OnHelpUsing.md)|處理 `ID_HELP_USING` 命令。|  
|[CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)|決定一個點是否位於指定工具的周框中並擷取工具的相關資訊。|  
|[CWnd::OpenClipboard](../Topic/CWnd::OpenClipboard.md)|開啟剪貼簿。  其他應用程式不會修改剪貼簿，直到呼叫 Windows [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) 函式為止。|  
|[CWnd::PaintWindowlessControls](../Topic/CWnd::PaintWindowlessControls.md)|在控制項容器上繪製無視窗控制項。|  
|[CWnd::PostMessage](../Topic/CWnd::PostMessage.md)|在應用程式佇列中放置訊息，然後傳回，而不需等待視窗處理訊息。|  
|[CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)|在建立附加至此 `CWnd` 物件的 Windows 視窗前呼叫。|  
|[CWnd::PreSubclassWindow](../Topic/CWnd::PreSubclassWindow.md)|可在呼叫 [SubclassWindow](../Topic/CWnd::SubclassWindow.md) 前允許發生其他必要的子類別。|  
|[CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)|由 `CWinApp` 使用，可先篩選視窗訊息，再將它們分派至 `TranslateMessage` 和 `DispatchMessage` Windows 函式。|  
|[CWnd::Print](../Topic/CWnd::Print.md)|在指定的裝置內容中繪製目前的視窗。|  
|[CWnd::PrintClient](../Topic/CWnd::PrintClient.md)|在指定的裝置內容中繪製任何視窗 \(通常是印表機裝置內容\)。|  
|[CWnd::PrintWindow](../Topic/CWnd::PrintWindow.md)|將視覺視窗複製到指定的裝置內容，通常是印表機 DC。|  
|[CWnd::RedrawWindow](../Topic/CWnd::RedrawWindow.md)|更新工作區中指定的矩形或區域。|  
|[CWnd::RegisterTouchWindow](../Topic/CWnd::RegisterTouchWindow.md)|註冊\/取消註冊視窗 Windows 觸控支援。|  
|[CWnd::ReleaseDC](../Topic/CWnd::ReleaseDC.md)|釋放用戶端和視窗裝置內容，釋放這些內容供其他應用程式使用。|  
|[CWnd::RepositionBars](../Topic/CWnd::RepositionBars.md)|工作區中的重新置放控制列。|  
|[CWnd::RunModalLoop](../Topic/CWnd::RunModalLoop.md)|擷取、轉換或分派處於強制回應狀態之視窗的訊息。|  
|[CWnd::ScreenToClient](../Topic/CWnd::ScreenToClient.md)|將畫面上指定的點或矩形的螢幕座標，轉換為用戶端座標。|  
|[CWnd::ScrollWindow](../Topic/CWnd::ScrollWindow.md)|捲動工作區的內容。|  
|[CWnd::ScrollWindowEx](../Topic/CWnd::ScrollWindowEx.md)|捲動工作區的內容。  類似於 `ScrollWindow`，但具有額外的功能。|  
|[CWnd::SendChildNotifyLastMsg](../Topic/CWnd::SendChildNotifyLastMsg.md)|從父視窗中將通知訊息提供給子視窗，讓子視窗可以處理工作。|  
|[CWnd::SendDlgItemMessage](../Topic/CWnd::SendDlgItemMessage.md)|將訊息傳送至指定的控制項。|  
|[CWnd::SendMessage](../Topic/CWnd::SendMessage.md)|傳送訊息給 `CWnd` 物件，在處理訊息後才會傳回。|  
|[CWnd::SendMessageToDescendants](../Topic/CWnd::SendMessageToDescendants.md)|傳送訊息給視窗的所有下階視窗。|  
|[CWnd::SendNotifyMessage](../Topic/CWnd::SendNotifyMessage.md)|將指定的訊息傳送至視窗並儘速傳回，視呼叫執行緒是否建立視窗而定。|  
|[CWnd::SetActiveWindow](../Topic/CWnd::SetActiveWindow.md)|啟用視窗。|  
|[CWnd::SetCapture](../Topic/CWnd::SetCapture.md)|導致所有後續滑鼠輸入傳送至 `CWnd`。|  
|[CWnd::SetCaretPos](../Topic/CWnd::SetCaretPos.md)|將插入號移動到指定的位置。|  
|[CWnd::SetClipboardViewer](../Topic/CWnd::SetClipboardViewer.md)|將 `CWnd` 新增到視窗的鏈結，每當剪貼簿的內容變更時就會通知這些視窗。|  
|[CWnd::SetDlgCtrlID](../Topic/CWnd::SetDlgCtrlID.md)|設定視窗或視窗的控制項識別碼 \(這可以是任何子視窗，而不只是對話方塊中的控制項\)。|  
|[CWnd::SetDlgItemInt](../Topic/CWnd::SetDlgItemInt.md)|將控制項的文字設為表示整數值的字串。|  
|[CWnd::SetDlgItemText](../Topic/CWnd::SetDlgItemText.md)|在指定的對話方塊中設定控制項的標題或文字。|  
|[CWnd::SetFocus](../Topic/CWnd::SetFocus.md)|宣告輸入焦點。|  
|[CWnd::SetFont](../Topic/CWnd::SetFont.md)|設定目前的字型。|  
|[CWnd::SetForegroundWindow](../Topic/CWnd::SetForegroundWindow.md)|將建立視窗的執行緒放置到前景並啟動視窗。|  
|[CWnd::SetIcon](../Topic/CWnd::SetIcon.md)|將控制代碼設為特定的圖示。|  
|[CWnd::SetLayeredWindowAttributes](../Topic/CWnd::SetLayeredWindowAttributes.md)|設定分層視窗的不透明和透明色鍵。|  
|[CWnd::SetMenu](../Topic/CWnd::SetMenu.md)|將功能表設定為指定的功能表。|  
|[CWnd::SetOwner](../Topic/CWnd::SetOwner.md)|變更 `CWnd` 的擁有者。|  
|[CWnd::SetParent](../Topic/CWnd::SetParent.md)|變更父視窗。|  
|[CWnd::SetProperty](../Topic/CWnd::SetProperty.md)|設定 ActiveX 控制項屬性。|  
|[CWnd::SetRedraw](../Topic/CWnd::SetRedraw.md)|允許重新繪製 `CWnd` 中的變更，或防止重新繪製進行變更。|  
|[CWnd::SetScrollInfo](../Topic/CWnd::SetScrollInfo.md)|設定捲軸的相關資訊。|  
|[CWnd::SetScrollPos](../Topic/CWnd::SetScrollPos.md)|設定捲動方塊的目前位置，而且如果指定，會重新繪製捲軸以反映新位置。|  
|[CWnd::SetScrollRange](../Topic/CWnd::SetScrollRange.md)|設定給定捲軸的最小和最大位置值。|  
|[CWnd::SetTimer](../Topic/CWnd::SetTimer.md)|安裝會在觸發時傳送 [WM\_TIMER](../Topic/CWnd::OnTimer.md) 訊息的系統計時器。|  
|[CWnd::SetWindowContextHelpId](../Topic/CWnd::SetWindowContextHelpId.md)|設定說明內容識別碼。|  
|[CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)|設定視窗的顯示狀態和一般 \(還原\)、最小化和最大化位置。|  
|[CWnd::SetWindowPos](../Topic/CWnd::SetWindowPos.md)|變更大小、位置和子系順序、快顯視窗，和最上層視窗。|  
|[CWnd::SetWindowRgn](../Topic/CWnd::SetWindowRgn.md)|設定視窗的區域。|  
|[CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)|將視窗文字或標題 \(如果有的話\) 設為指定的文字。|  
|[CWnd::ShowCaret](../Topic/CWnd::ShowCaret.md)|在畫面上插入號的目前位置上顯示插入號。  顯示後，插入號會開始自動閃爍。|  
|[CWnd::ShowOwnedPopups](../Topic/CWnd::ShowOwnedPopups.md)|顯示或隱藏視窗擁有的所有快顯視窗。|  
|[CWnd::ShowScrollBar](../Topic/CWnd::ShowScrollBar.md)|顯示或隱藏捲軸。|  
|[CWnd::ShowWindow](../Topic/CWnd::ShowWindow.md)|顯示或隱藏視窗。|  
|[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md)|將 Windows 控制項附加至 `CWnd` 物件，並使其透過 `CWnd` 的訊息對應來路由訊息。|  
|[CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)|將視窗附加至 `CWnd` 物件，並使其透過 `CWnd` 的訊息對應來路由訊息。|  
|[CWnd::UnlockWindowUpdate](../Topic/CWnd::UnlockWindowUpdate.md)|解除鎖定已使用 `CWnd::LockWindowUpdate` 鎖定的視窗。|  
|[CWnd::UnsubclassWindow](../Topic/CWnd::UnsubclassWindow.md)|從 `CWnd`  物件卸離視窗|  
|[CWnd::UpdateData](../Topic/CWnd::UpdateData.md)|從對話方塊中初始化或擷取資料。|  
|[CWnd::UpdateDialogControls](../Topic/CWnd::UpdateDialogControls.md)|呼叫以更新對話方塊按鈕和其他控制項的狀態。|  
|[CWnd::UpdateLayeredWindow](../Topic/CWnd::UpdateLayeredWindow.md)|更新分層視窗的位置、大小、形狀、內容和透明度。|  
|[CWnd::UpdateWindow](../Topic/CWnd::UpdateWindow.md)|更新工作區。|  
|[CWnd::ValidateRect](../Topic/CWnd::ValidateRect.md)|從目前的更新區域中移除矩形，驗證給定矩形內的工作區。|  
|[CWnd::ValidateRgn](../Topic/CWnd::ValidateRgn.md)|從目前的更新區域中移除區域，驗證給定區域內的工作區。|  
|[CWnd::WindowFromPoint](../Topic/CWnd::WindowFromPoint.md)|識別包含指定點的視窗。|  
|[CWnd::WinHelp](../Topic/CWnd::WinHelp.md)|呼叫以初始化 WinHelp 應用程式。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CWnd::Default](../Topic/CWnd::Default.md)|呼叫預設視窗程序，提供應用程式不會處理的任何視窗訊息的預設處理程序。|  
|[CWnd::DefWindowProc](../Topic/CWnd::DefWindowProc.md)|呼叫預設視窗程序，提供應用程式不會處理的任何視窗訊息的預設處理程序。|  
|[CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)|適用於對話方塊資料交換和驗證。  由 `UpdateData` 呼叫。|  
|[CWnd::GetCurrentMessage](../Topic/CWnd::GetCurrentMessage.md)|傳回此視窗目前正在處理的訊息指標。  應該只在 `On`*Message* 訊息處理常式成員函式中呼叫。|  
|[CWnd::InitDynamicLayout](../Topic/CWnd::InitDynamicLayout.md)|由架構呼叫以初始化視窗的動態配置。|  
|[CWnd::LoadDynamicLayoutResource](../Topic/CWnd::LoadDynamicLayoutResource.md)|從資源檔載入動態配置資訊。|  
|[CWnd::OnActivate](../Topic/CWnd::OnActivate.md)|當 `CWnd` 啟動或停用時呼叫。|  
|[CWnd::OnActivateApp](../Topic/CWnd::OnActivateApp.md)|當應用程式即將啟動或停用時呼叫。|  
|[CWnd::OnAppCommand](../Topic/CWnd::OnAppCommand.md)|當使用者產生應用程式命令事件時呼叫。|  
|[CWnd::OnAskCbFormatName](../Topic/CWnd::OnAskCbFormatName.md)|當剪貼簿擁有者將顯示剪貼簿內容時，由剪貼簿檢視器應用程式呼叫。|  
|[CWnd::OnCancelMode](../Topic/CWnd::OnCancelMode.md)|呼叫以讓 `CWnd` 取消任何內部的模式，例如滑鼠捕捉。|  
|[CWnd::OnCaptureChanged](../Topic/CWnd::OnCaptureChanged.md)|將訊息傳送至正失去滑鼠捕捉的視窗。|  
|[CWnd::OnChangeCbChain](../Topic/CWnd::OnChangeCbChain.md)|通知正在從鏈結中移除指定的視窗。|  
|[CWnd::OnChangeUIState](../Topic/CWnd::OnChangeUIState.md)|應變更使用者介面 \(UI\) 狀態時呼叫。|  
|[CWnd::OnChar](../Topic/CWnd::OnChar.md)|按鍵轉譯為非系統字元時呼叫。|  
|[CWnd::OnCharToItem](../Topic/CWnd::OnCharToItem.md)|由含有 [LBS\_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md) 樣式的子清單方塊呼叫，以回應 [WM\_CHAR](../Topic/CWnd::OnChar.md) 訊息。|  
|[CWnd::OnChildActivate](../Topic/CWnd::OnChildActivate.md)|每當 `CWnd` 的大小或位置變更，或 `CWnd` 已啟動時，針對多重文件介面 \(MDI\) 子視窗呼叫。|  
|[CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)|由父視窗呼叫，讓通知控制項有機會回應控制項通知。|  
|[CWnd::OnClipboardUpdate](../Topic/CWnd::OnClipboardUpdate.md)|於剪貼簿內容已變更時呼叫。|  
|[CWnd::OnClose](../Topic/CWnd::OnClose.md)|呼叫以表示 `CWnd` 應該關閉。|  
|[CWnd::OnColorizationColorChanged](../Topic/CWnd::OnColorizationColorChanged.md)|當非工作區的轉譯原則已變更時呼叫。|  
|[CWnd::OnCommand](../Topic/CWnd::OnCommand.md)|當使用者選取命令時呼叫。|  
|[CWnd::OnCompacting](../Topic/CWnd::OnCompacting.md)|當 Windows 偵測到系統記憶體過低時呼叫。|  
|[CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)|呼叫以判斷子排序之主控描繪的下拉式方塊或清單方塊中新項目的相對位置。|  
|[CWnd::OnCompositionChanged](../Topic/CWnd::OnCompositionChanged.md)|當桌面視窗管理員 \(DWM\) 組合啟用或停用時，為所有最上層視窗呼叫。|  
|[CWnd::OnContextMenu](../Topic/CWnd::OnContextMenu.md)|當使用者在視窗中按一下滑鼠右鍵時呼叫。|  
|[CWnd::OnCopyData](../Topic/CWnd::OnCopyData.md)|在應用程式之間複製資料。|  
|[CWnd::OnCreate](../Topic/CWnd::OnCreate.md)|在視窗建立過程中呼叫。|  
|[CWnd::OnCtlColor](../Topic/CWnd::OnCtlColor.md)|即將繪製控制項時，如果`CWnd` 是控制項的父代則呼叫。|  
|[CWnd::OnDeadChar](../Topic/CWnd::OnDeadChar.md)|當按鍵轉譯為非系統無效字元 \(例如強調符號\) 時呼叫。|  
|[CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)|當主控描繪子清單方塊或下拉式方塊損毀，或從控制項移除項目時呼叫。|  
|[CWnd::OnDestroy](../Topic/CWnd::OnDestroy.md)|`CWnd` 正在損毀時呼叫。|  
|[CWnd::OnDestroyClipboard](../Topic/CWnd::OnDestroyClipboard.md)|透過呼叫 Windows [EmptyClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649037) 函式清空剪貼簿時呼叫。|  
|[CWnd::OnDeviceChange](../Topic/CWnd::OnDeviceChange.md)|將裝置或電腦的硬體組態變更通知應用程式或裝置驅動程式。|  
|[CWnd::OnDevModeChange](../Topic/CWnd::OnDevModeChange.md)|當使用者變更裝置模式設定時，針對所有最上層視窗呼叫。|  
|[CWnd::OnDrawClipboard](../Topic/CWnd::OnDrawClipboard.md)|於剪貼簿內容變更時呼叫。|  
|[CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)|主控描繪子按鈕控制項、下拉式方塊控制項、清單方塊控制項或功能表的視覺外觀必須繪製時呼叫。|  
|[CWnd::OnDropFiles](../Topic/CWnd::OnDropFiles.md)|當使用者在視窗 \(已本身註冊為捨棄檔案的收件者\) 上放開滑鼠按鈕時呼叫。|  
|[CWnd::OnEnable](../Topic/CWnd::OnEnable.md)|啟用或停用 `CWnd` 時呼叫。|  
|[CWnd::OnEndSession](../Topic/CWnd::OnEndSession.md)|當工作階段正在結束時呼叫。|  
|[CWnd::OnEnterIdle](../Topic/CWnd::OnEnterIdle.md)|呼叫此函式，可將強制回應對話方塊或功能表正在進入閒置狀態的訊息，通知應用程式的主視窗程序。|  
|[CWnd::OnEnterMenuLoop](../Topic/CWnd::OnEnterMenuLoop.md)|已進入功能表強制回應迴圈時呼叫。|  
|[CWnd::OnEnterSizeMove](../Topic/CWnd::OnEnterSizeMove.md)|在受影響的視窗進入移動或調整大小的強制回應迴圈後呼叫。|  
|[CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)|視窗背景需要清除時呼叫。|  
|[CWnd::OnExitMenuLoop](../Topic/CWnd::OnExitMenuLoop.md)|已結束功能表強制回應迴圈時呼叫。|  
|[CWnd::OnExitSizeMove](../Topic/CWnd::OnExitSizeMove.md)|在受影響的視窗結束移動或調整大小的強制回應迴圈後呼叫。|  
|[CWnd::OnFontChange](../Topic/CWnd::OnFontChange.md)|字型資源的集區變更時呼叫。|  
|[CWnd::OnGetDlgCode](../Topic/CWnd::OnGetDlgCode.md)|呼叫控制項，讓控制項可以處理方向鍵和 TAB 鍵輸入本身。|  
|[CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)|每當 Windows 必須知道最大化的位置或維度，或最小或最大的追蹤大小時呼叫。|  
|[CWnd::OnHelpInfo](../Topic/CWnd::OnHelpInfo.md)|當使用者按下 F1 鍵時，由架構呼叫。|  
|[CWnd::OnHotKey](../Topic/CWnd::OnHotKey.md)|當使用者按下全系統的便捷鍵時呼叫。|  
|[CWnd::OnHScroll](../Topic/CWnd::OnHScroll.md)|當使用者按一下 `CWnd` 的水平捲軸時呼叫。|  
|[CWnd::OnHScrollClipboard](../Topic/CWnd::OnHScrollClipboard.md)|當剪貼簿擁有者應該捲動剪貼簿影像、使適當的區段失效，及更新捲軸值時呼叫。|  
|[CWnd::OnIconEraseBkgnd](../Topic/CWnd::OnIconEraseBkgnd.md)|當 `CWnd` 減到最小 \(圖示\)，且必須先填入圖示的背景再繪製圖示時呼叫。|  
|[CWnd::OnInitMenu](../Topic/CWnd::OnInitMenu.md)|當功能表即將變成現用時呼叫。|  
|[CWnd::OnInitMenuPopup](../Topic/CWnd::OnInitMenuPopup.md)|當快顯功能表即將變成現用時呼叫。|  
|[CWnd::OnInputDeviceChange](../Topic/CWnd::OnInputDeviceChange.md)|從系統中新增或移除 I\/O 裝置時呼叫。|  
|[CWnd::OnInputLangChange](../Topic/CWnd::OnInputLangChange.md)|在應用程式的輸入語言變更後呼叫。|  
|[CWnd::OnInputLangChangeRequest](../Topic/CWnd::OnInputLangChangeRequest.md)|當使用者選擇新的輸入語言時呼叫。|  
|[CWnd::OnKeyDown](../Topic/CWnd::OnKeyDown.md)|按下非系統鍵時呼叫。|  
|[CWnd::OnKeyUp](../Topic/CWnd::OnKeyUp.md)|放開非系統鍵時呼叫。|  
|[CWnd::OnKillFocus](../Topic/CWnd::OnKillFocus.md)|在 `CWnd` 遺失輸入焦點前立即呼叫。|  
|[CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md)|當使用者按兩下滑鼠左鍵時呼叫。|  
|[CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md)|當使用者按下滑鼠左鍵時呼叫。|  
|[CWnd::OnLButtonUp](../Topic/CWnd::OnLButtonUp.md)|當使用者放開滑鼠左鍵時呼叫。|  
|[CWnd::OnMButtonDblClk](../Topic/CWnd::OnMButtonDblClk.md)|當使用者按兩下滑鼠中鍵時呼叫。|  
|[CWnd::OnMButtonDown](../Topic/CWnd::OnMButtonDown.md)|當使用者按下滑鼠中鍵時呼叫。|  
|[CWnd::OnMButtonUp](../Topic/CWnd::OnMButtonUp.md)|當使用者放開滑鼠中鍵時呼叫。|  
|[CWnd::OnMDIActivate](../Topic/CWnd::OnMDIActivate.md)|當 MDI 子視窗啟用或停用時呼叫。|  
|[CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)|建立控制項時，針對主控描繪子下拉式方塊、清單方塊或功能表項目呼叫。  `CWnd` 會將控制項維度通知 Windows。|  
|[CWnd::OnMenuChar](../Topic/CWnd::OnMenuChar.md)|當使用者按下功能表的助憶鍵字元，且該字元不符合目前功能表中任何預先定義的助憶鍵時呼叫。|  
|[CWnd::OnMenuDrag](../Topic/CWnd::OnMenuDrag.md)|當使用者開始拖曳功能表項目時呼叫。|  
|[CWnd::OnMenuGetObject](../Topic/CWnd::OnMenuGetObject.md)|當滑鼠游標進入功能表項目，或從項目中央移到項目上方或下方時呼叫。|  
|[CWnd::OnMenuRButtonUp](../Topic/CWnd::OnMenuRButtonUp.md)|當游標位於功能表項目上，而使用者放開滑鼠右鍵時呼叫。|  
|[CWnd::OnMenuSelect](../Topic/CWnd::OnMenuSelect.md)|當使用者選取功能表項目時呼叫。|  
|[CWnd::OnMouseActivate](../Topic/CWnd::OnMouseActivate.md)|當游標處於非使用中視窗，且使用者按下滑鼠按鈕時呼叫。|  
|[CWnd::OnMouseHover](../Topic/CWnd::OnMouseHover.md)|將游標停留在視窗的工作區上，且在先前呼叫 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 時指定的時段內持續停留時，則進行呼叫。|  
|[CWnd::OnMouseHWheel](../Topic/CWnd::OnMouseHWheel.md)|當目前的視窗由桌面視窗管理員 \(DWM\) 組成，且該視窗最大化時呼叫。|  
|[CWnd::OnMouseLeave](../Topic/CWnd::OnMouseLeave.md)|當游標離開之前的 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 呼叫中所指定視窗的工作區時呼叫。|  
|[CWnd::OnMouseMove](../Topic/CWnd::OnMouseMove.md)|當滑鼠游標移動時呼叫。|  
|[CWnd::OnMouseWheel](../Topic/CWnd::OnMouseWheel.md)|當使用者旋轉滑鼠滾輪時呼叫。  使用 Windows NT 4.0 訊息處理。|  
|[CWnd::OnMove](../Topic/CWnd::OnMove.md)|在 `CWnd` 的位置變更後呼叫。|  
|[CWnd::OnMoving](../Topic/CWnd::OnMoving.md)|指出使用者正在移動 `CWnd` 物件。|  
|[CWnd::OnNcActivate](../Topic/CWnd::OnNcActivate.md)|當非工作區需要變更以表示作用中或非作用中狀態時呼叫。|  
|[CWnd::OnNcCalcSize](../Topic/CWnd::OnNcCalcSize.md)|需要計算工作區的大小和位置時呼叫。|  
|[CWnd::OnNcCreate](../Topic/CWnd::OnNcCreate.md)|建立非工作區時，在 [OnCreate](../Topic/CWnd::OnCreate.md) 之前呼叫。|  
|[CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)|當非工作區正在損毀時呼叫。|  
|[CWnd::OnNcHitTest](../Topic/CWnd::OnNcHitTest.md)|每次移動滑鼠時，如果 `CWnd` 包含游標，或已使用 `SetCapture` 擷取滑鼠輸入時呼叫。|  
|[CWnd::OnNcLButtonDblClk](../Topic/CWnd::OnNcLButtonDblClk.md)|當使用者按兩下滑鼠左鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcLButtonDown](../Topic/CWnd::OnNcLButtonDown.md)|當使用者按下滑鼠左鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcLButtonUp](../Topic/CWnd::OnNcLButtonUp.md)|當使用者放開滑鼠左鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcMButtonDblClk](../Topic/CWnd::OnNcMButtonDblClk.md)|當使用者按兩下滑鼠中鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcMButtonDown](../Topic/CWnd::OnNcMButtonDown.md)|當使用者按下滑鼠中鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcMButtonUp](../Topic/CWnd::OnNcMButtonUp.md)|當使用者放開滑鼠中鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcMouseHover](../Topic/CWnd::OnNcMouseHover.md)|將游標停留在視窗的非工作區上，且在先前呼叫 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 時指定的時段內持續停留時，則進行呼叫。|  
|[CWnd::OnNcMouseLeave](../Topic/CWnd::OnNcMouseLeave.md)|當游標離開之前的 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 呼叫中所指定視窗的非工作區時，架構會呼叫此成員函式。|  
|[CWnd::OnNcMouseMove](../Topic/CWnd::OnNcMouseMove.md)|當游標在 `CWnd` 的非工作區內移動時呼叫。|  
|[CWnd::OnNcPaint](../Topic/CWnd::OnNcPaint.md)|當非工作區需要繪製時呼叫。|  
|[CWnd::OnNcRButtonDblClk](../Topic/CWnd::OnNcRButtonDblClk.md)|當使用者按兩下滑鼠右鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcRButtonDown](../Topic/CWnd::OnNcRButtonDown.md)|當使用者按下滑鼠右鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcRButtonUp](../Topic/CWnd::OnNcRButtonUp.md)|當使用者放開滑鼠右鍵，而游標位於 `CWnd` 的非工作區內時呼叫。|  
|[CWnd::OnNcRenderingChanged](../Topic/CWnd::OnNcRenderingChanged.md)|當非工作區的轉譯原則已變更時呼叫。|  
|[CWnd::OnNcXButtonDblClk](../Topic/CWnd::OnNcXButtonDblClk.md)|當使用者按兩下 XBUTTON1 或 XBUTTON2，而游標位於視窗的非工作區時呼叫。|  
|[CWnd::OnNcXButtonDown](../Topic/CWnd::OnNcXButtonDown.md)|當使用者按下滑鼠的 XBUTTON1 或 XBUTTON2，而游標位於視窗的非工作區時呼叫。|  
|[CWnd::OnNcXButtonUp](../Topic/CWnd::OnNcXButtonUp.md)|當使用者放開滑鼠的 XBUTTON1 或 XBUTTON2，而游標位於視窗的非工作區時呼叫。|  
|[CWnd::OnNextMenu](../Topic/CWnd::OnNextMenu.md)|當使用向右鍵或向左鍵切換功能表列和系統功能表時呼叫。|  
|[CWnd::OnNotify](../Topic/CWnd::OnNotify.md)|由架構呼叫，將其中一個控制項已發生的事件，或控制項需要資訊等狀況通知父視窗。|  
|[CWnd::OnNotifyFormat](../Topic/CWnd::OnNotifyFormat.md)|呼叫以決定目前視窗的 WM\_NOTIFY 通知訊息中是否接受 ANSI 或 Unicode 結構。|  
|[CWnd::OnPaint](../Topic/CWnd::OnPaint.md)|呼叫以重新繪製視窗的一部份。|  
|[CWnd::OnPaintClipboard](../Topic/CWnd::OnPaintClipboard.md)|當需要重新繪製剪貼簿檢視器的工作區時呼叫。|  
|[CWnd::OnPaletteChanged](../Topic/CWnd::OnPaletteChanged.md)|呼叫以允許使用調色盤的視窗調整其邏輯色板的大小，並更新其工作區。|  
|[CWnd::OnPaletteIsChanging](../Topic/CWnd::OnPaletteIsChanging.md)|當應用程式即將實現其邏輯色板時通知其他應用程式。|  
|[CWnd::OnParentNotify](../Topic/CWnd::OnParentNotify.md)|建立或終結子視窗時，或當使用者按一下滑鼠按鈕，而游標移至子視窗上方時，進行呼叫。|  
|[CWnd::OnPowerBroadcast](../Topic/CWnd::OnPowerBroadcast.md)|電源管理事件發生時呼叫。|  
|[CWnd::OnQueryDragIcon](../Topic/CWnd::OnQueryDragIcon.md)|最小化 \(圖示化\) `CWnd` 即將由使用者拖曳時呼叫。|  
|[CWnd::OnQueryEndSession](../Topic/CWnd::OnQueryEndSession.md)|當使用者選擇結束 Windows 工作階段時呼叫。|  
|[CWnd::OnQueryNewPalette](../Topic/CWnd::OnQueryNewPalette.md)|通知 `CWnd` 即將接收輸入焦點。|  
|[CWnd::OnQueryOpen](../Topic/CWnd::OnQueryOpen.md)|當 `CWnd` 是圖示，且使用者要求開啟圖示時呼叫。|  
|[CWnd::OnQueryUIState](../Topic/CWnd::OnQueryUIState.md)|呼叫以擷取視窗的使用者介面 \(UI\) 狀態。|  
|[CWnd::OnRawInput](../Topic/CWnd::OnRawInput.md)|當目前視窗取得原始輸入時呼叫。|  
|[CWnd::OnRButtonDblClk](../Topic/CWnd::OnRButtonDblClk.md)|當使用者按兩下滑鼠右鍵時呼叫。|  
|[CWnd::OnRButtonDown](../Topic/CWnd::OnRButtonDown.md)|當使用者按下滑鼠右鍵時呼叫。|  
|[CWnd::OnRButtonUp](../Topic/CWnd::OnRButtonUp.md)|當使用者放開滑鼠右鍵時呼叫。|  
|[CWnd::OnRenderAllFormats](../Topic/CWnd::OnRenderAllFormats.md)|當擁有者應用程式正在被破壞，而且需要呈現其所有格式時呼叫。|  
|[CWnd::OnRenderFormat](../Topic/CWnd::OnRenderFormat.md)|需要呈現具有延遲轉譯需求的特定格式時，針對剪貼簿擁有者呼叫。|  
|[CWnd::OnSessionChange](../Topic/CWnd::OnSessionChange.md)|呼叫以將工作階段狀態的變更通知應用程式。|  
|[CWnd::OnSetCursor](../Topic/CWnd::OnSetCursor.md)|如果不擷取滑鼠輸入，而且滑鼠導致游標在視窗內移動，則呼叫。|  
|[CWnd::OnSetFocus](../Topic/CWnd::OnSetFocus.md)|在 `CWnd` 取得輸入焦點後呼叫。|  
|[CWnd::OnSettingChange](../Topic/CWnd::OnSettingChange.md)|當 Win32 `SystemParametersInfo` 函式變更整個系統的設定時呼叫。|  
|[CWnd::OnShowWindow](../Topic/CWnd::OnShowWindow.md)|當 `CWnd` 要隱藏或顯示時呼叫。|  
|[CWnd::OnSize](../Topic/CWnd::OnSize.md)|在 `CWnd` 大小變更後呼叫。|  
|[CWnd::OnSizeClipboard](../Topic/CWnd::OnSizeClipboard.md)|當剪貼簿檢視器視窗中的工作區大小變更後呼叫。|  
|[CWnd::OnSizing](../Topic/CWnd::OnSizing.md)|表示使用者正在重新調整矩形的大小。|  
|[CWnd::OnSpoolerStatus](../Topic/CWnd::OnSpoolerStatus.md)|每當加入工作或從列印管理員佇列中移除工作時，從列印管理員呼叫。|  
|[CWnd::OnStyleChanged](../Topic/CWnd::OnStyleChanged.md)|表示 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函式已變更一或多個視窗的樣式。|  
|[CWnd::OnStyleChanging](../Topic/CWnd::OnStyleChanging.md)|表示 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函式即將變更一或多個視窗的樣式。|  
|[CWnd::OnSysChar](../Topic/CWnd::OnSysChar.md)|按鍵轉譯為系統字元時呼叫。|  
|[CWnd::OnSysColorChange](../Topic/CWnd::OnSysColorChange.md)|當系統色彩設定中進行變更時，為所有最上層視窗呼叫。|  
|[CWnd::OnSysCommand](../Topic/CWnd::OnSysCommand.md)|當使用者從 \[控制\] 功能表中選取命令時，或在使用者選取 \[最大化\] 或 \[最小化\] 按鈕時呼叫。|  
|[CWnd::OnSysDeadChar](../Topic/CWnd::OnSysDeadChar.md)|當按鍵轉譯為系統無效字元 \(例如強調符號\) 時呼叫。|  
|[CWnd::OnSysKeyDown](../Topic/CWnd::OnSysKeyDown.md)|當使用者按住 ALT 鍵，然後按下另一個按鍵時呼叫。|  
|[CWnd::OnSysKeyUp](../Topic/CWnd::OnSysKeyUp.md)|當使用者在按住 ALT 鍵時放開按下的按鍵時呼叫。|  
|[CWnd::OnTCard](../Topic/CWnd::OnTCard.md)|使用者按一下可設計的按鈕時呼叫。|  
|[CWnd::OnTimeChange](../Topic/CWnd::OnTimeChange.md)|在系統時間變更後，針對所有最上層視窗呼叫。|  
|[CWnd::OnTimer](../Topic/CWnd::OnTimer.md)|在 [SetTimer](../Topic/CWnd::SetTimer.md) 中指定的每個間隔後呼叫。|  
|[CWnd::OnTouchInput](../Topic/CWnd::OnTouchInput.md)|處理來自 Windows 觸控的單一輸入。|  
|[CWnd::OnTouchInputs](../Topic/CWnd::OnTouchInputs.md)|處理來自 Windows 觸控的輸入。|  
|[CWnd::OnUniChar](../Topic/CWnd::OnUniChar.md)|按下按鍵時呼叫。  也就是目前的視窗擁有鍵盤焦點，且 [WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) 訊息由 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 函式轉譯。|  
|[CWnd::OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)|於下拉式功能表或子功能表被終結時呼叫。|  
|[CWnd::OnUpdateUIState](../Topic/CWnd::OnUpdateUIState.md)|呼叫以變更指定的視窗及其所有子視窗的使用者介面 \(UI\) 狀態。|  
|[CWnd::OnUserChanged](../Topic/CWnd::OnUserChanged.md)|在使用者登入或登出後呼叫。|  
|[CWnd::OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)|由 `CWnd` 擁有的清單方塊呼叫，以回應 [WM\_KEYDOWN](../Topic/CWnd::OnKeyDown.md) 訊息。|  
|[CWnd::OnVScroll](../Topic/CWnd::OnVScroll.md)|當使用者按一下視窗的垂直捲軸時呼叫。|  
|[CWnd::OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)|當擁有者應該捲動剪貼簿影像、使適當的區段失效，及更新捲軸值時呼叫。|  
|[CWnd::OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)|當大小、位置或疊置順序已因呼叫 [SetWindowPos](../Topic/CWnd::SetWindowPos.md) 或另一個視窗管理函式而變更時呼叫。|  
|[CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)|當大小、位置或疊置順序即將因呼叫 [SetWindowPos](../Topic/CWnd::SetWindowPos.md) 或另一個視窗管理函式而變更時呼叫。|  
|[CWnd::OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)|在 Windows 初始化檔案 \(WIN.INI\) 變更後，針所有最上層視窗呼叫。|  
|[CWnd::OnWndMsg](../Topic/CWnd::OnWndMsg.md)|指出是否已處理視窗訊息。|  
|[CWnd::OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)|當使用者按兩下 XBUTTON1 或 XBUTTON2，而游標位於視窗的工作區時呼叫。|  
|[CWnd::OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)|當使用者按下 XBUTTON1 或 XBUTTON2，而游標位於視窗的工作區時呼叫。|  
|[CWnd::OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)|當使用者放開 XBUTTON1 或 XBUTTON2，而游標位於視窗的工作區時呼叫。|  
|[CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)|在終結視窗後，此虛擬函式由預設 [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md) 函式所呼叫。|  
|[CWnd::ReflectChildNotify](../Topic/CWnd::ReflectChildNotify.md)|將訊息反映至其來源的 Helper 函式。|  
|[CWnd::ReflectLastMsg](../Topic/CWnd::ReflectLastMsg.md)|將最後一個訊息反映到子視窗。|  
|[CWnd::ResizeDynamicLayout](../Topic/CWnd::ResizeDynamicLayout.md)|如果已啟用視窗的動態配置，則會在視窗大小變更以調整子視窗的版面配置時由架構呼叫。|  
|[CWnd::WindowProc](../Topic/CWnd::WindowProc.md)|提供 `CWnd` 的視窗程序。  透過訊息對應的預設分派訊息。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CWnd::operator HWND](../Topic/CWnd::operator%20HWND.md)|呼叫以取得視窗的控制代碼。|  
|[CWnd::operator \!\=](../Topic/CWnd::operator%20!=.md)|判斷視窗是否與控制代碼為 [m\_hWnd](../Topic/CWnd::m_hWnd.md) 的視窗不同。|  
|[CWnd::operator \=\=](../Topic/CWnd::operator%20==.md)|判斷視窗是否與控制代碼為 [m\_hWnd](../Topic/CWnd::m_hWnd.md) 的視窗相同。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWnd::m\_hWnd](../Topic/CWnd::m_hWnd.md)|指出 `HWND` 附加至此 `CWnd`。|  
  
## 備註  
 `CWnd` 物件不同於 Windows 視窗，但兩者緊密連結。  `CWnd` 物件是由 `CWnd` 建構函式和解構函式所建立或終結。  相反地，Windows 視窗中是 Windows 內部的一種資料結構所，由 **Create** 成員函式建立，並由 `CWnd` 虛擬解構函式終結。  [DestroyWindow](../Topic/CWnd::DestroyWindow.md) 函式會終結 Windows 視窗而不會終結物件。  
  
 `CWnd` 類別和訊息對應機制會隱藏 **WndProc** 函式。  會透過將訊息對應到適當的 **On***Message* `CWnd` 成員函式，自動路由連入的 Windows 通知訊息。  您可以覆寫 **On***Message* 成員函式，處理衍生類別中成員的特定訊息。  
  
 `CWnd` 類別也可讓您建立應用程式的 Windows 子視窗。  自 `CWnd` 衍生類別，然後將成員變數加入至衍生類別以儲存應用程式的特定資料。  實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。  
  
 您在兩個步驟中建立子視窗。  首先，呼叫建構函式 `CWnd` 以建構 `CWnd` 物件，然後呼叫 [Create](../Topic/CWnd::Create.md) 成員函式來建立子視窗，並將其附加至 `CWnd` 物件。  
  
 當使用者終止子視窗時，摧毀 `CWnd` 物件，或呼叫 `DestroyWindow` 成員函式來移除視窗並摧毀其資料結構。  
  
 在 Microsoft Foundation 類別庫中，會自 `CWnd` 衍生進一步類別以提供特定的視窗類型。  其中許多類別 \(包括 [CFrameWnd](../../mfc/reference/cframewnd-class.md)、[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)、[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)、[CView](../../mfc/reference/cview-class.md) 和 [CDialog](../../mfc/reference/cdialog-class.md)\) 是專為進一步衍生所設計。  控制項類別衍生自 `CWnd`，例如 [CButton](../../mfc/reference/cbutton-class.md)，可以直接使用或用於進一步衍生的類別。  
  
 如需使用 `CWnd` 的詳細資訊，請參閱[框架視窗](../../mfc/frame-windows.md)和[視窗物件](../../mfc/window-objects.md)。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWnd`  
  
## 需求  
 **標題：**afxwin.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)