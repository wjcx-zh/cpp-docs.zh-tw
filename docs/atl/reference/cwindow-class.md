---
title: "CWindow 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CWindow
- ATL::CWindow
- CWindow
dev_langs:
- C++
helpviewer_keywords:
- CWindow class
ms.assetid: fefa00c8-f053-4bcf-87bc-dc84f5386683
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dd5e052f74fad8362c58170262e4229549e26868
ms.lasthandoff: 02/24/2017

---
# <a name="cwindow-class"></a>CWindow 類別
這個類別會提供管理視窗的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CWindow
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWindow::CWindow](#cwindow)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWindow::ArrangeIconicWindows](#arrangeiconicwindows)|排列所有的最小化的子視窗。|  
|[CWindow::Attach](#attach)|將附加的視窗`CWindow`物件。|  
|[CWindow::BeginPaint](#beginpaint)|準備要繪製的視窗。|  
|[CWindow::BringWindowToTop](#bringwindowtotop)|將視窗帶到疊置順序的頂端。|  
|[CWindow::CenterWindow](#centerwindow)|針對指定的視窗視窗置中對齊。|  
|[CWindow::ChangeClipboardChain](#changeclipboardchain)|從剪貼簿檢視器的鏈結中移除視窗。|  
|[CWindow::CheckDlgButton](#checkdlgbutton)|指定按鈕的核取狀態變更。|  
|[CWindow::CheckRadioButton](#checkradiobutton)|檢查指定的選項按鈕。|  
|[CWindow::ChildWindowFromPoint](#childwindowfrompoint)|擷取包含指定的點的子視窗。|  
|[CWindow::ChildWindowFromPointEx](#childwindowfrompointex)|擷取特定類型的子視窗，其中包含指定的點。|  
|[CWindow::ClientToScreen](#clienttoscreen)|將工作區座標轉換為螢幕座標。|  
|[CWindow::Create](#create)|建立視窗。|  
|[CWindow::CreateCaret](#createcaret)|建立新的圖形，使系統插入號。|  
|[CWindow::CreateGrayCaret](#creategraycaret)|建立系統游標的灰色矩形。|  
|[CWindow::CreateSolidCaret](#createsolidcaret)|建立系統游標的實心矩形。|  
|[CWindow::DeferWindowPos](#deferwindowpos)|更新指定的多個視窗位置結構指定的視窗。|  
|[CWindow::DestroyWindow](#destroywindow)|終結視窗相關聯`CWindow`物件。|  
|[CWindow::Detach](#detach)|卸離 視窗中的，從`CWindow`物件。|  
|[CWindow::DlgDirList](#dlgdirlist)|清單方塊中填入所有符合指定的路徑或檔案名稱的檔案名稱。|  
|[CWindow::DlgDirListComboBox](#dlgdirlistcombobox)|下拉式方塊中填入所有符合指定的路徑或檔案名稱的檔案名稱。|  
|[CWindow::DlgDirSelect](#dlgdirselect)|從清單方塊擷取目前的選取範圍。|  
|[CWindow::DlgDirSelectComboBox](#dlgdirselectcombobox)|從下拉式方塊擷取目前的選取範圍。|  
|[CWindow::DragAcceptFiles](#dragacceptfiles)|暫存器視窗是否會接受拖曳檔案。|  
|[CWindow::DrawMenuBar](#drawmenubar)|視窗的功能表列來重新繪製。|  
|[CWindow::EnableScrollBar](#enablescrollbar)|啟用或停用捲軸箭號。|  
|[CWindow::EnableWindow](#enablewindow)|啟用或停用輸入。|  
|[CWindow::EndPaint](#endpaint)|標記繪製的結束。|  
|[CWindow::FlashWindow](#flashwindow)|閃爍視窗一次。|  
|[CWindow::GetClientRect](#getclientrect)|擷取用戶端區域的座標。|  
|[CWindow::GetDC](#getdc)|擷取用戶端區域的裝置內容。|  
|[CWindow::GetDCEx](#getdcex)|擷取用戶端區域的裝置內容，並允許裁剪選項。|  
|[CWindow::GetDescendantWindow](#getdescendantwindow)|擷取指定之子系的視窗。|  
|[CWindow::GetDlgControl](#getdlgcontrol)|擷取指定的控制項上的介面。|  
|[CWindow::GetDlgCtrlID](#getdlgctrlid)|擷取 （僅適用於子 windows) 視窗中的識別項。|  
|[CWindow::GetDlgHost](#getdlghost)|擷取 ATL 控制項裝載容器的介面指標。|  
|[CWindow::GetDlgItem](#getdlgitem)|擷取指定的子視窗。|  
|[CWindow::GetDlgItemInt](#getdlgitemint)|將轉譯成整數的控制項的文字。|  
|[CWindow::GetDlgItemText](#getdlgitemtext)|擷取控制項的文字。|  
|[CWindow::GetExStyle](#getexstyle)|擷取延伸的視窗樣式。|  
|[CWindow::GetFont](#getfont)|擷取目前的視窗的字型。|  
|[CWindow::GetHotKey](#gethotkey)|決定熱鍵與視窗相關聯。|  
|[CWindow::GetIcon](#geticon)|擷取視窗的大型或小型圖示。|  
|[CWindow::GetLastActivePopup](#getlastactivepopup)|擷取最近使用的快顯視窗。|  
|[CWindow::GetMenu](#getmenu)|擷取視窗的功能表。|  
|[CWindow::GetNextDlgGroupItem](#getnextdlggroupitem)|擷取群組內的控制項的上一個或下一個控制項。|  
|[CWindow::GetNextDlgTabItem](#getnextdlgtabitem)|擷取上一個或下一個控制項有**WS_TABSTOP**樣式。|  
|[CWindow::GetParent](#getparent)|擷取直屬父視窗。|  
|[CWindow::GetScrollInfo](#getscrollinfo)|擷取捲軸的參數。|  
|[CWindow::GetScrollPos](#getscrollpos)|擷取的捲動方塊的位置。|  
|[CWindow::GetScrollRange](#getscrollrange)|擷取捲軸列範圍。|  
|[CWindow::GetStyle](#getstyle)|擷取的視窗樣式。|  
|[CWindow::GetSystemMenu](#getsystemmenu)|建立一份要修改的 [系統] 功能表。|  
|[CWindow::GetTopLevelParent](#gettoplevelparent)|擷取父系或擁有者的最上層視窗。|  
|[CWindow::GetTopLevelWindow](#gettoplevelwindow)|擷取最上層視窗。|  
|[CWindow::GetTopWindow](#gettopwindow)|擷取最上層的子視窗。|  
|[CWindow::GetUpdateRect](#getupdaterect)|擷取最小完全圍住更新區域的矩形的座標。|  
|[CWindow::GetUpdateRgn](#getupdatergn)|擷取更新區域，並將它複製到指定的區域。|  
|[CWindow::GetWindow](#getwindow)|擷取指定的視窗。|  
|[CWindow::GetWindowContextHelpId](#getwindowcontexthelpid)|擷取視窗的說明內容識別碼。|  
|[CWindow::GetWindowDC](#getwindowdc)|擷取整個視窗的裝置內容。|  
|[CWindow::GetWindowLong](#getwindowlong)|擷取的 32 位元值的指定位移到額外的視窗記憶體。|  
|[CWindow::GetWindowLongPtr](#getwindowlongptr)|擷取指定的視窗，包括額外的視窗記憶體中指定的位移值的相關資訊。|  
|[CWindow::GetWindowPlacement](#getwindowplacement)|擷取的顯示狀態和位置。|  
|[CWindow::GetWindowProcessID](#getwindowprocessid)|擷取建立視窗的視窗程序的識別項。|  
|[CWindow::GetWindowRect](#getwindowrect)|擷取視窗的週框的大小。|  
|[CWindow::GetWindowRgn](#getwindowrgn)|取得視窗的視窗區域的複本。|  
|[CWindow::GetWindowText](#getwindowtext)|擷取視窗的文字。|  
|[CWindow::GetWindowTextLength](#getwindowtextlength)|擷取視窗的文字的長度。|  
|[CWindow::GetWindowThreadID](#getwindowthreadid)|擷取建立指定之的視窗的執行緒的識別項。|  
|[CWindow::GetWindowWord](#getwindowword)|擷取的 16 位元值的指定位移到額外的視窗記憶體。|  
|[CWindow::GotoDlgCtrl](#gotodlgctrl)|在對話方塊中，為控制項設定鍵盤焦點。|  
|[CWindow::HideCaret](#hidecaret)|隱藏系統游標。|  
|[CWindow::HiliteMenuItem](#hilitemenuitem)|反白顯示，或從最上層功能表項目移除反白顯示。|  
|[CWindow::Invalidate](#invalidate)|使整個工作區失效。|  
|[CWindow::InvalidateRect](#invalidaterect)|使工作區中指定的矩形。|  
|[CWindow::InvalidateRgn](#invalidatergn)|使指定的區域內的用戶端區域。|  
|[CWindow::IsChild](#ischild)|判斷指定的視窗是否為子視窗。|  
|[CWindow::IsDialogMessage](#isdialogmessage)|判斷訊息是否可供指定的對話方塊。|  
|[CWindow::IsDlgButtonChecked](#isdlgbuttonchecked)|決定按鈕的核取狀態。|  
|[CWindow::IsIconic](#isiconic)|決定是否視窗最小化。|  
|[CWindow::IsParentDialog](#isparentdialog)|判斷控制項的父視窗是否為對話方塊視窗。|  
|[CWindow::IsWindow](#iswindow)|判斷指定的視窗控制代碼是否識別現有視窗。|  
|[CWindow::IsWindowEnabled](#iswindowenabled)|判斷輸入是否已啟用視窗。|  
|[CWindow::IsWindowUnicode](#iswindowunicode)|判斷指定的視窗是否為原生的 Unicode 視窗。|  
|[CWindow::IsWindowVisible](#iswindowvisible)|決定視窗的可見性狀態。|  
|[CWindow::IsZoomed](#iszoomed)|決定是否要最大化的視窗。|  
|[CWindow::KillTimer](#killtimer)|終結的計時器事件。|  
|[CWindow::LockWindowUpdate](#lockwindowupdate)|停用或啟用 在視窗中繪製。|  
|[CWindow::MapWindowPoints](#mapwindowpoints)|將一組點視窗的座標空間轉換到另一個視窗的座標空間。|  
|[CWindow::MessageBox](#messagebox)|顯示訊息方塊。|  
|[CWindow::ModifyStyle](#modifystyle)|修改的視窗樣式。|  
|[CWindow::ModifyStyleEx](#modifystyleex)|修改延伸的視窗樣式。|  
|[CWindow::MoveWindow](#movewindow)|變更視窗的大小和位置。|  
|[CWindow::NextDlgCtrl](#nextdlgctrl)|在對話方塊中設定的下一個控制項鍵盤焦點。|  
|[CWindow::OpenClipboard](#openclipboard)|開啟剪貼簿。|  
|[CWindow::PostMessage](#postmessage)|將訊息放在建立視窗的執行緒相關聯的訊息佇列中。 傳回而不需等待的執行緒來處理訊息。|  
|[CWindow::PrevDlgCtrl](#prevdlgctrl)|在對話方塊中上, 一個控制項來設定鍵盤焦點。|  
|[CWindow::Print](#print)|視窗會繪製在指定的裝置內容中的要求。|  
|[CWindow::PrintClient](#printclient)|視窗的工作區會繪製在指定的裝置內容中的要求。|  
|[CWindow::RedrawWindow](#redrawwindow)|更新指定的矩形或工作區中的區域。|  
|[CWindow::ReleaseDC](#releasedc)|釋放裝置內容。|  
|[CWindow::ResizeClient](#resizeclient)|調整視窗的大小。|  
|[CWindow::ScreenToClient](#screentoclient)|將螢幕座標轉換為工作區座標。|  
|[CWindow::ScrollWindow](#scrollwindow)|將指定的用戶端區域的捲動。|  
|[CWindow::ScrollWindowEx](#scrollwindowex)|將額外的功能在指定的用戶端區域的捲動。|  
|[CWindow::SendDlgItemMessage](#senddlgitemmessage)|傳送訊息至控制項。|  
|[CWindow::SendMessage](#sendmessage)|將訊息傳送至視窗，並不會傳回之前處理訊息的視窗程序之後。|  
|[CWindow::SendMessageToDescendants](#sendmessagetodescendants)|將指定之子系的 windows 訊息。|  
|[CWindow::SendNotifyMessage](#sendnotifymessage)|傳送訊息至視窗。 如果呼叫的執行緒，所建立視窗`SendNotifyMessage`等到處理訊息的視窗程序之後才會傳回。 否則，它會立即傳回。|  
|[CWindow::SetActiveWindow](#setactivewindow)|啟用視窗。|  
|[CWindow::SetCapture](#setcapture)|傳送至視窗的所有後續的滑鼠輸入。|  
|[CWindow::SetClipboardViewer](#setclipboardviewer)|將剪貼簿檢視器鏈結中的視窗。|  
|[CWindow::SetDlgCtrlID](#setdlgctrlid)|變更視窗的識別項。|  
|[CWindow::SetDlgItemInt](#setdlgitemint)|變更控制項的文字字串表示的整數值。|  
|[CWindow::SetDlgItemText](#setdlgitemtext)|變更控制項的文字。|  
|[CWindow::SetFocus](#setfocus)|將輸入的焦點設定為視窗。|  
|[CWindow::SetFont](#setfont)|變更視窗的目前字型。|  
|[CWindow::SetHotKey](#sethotkey)|使熱鍵與視窗產生關聯。|  
|[CWindow::SetIcon](#seticon)|變更視窗的大型或小型圖示。|  
|[CWindow::SetMenu](#setmenu)|變更目前的視窗的功能表。|  
|[CWindow::SetParent](#setparent)|變更父視窗。|  
|[CWindow::SetRedraw](#setredraw)|設定或清除重繪旗標。|  
|[CWindow::SetScrollInfo](#setscrollinfo)|設定捲軸上的參數。|  
|[CWindow::SetScrollPos](#setscrollpos)|變更的捲動方塊的位置。|  
|[CWindow::SetScrollRange](#setscrollrange)|變更捲軸列範圍。|  
|[CWindow::SetTimer](#settimer)|建立計時器事件。|  
|[CWindow::SetWindowContextHelpId](#setwindowcontexthelpid)|設定視窗的說明內容識別碼。|  
|[CWindow::SetWindowLong](#setwindowlong)|32 位元值的指定位移設定額外的視窗記憶體。|  
|[CWindow::SetWindowLongPtr](#setwindowlongptr)|指定的視窗中，屬性變更，也會將值設定額外的視窗記憶體中指定的位移。|  
|[CWindow::SetWindowPlacement](#setwindowplacement)|設定顯示狀態和位置。|  
|[CWindow::SetWindowPos](#setwindowpos)|設定大小、 位置和 Z 順序。|  
|[CWindow::SetWindowRgn](#setwindowrgn)|設定視窗的視窗區域。|  
|[CWindow::SetWindowText](#setwindowtext)|變更視窗的文字。|  
|[CWindow::SetWindowWord](#setwindowword)|設定中指定位移的 16 位元值到額外的視窗記憶體。|  
|[CWindow::ShowCaret](#showcaret)|顯示系統游標。|  
|[CWindow::ShowOwnedPopups](#showownedpopups)|顯示或隱藏視窗所擁有的快顯視窗。|  
|[CWindow::ShowScrollBar](#showscrollbar)|顯示或隱藏捲軸。|  
|[CWindow::ShowWindow](#showwindow)|設定視窗的顯示狀態。|  
|[CWindow::ShowWindowAsync](#showwindowasync)|設定不同的執行緒所建立之視窗的顯示狀態。|  
|[CWindow::UpdateWindow](#updatewindow)|更新工作區。|  
|[CWindow::ValidateRect](#validaterect)|驗證指定的矩形內的用戶端區域。|  
|[CWindow::ValidateRgn](#validatergn)|驗證指定的區域內的用戶端區域。|  
|[CWindow::WinHelp](#winhelp)|啟動 Windows 說明。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CWindow::operator HWND](#operator_hwnd)|將轉換`CWindow`物件傳遞給`HWND`。|  
|[CWindow::operator =](#operator_eq)|指派`HWND`到`CWindow`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CWindow::m_hWnd](#m_hwnd)|相關聯的視窗控制代碼`CWindow`物件。|  
|[CWindow::rcDefault](#rcdefault)|包含預設視窗大小。|  
  
## <a name="remarks"></a>備註  
 `CWindow`提供基底功能操作 ATL 中的視窗 許多`CWindow`方法只會包裝 Win32 API 函式的其中一個。 例如，比較的原型`CWindow::ShowWindow`和`ShowWindow`:  
  
|CWindow 方法|Win32 函式|  
|--------------------|--------------------|  
|**BOOL ShowWindow (int** `nCmdShow` **);**|**BOOL ShowWindow( HWND** `hWnd` **, int** `nCmdShow` **);**|  
  
 `CWindow::ShowWindow`呼叫 Win32 函式`ShowWindow`藉由傳遞`CWindow::m_hWnd`的第一個參數。 每個`CWindow`直接包裝 Win32 函式的方法會傳遞`m_hWnd`成員; 因此，大部分的`CWindow`文件會參考您[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  並非每個視窗相關的 Win32 函式會由包裝`CWindow`，並不是每個`CWindow`方法會包裝 Win32 函式。  
  
 `CWindow::m_hWnd`儲存`HWND`識別視窗。 `HWND`附加至您的物件時您︰  
  
-   指定`HWND`中`CWindow`的建構函式。  
  
-   呼叫 `CWindow::Attach`。  
  
-   Use `CWindow`'s **operator =**.  
  
-   建立或子類別化視窗，使用下列類別的其中一個衍生自`CWindow`:  
  
 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)可讓您建立新的視窗或子類別化現有視窗。  
  
 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)實作另一個物件所含的視窗。 您可以建立新的視窗或子類別化現有視窗。  
  
 [CDialogImpl](../../atl/reference/cdialogimpl-class.md)可讓您建立強制回應或非強制回應對話方塊。  
  
 如需 windows 的詳細資訊，請參閱[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595)和後續主題中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需在 ATL 中使用 windows 的詳細資訊，請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-namearrangeiconicwindowsa--cwindowarrangeiconicwindows"></a><a name="arrangeiconicwindows"></a>CWindow::ArrangeIconicWindows  
 排列所有的最小化的子視窗。  
  
```
UINT ArrangeIconicWindows() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ArrangeIconicWindows](http://msdn.microsoft.com/library/windows/desktop/ms632671)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameattacha--cwindowattach"></a><a name="attach"></a>CWindow::Attach  
 會將由視窗附加`hWndNew`到`CWindow`物件。  
  
```
void Attach(HWND hWndNew) throw();
```  
  
### <a name="parameters"></a>參數  
 `hWndNew`  
 [in]視窗控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&1;](../../atl/codesnippet/cpp/cwindow-class_1.cpp)]  
  
##  <a name="a-namebeginpainta--cwindowbeginpaint"></a><a name="beginpaint"></a>CWindow::BeginPaint  
 準備要繪製的視窗。  
  
```
HDC BeginPaint(LPPAINTSTRUCT lpPaint) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[BeginPaint](http://msdn.microsoft.com/library/windows/desktop/dd183362)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&2;](../../atl/codesnippet/cpp/cwindow-class_2.cpp)]  
  
##  <a name="a-namebringwindowtotopa--cwindowbringwindowtotop"></a><a name="bringwindowtotop"></a>CWindow::BringWindowToTop  
 將視窗帶到疊置順序的頂端。  
  
```
BOOL BringWindowToTop() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[BringWindowToTop](http://msdn.microsoft.com/library/windows/desktop/ms632673)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&3;](../../atl/codesnippet/cpp/cwindow-class_3.cpp)]  
  
##  <a name="a-namecenterwindowa--cwindowcenterwindow"></a><a name="centerwindow"></a>CWindow::CenterWindow  
 針對指定的視窗視窗置中對齊。  
  
```
BOOL CenterWindow(HWND hWndCenter = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `hWndCenter`  
 [in]對其中心視窗控制代碼。 如果這個參數是**NULL** （預設值），方法會設定`hWndCenter`至視窗的父視窗是否為子視窗。 否則，它將會設定`hWndCenter`視窗的擁有者視窗。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗是否成功置中，否則**FALSE**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&4;](../../atl/codesnippet/cpp/cwindow-class_4.cpp)]  
  
##  <a name="a-namechangeclipboardchaina--cwindowchangeclipboardchain"></a><a name="changeclipboardchain"></a>CWindow::ChangeClipboardChain  
 從剪貼簿檢視器的鏈結中移除視窗。  
  
```
BOOL ChangeClipboardChain(HWND hWndNewNext) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ChangeClipboardChain](http://msdn.microsoft.com/library/windows/desktop/ms649034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecheckdlgbuttona--cwindowcheckdlgbutton"></a><a name="checkdlgbutton"></a>CWindow::CheckDlgButton  
 指定按鈕的核取狀態變更。  
  
```
BOOL CheckDlgButton(int nIDButton, UINT nCheck) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[CheckDlgButton](http://msdn.microsoft.com/library/windows/desktop/bb761875)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecheckradiobuttona--cwindowcheckradiobutton"></a><a name="checkradiobutton"></a>CWindow::CheckRadioButton  
 檢查指定的選項按鈕。  
  
```
BOOL CheckRadioButton(  
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[CheckRadioButton](http://msdn.microsoft.com/library/windows/desktop/bb761877)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namechildwindowfrompointa--cwindowchildwindowfrompoint"></a><a name="childwindowfrompoint"></a>CWindow::ChildWindowFromPoint  
 擷取包含指定的點的子視窗。  
  
```
HWND ChildWindowFromPoint(POINT point) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ChildWindowFromPoint](http://msdn.microsoft.com/library/windows/desktop/ms632676)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namechildwindowfrompointexa--cwindowchildwindowfrompointex"></a><a name="childwindowfrompointex"></a>CWindow::ChildWindowFromPointEx  
 擷取特定類型的子視窗，其中包含指定的點。  
  
```
HWND ChildWindowFromPoint(POINT point, UINT uFlags) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ChildWindowFromPointEx](http://msdn.microsoft.com/library/windows/desktop/ms632677)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclienttoscreena--cwindowclienttoscreen"></a><a name="clienttoscreen"></a>CWindow::ClientToScreen  
 將工作區座標轉換為螢幕座標。  
  
```
BOOL ClientToScreen(LPPOINT lpPoint) const throw();
BOOL ClientToScreen(LPRECT lpRect) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ClientToScreen](http://msdn.microsoft.com/library/windows/desktop/dd183434)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法的第二個版本可讓您轉換的座標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
##  <a name="a-namecreatea--cwindowcreate"></a><a name="create"></a>CWindow::Create  
 建立視窗。  
  
```
HWND Create(
    LPCTSTR lpstrWndClass,
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpstrWndClass`  
 [in]視窗類別的指標。  
  
 `hWndParent`  
 [in]父系或擁有者的視窗控制代碼。  
  
 `rect`  
 [in]型別的變數[_U_RECT](../../atl/reference/u-rect-class.md)指定視窗的位置。 預設值是**NULL**。 當此參數是**NULL**，值`CWindow::rcDefault`用。  
  
 `szWindowName`  
 [in]指定的視窗名稱。 預設值是**NULL**。  
  
 `dwStyle`  
 [in]視窗樣式。 預設值為 0，表示沒有任何樣式會指定。 如需可能的值，請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwExStyle`  
 [in]延伸的視窗樣式。 預設值為 0，表示沒有任何延伸的樣式會指定。 如需可能的值，請參閱[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `MenuOrID`  
 [in]型別的變數[_U_MENUorID](../../atl/reference/u-menuorid-class.md)指定功能表或視窗識別項的控制代碼。 預設值是 0U。  
  
 `lpCreateParam`  
 包含在視窗建立資料指標[CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功，[新建] 視窗的控制代碼所指定[m_hWnd](#m_hwnd)。 否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 `CWindow::rcDefault`定義為`__declspec(selectany) RECT CWindow::rcDefault = {CW_USEDEFAULT, CW_USEDEFAULT, 0, 0};`。  
  
 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
 **請注意**如果會使用 0 做為值`MenuOrID`參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。  
  
##  <a name="a-namecreatecareta--cwindowcreatecaret"></a><a name="createcaret"></a>CWindow::CreateCaret  
 建立新的圖形，使系統插入號。  
  
```
BOOL CreateCaret(HBITMAP pBitmap) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[CreateCaret](http://msdn.microsoft.com/library/windows/desktop/ms648399)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreategraycareta--cwindowcreategraycaret"></a><a name="creategraycaret"></a>CWindow::CreateGrayCaret  
 建立系統游標的灰色矩形。  
  
```
BOOL CreateGrayCaret(int nWidth, int nHeight) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[CreateCaret](http://msdn.microsoft.com/library/windows/desktop/ms648399)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 傳遞 (HBITMAP) 1 點陣圖控制代碼的 Win32 函式的參數。  
  
##  <a name="a-namecreatesolidcareta--cwindowcreatesolidcaret"></a><a name="createsolidcaret"></a>CWindow::CreateSolidCaret  
 建立系統游標的實心矩形。  
  
```
BOOL CreateSolidCaret(int nWidth, int nHeight) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[CreateCaret](http://msdn.microsoft.com/library/windows/desktop/ms648399)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 傳遞 (HBITMAP) 0 點陣圖控制代碼的 Win32 函式的參數。  
  
##  <a name="a-namecwindowa--cwindowcwindow"></a><a name="cwindow"></a>CWindow::CWindow  
 建構函式。  
  
```
CWindow(HWND hWnd = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]視窗控制代碼。  
  
### <a name="remarks"></a>備註  
 初始化[m_hWnd](#m_hwnd)成員`hWnd`，其預設值是**NULL**。  
  
> [!NOTE]
> `CWindow::CWindow`不會建立視窗。 類別[CWindowImpl](../../atl/reference/cwindowimpl-class.md)， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)，和[CDialogImpl](../../atl/reference/cdialogimpl-class.md) (其中都衍生自`CWindow`) 提供一個方法來建立視窗或對話方塊的方塊，然後指派給`CWindow::m_hWnd`。 您也可以使用[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Win32 函式。  
  
##  <a name="a-namedeferwindowposa--cwindowdeferwindowpos"></a><a name="deferwindowpos"></a>CWindow::DeferWindowPos  
 更新指定的多個視窗位置結構指定的視窗。  
  
```
HDWP DeferWindowPos(  
    HDWP hWinPosInfo,
    HWND hWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT uFlags) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632681)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedestroywindowa--cwindowdestroywindow"></a><a name="destroywindow"></a>CWindow::DestroyWindow  
 終結視窗相關聯`CWindow`物件，然後設定[m_hWnd](#m_hwnd)至**NULL**。  
  
```
BOOL DestroyWindow() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 它不會終結`CWindow`物件本身。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&5;](../../atl/codesnippet/cpp/cwindow-class_5.cpp)]  
  
##  <a name="a-namedetacha--cwindowdetach"></a><a name="detach"></a>CWindow::Detach  
 卸離[m_hWnd](#m_hwnd)從`CWindow`物件，然後設定`m_hWnd`至**NULL**。  
  
```
HWND Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HWND`聯`CWindow`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&6;](../../atl/codesnippet/cpp/cwindow-class_6.cpp)]  
  
##  <a name="a-namedlgdirlista--cwindowdlgdirlist"></a><a name="dlgdirlist"></a>CWindow::DlgDirList  
 清單方塊中填入所有符合指定的路徑或檔案名稱的檔案名稱。  
  
```
int DlgDirList(  
    LPTSTR lpPathSpec,
    int nIDListBox,
    int nIDStaticPath,
    UINT nFileType) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DlgDirList](http://msdn.microsoft.com/library/windows/desktop/bb761366)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedlgdirlistcomboboxa--cwindowdlgdirlistcombobox"></a><a name="dlgdirlistcombobox"></a>CWindow::DlgDirListComboBox  
 下拉式方塊中填入所有符合指定的路徑或檔案名稱的檔案名稱。  
  
```
int DlgDirListComboBox(  
    LPTSTR lpPathSpec,
    int nIDComboBox,
    int nIDStaticPath,
    UINT nFileType) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DlgDirListComboBox](http://msdn.microsoft.com/library/windows/desktop/bb775935)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedlgdirselecta--cwindowdlgdirselect"></a><a name="dlgdirselect"></a>CWindow::DlgDirSelect  
 從清單方塊擷取目前的選取範圍。  
  
```
BOOL DlgDirSelect(  
    LPTSTR lpString,
    int nCount,
    int nIDListBox) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DlgDirSelectEx](http://msdn.microsoft.com/library/windows/desktop/bb761368)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedlgdirselectcomboboxa--cwindowdlgdirselectcombobox"></a><a name="dlgdirselectcombobox"></a>CWindow::DlgDirSelectComboBox  
 從下拉式方塊擷取目前的選取範圍。  
  
```
BOOL DlgDirSelectComboBox(  
    LPTSTR lpString,
    int nCount,
    int nIDComboBox) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DlgDirSelectComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775937)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedragacceptfilesa--cwindowdragacceptfiles"></a><a name="dragacceptfiles"></a>CWindow::DragAcceptFiles  
 暫存器視窗是否會接受拖曳檔案。  
  
```
void DragAcceptFiles(BOOL bAccept = TRUE);
```  
  
### <a name="remarks"></a>備註  
 請參閱[DragAcceptFiles](http://msdn.microsoft.com/library/windows/desktop/bb776406)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedrawmenubara--cwindowdrawmenubar"></a><a name="drawmenubar"></a>CWindow::DrawMenuBar  
 視窗的功能表列來重新繪製。  
  
```
BOOL DrawMenuBar() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[DrawMenuBar](http://msdn.microsoft.com/library/windows/desktop/ms647633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameenablescrollbara--cwindowenablescrollbar"></a><a name="enablescrollbar"></a>CWindow::EnableScrollBar  
 啟用或停用捲軸箭號。  
  
```
BOOL EnableScrollBar(UINT uSBFlags, UINT uArrowFlags = ESB_ENABLE_BOTH) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[EnableScrollBar](http://msdn.microsoft.com/library/windows/desktop/bb787579)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameenablewindowa--cwindowenablewindow"></a><a name="enablewindow"></a>CWindow::EnableWindow  
 啟用或停用輸入。  
  
```
BOOL EnableWindow(BOOL bEnable = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[EnableWindow](http://msdn.microsoft.com/library/windows/desktop/ms646291)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&7;](../../atl/codesnippet/cpp/cwindow-class_7.cpp)]  
  
##  <a name="a-nameendpainta--cwindowendpaint"></a><a name="endpaint"></a>CWindow::EndPaint  
 標記繪製的結束。  
  
```
void EndPaint(LPPAINTSTRUCT lpPaint) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[EndPaint](http://msdn.microsoft.com/library/windows/desktop/dd162598)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&2;](../../atl/codesnippet/cpp/cwindow-class_2.cpp)]  
  
##  <a name="a-nameflashwindowa--cwindowflashwindow"></a><a name="flashwindow"></a>CWindow::FlashWindow  
 閃爍視窗一次。  
  
```
BOOL FlashWindow(BOOL bInvert) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[FlashWindow](http://msdn.microsoft.com/library/windows/desktop/ms679346)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclientrecta--cwindowgetclientrect"></a><a name="getclientrect"></a>CWindow::GetClientRect  
 擷取用戶端區域的座標。  
  
```
BOOL GetClientRect(LPRECT lpRect) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetClientRect](http://msdn.microsoft.com/library/windows/desktop/ms633503)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&8;](../../atl/codesnippet/cpp/cwindow-class_8.cpp)]  
  
##  <a name="a-namegetdca--cwindowgetdc"></a><a name="getdc"></a>CWindow::GetDC  
 擷取用戶端區域的裝置內容。  
  
```
HDC GetDC() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&9;](../../atl/codesnippet/cpp/cwindow-class_9.cpp)]  
  
##  <a name="a-namegetdcexa--cwindowgetdcex"></a><a name="getdcex"></a>CWindow::GetDCEx  
 擷取用戶端區域的裝置內容，並允許裁剪選項。  
  
```
HDC GetDCEx(HRGN hRgnClip, DWORD flags) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDCEx](http://msdn.microsoft.com/library/windows/desktop/dd144873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdescendantwindowa--cwindowgetdescendantwindow"></a><a name="getdescendantwindow"></a>CWindow::GetDescendantWindow  
 尋找指定的識別項所指定的子系視窗。  
  
```
HWND GetDescendantWindow(int nID) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 [in]要擷取的子系視窗識別項。  
  
### <a name="return-value"></a>傳回值  
 子系的視窗控制代碼。  
  
### <a name="remarks"></a>備註  
 `GetDescendantWindow`搜尋整個樹狀結構的子視窗，不只會直接子系的視窗。  
  
##  <a name="a-namegetdlgcontrola--cwindowgetdlgcontrol"></a><a name="getdlgcontrol"></a>CWindow::GetDlgControl  
 呼叫此函式可取得的複合控制項的控制項裝載對話方塊裝載 ActiveX 控制項介面的指標。  
  
```
HRESULT GetDlgControl(  
    int nID,
    REFIID iid,
    void** ppCtrl) throw();
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 [in]正在擷取控制項的資源 ID。  
  
 `iid`  
 [in]您想要從控制項取得的介面識別碼。  
  
 *ppCtrl*  
 [out]介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`成功或任何有效的錯誤`HRESULT`。 例如，此函數會傳回**E_FAIL**如果所指定的控制項`nID`找不到，它會傳回**E_NOINTERFACE**如果可以找到控制項，但它不支援指定的介面`iid`。  
  
### <a name="remarks"></a>備註  
 使用這個指標，您可以在介面上呼叫方法。  
  
##  <a name="a-namegetdlgctrlida--cwindowgetdlgctrlid"></a><a name="getdlgctrlid"></a>CWindow::GetDlgCtrlID  
 擷取 （僅適用於子 windows) 視窗中的識別項。  
  
```
int GetDlgCtrlID() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDlgCtrlID](http://msdn.microsoft.com/library/windows/desktop/ms645478)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdlghosta--cwindowgetdlghost"></a><a name="getdlghost"></a>CWindow::GetDlgHost  
 擷取 ATL 控制項裝載容器的介面指標。  
  
```
HRESULT GetDlgHost(  
    int nID,
    REFIID iid,
    void** ppHost) throw();
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 [in]正在擷取控制項的資源 ID。  
  
 `iid`  
 [in]您想要從控制項取得的介面識別碼。  
  
 *ppHost*  
 [out]介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`如果所指定視窗`iid`是控制項容器，且無法擷取要求的介面。 傳回**E_FAIL**如果視窗不是控制項的容器，或如果無法擷取要求的介面。 如果找不到具有指定識別碼的視窗，然後傳回值會等於 HRESULT_FROM_WIN32(ERROR_CONTROL_ID_NOT_FOUND)。  
  
### <a name="remarks"></a>備註  
 使用這個指標，您可以在介面上呼叫方法。  
  
##  <a name="a-namegetdlgitema--cwindowgetdlgitem"></a><a name="getdlgitem"></a>CWindow::GetDlgItem  
 擷取指定的子視窗。  
  
```
HWND GetDlgItem(int nID) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDlgItem](http://msdn.microsoft.com/library/windows/desktop/ms645481)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdlgiteminta--cwindowgetdlgitemint"></a><a name="getdlgitemint"></a>CWindow::GetDlgItemInt  
 將轉譯成整數的控制項的文字。  
  
```
UINT GetDlgItemInt(  
    int nID,
    BOOL* lpTrans = NULL,
    BOOL bSigned = TRUE) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDlgItemInt](http://msdn.microsoft.com/library/windows/desktop/ms645485)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdlgitemtexta--cwindowgetdlgitemtext"></a><a name="getdlgitemtext"></a>CWindow::GetDlgItemText  
 擷取控制項的文字。  
  
```
UINT GetDlgItemText(  
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const throw();

BOOL GetDlgItemText(  
    int nID,
    BSTR& bstrText) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetDlgItemText](http://msdn.microsoft.com/library/windows/desktop/ms645489)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 這個方法的第二個版本可讓您複製到控制項的文字`BSTR`。 這一版傳回**TRUE**文字是否順利複製，否則**FALSE**。  
  
##  <a name="a-namegetexstylea--cwindowgetexstyle"></a><a name="getexstyle"></a>CWindow::GetExStyle  
 擷取視窗的延伸的視窗樣式。  
  
```
DWORD GetExStyle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 在視窗的延伸樣式。  
  
### <a name="remarks"></a>備註  
 若要擷取一般的視窗樣式，請呼叫[GetStyle](#getstyle)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&10;](../../atl/codesnippet/cpp/cwindow-class_10.cpp)]  
  
##  <a name="a-namegetfonta--cwindowgetfont"></a><a name="getfont"></a>CWindow::GetFont  
 藉由傳送擷取視窗的目前字型[WM_GETFONT](http://msdn.microsoft.com/library/windows/desktop/ms632624)至視窗的訊息。  
  
```
HFONT GetFont() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 字型的控制代碼。  
  
##  <a name="a-namegethotkeya--cwindowgethotkey"></a><a name="gethotkey"></a>CWindow::GetHotKey  
 決定熱鍵與視窗相關聯，藉由傳送**WM_GETHOTKEY**訊息。  
  
```
DWORD GetHotKey() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 虛擬按鍵碼和修飾詞的熱鍵與視窗相關聯。 如需可能的修飾詞的清單，請參閱[WM_GETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646278)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.。  
  
##  <a name="a-namegeticona--cwindowgeticon"></a><a name="geticon"></a>CWindow::GetIcon  
 擷取視窗的大型或小型圖示的控制代碼。  
  
```
HICON GetIcon(BOOL bBigIcon = TRUE) const;
```  
  
### <a name="parameters"></a>參數  
 `bBigIcon`  
 [in]如果**TRUE** （預設值） 方法會傳回大型圖示。 否則，它會傳回之小圖示。  
  
### <a name="return-value"></a>傳回值  
 將圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
 `GetIcon`傳送[WM_GETICON](http://msdn.microsoft.com/library/windows/desktop/ms632625)至視窗的訊息。  
  
##  <a name="a-namegetlastactivepopupa--cwindowgetlastactivepopup"></a><a name="getlastactivepopup"></a>CWindow::GetLastActivePopup  
 擷取最近使用的快顯視窗。  
  
```
HWND GetLastActivePopup() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetLastActivePopup](http://msdn.microsoft.com/library/windows/desktop/ms633507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmenua--cwindowgetmenu"></a><a name="getmenu"></a>CWindow::GetMenu  
 擷取視窗的功能表。  
  
```
HMENU GetMenu() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetMenu](http://msdn.microsoft.com/library/windows/desktop/ms647640)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnextdlggroupitema--cwindowgetnextdlggroupitem"></a><a name="getnextdlggroupitem"></a>CWindow::GetNextDlgGroupItem  
 擷取群組內的控制項的上一個或下一個控制項。  
  
```
HWND GetNextDlgGroupItem(HWND hWndCtl, BOOL bPrevious = FALSE) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetNextDlgGroupItem](http://msdn.microsoft.com/library/windows/desktop/ms645492)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnextdlgtabitema--cwindowgetnextdlgtabitem"></a><a name="getnextdlgtabitem"></a>CWindow::GetNextDlgTabItem  
 擷取上一個或下一個控制項有**WS_TABSTOP**樣式。  
  
```
HWND GetNextDlgTabItem(HWND hWndCtl, BOOL bPrevious = FALSE) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetNextDlgTabItem](http://msdn.microsoft.com/library/windows/desktop/ms645495)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetparenta--cwindowgetparent"></a><a name="getparent"></a>CWindow::GetParent  
 擷取直屬父視窗。  
  
```
HWND GetParent() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetParent](http://msdn.microsoft.com/library/windows/desktop/ms633510)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&11;](../../atl/codesnippet/cpp/cwindow-class_11.cpp)]  
  
##  <a name="a-namegetscrollinfoa--cwindowgetscrollinfo"></a><a name="getscrollinfo"></a>CWindow::GetScrollInfo  
 擷取捲軸的參數。  
  
```
BOOL GetScrollInfo(int nBar, LPSCROLLINFO lpScrollInfo) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetScrollInfo](http://msdn.microsoft.com/library/windows/desktop/bb787583)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetscrollposa--cwindowgetscrollpos"></a><a name="getscrollpos"></a>CWindow::GetScrollPos  
 擷取的捲動方塊的位置。  
  
```
int GetScrollPos(int nBar) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetscrollrangea--cwindowgetscrollrange"></a><a name="getscrollrange"></a>CWindow::GetScrollRange  
 擷取捲軸列範圍。  
  
```
BOOL GetScrollRange(  
    int nBar,
    LPINT lpMinPos,
    LPINT lpMaxPos) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetScrollRange](http://msdn.microsoft.com/library/windows/desktop/bb787587)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetstylea--cwindowgetstyle"></a><a name="getstyle"></a>CWindow::GetStyle  
 擷取視窗的視窗樣式。  
  
```
DWORD GetStyle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 視窗樣式。  
  
### <a name="remarks"></a>備註  
 若要擷取的延伸的視窗樣式，請呼叫[GetExStyle](#getexstyle)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&12;](../../atl/codesnippet/cpp/cwindow-class_12.cpp)]  
  
##  <a name="a-namegetsystemmenua--cwindowgetsystemmenu"></a><a name="getsystemmenu"></a>CWindow::GetSystemMenu  
 建立一份要修改的 [系統] 功能表。  
  
```
HMENU GetSystemMenu(BOOL bRevert) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetSystemMenu](http://msdn.microsoft.com/library/windows/desktop/ms647985)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettoplevelparenta--cwindowgettoplevelparent"></a><a name="gettoplevelparent"></a>CWindow::GetTopLevelParent  
 擷取視窗的最上層的父視窗。  
  
```
HWND GetTopLevelParent() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 最上層父視窗控制代碼。  
  
##  <a name="a-namegettoplevelwindowa--cwindowgettoplevelwindow"></a><a name="gettoplevelwindow"></a>CWindow::GetTopLevelWindow  
 擷取視窗的最上層父系或擁有者視窗。  
  
```
HWND GetTopLevelWindow() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 最上層視窗控制代碼。  
  
##  <a name="a-namegettopwindowa--cwindowgettopwindow"></a><a name="gettopwindow"></a>CWindow::GetTopWindow  
 擷取最上層的子視窗。  
  
```
HWND GetTopWindow() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetTopWindow](http://msdn.microsoft.com/library/windows/desktop/ms633514)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&13;](../../atl/codesnippet/cpp/cwindow-class_13.cpp)]  
  
##  <a name="a-namegetupdaterecta--cwindowgetupdaterect"></a><a name="getupdaterect"></a>CWindow::GetUpdateRect  
 擷取最小完全圍住更新區域的矩形的座標。  
  
```
BOOL GetUpdateRect(LPRECT lpRect, BOOL bErase = FALSE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetUpdateRect](http://msdn.microsoft.com/library/windows/desktop/dd144943)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetupdatergna--cwindowgetupdatergn"></a><a name="getupdatergn"></a>CWindow::GetUpdateRgn  
 擷取更新區域，並將它複製到指定的區域。  
  
```
int GetUpdateRgn(HRGN hRgn, BOOL bErase = FALSE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetUpdateRgn](http://msdn.microsoft.com/library/windows/desktop/dd144944)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowa--cwindowgetwindow"></a><a name="getwindow"></a>CWindow::GetWindow  
 擷取指定的視窗。  
  
```
HWND GetWindow(UINT nCmd) const throw();
```  
  
### <a name="remarks"></a>備註  
 See `GetWindow` in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetwindowcontexthelpida--cwindowgetwindowcontexthelpid"></a><a name="getwindowcontexthelpid"></a>CWindow::GetWindowContextHelpId  
 擷取視窗的說明內容識別碼。  
  
```
DWORD GetWindowContextHelpId() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowContextHelpId](http://msdn.microsoft.com/library/windows/desktop/bb776429)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowdca--cwindowgetwindowdc"></a><a name="getwindowdc"></a>CWindow::GetWindowDC  
 擷取整個視窗的裝置內容。  
  
```
HDC GetWindowDC() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&14;](../../atl/codesnippet/cpp/cwindow-class_14.cpp)]  
  
##  <a name="a-namegetwindowlonga--cwindowgetwindowlong"></a><a name="getwindowlong"></a>CWindow::GetWindowLong  
 擷取的 32 位元值的指定位移到額外的視窗記憶體。  
  
```
LONG GetWindowLong(int nIndex) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  若要撰寫與 32 位元和 64 位元版本的 Windows 相容的程式碼，使用[CWindow::GetWindowLongPtr](#getwindowlongptr)。  
  
##  <a name="a-namegetwindowlongptra--cwindowgetwindowlongptr"></a><a name="getwindowlongptr"></a>CWindow::GetWindowLongPtr  
 擷取指定的視窗，包括額外的視窗記憶體中指定的位移值的相關資訊。  
  
```
LONG_PTR GetWindowLongPtr(int nIndex) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowLongPtr](http://msdn.microsoft.com/library/windows/desktop/ms633585)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您要擷取的指標或控制代碼，這個函數會取代`CWindow::GetWindowLong`方法。  
  
> [!NOTE]
>  指標和控制代碼為 32 位元 windows 32 位元和 64 位元 Windows 上的 64 位元。  
  
 若要撰寫與 32 位元和 64 位元版本的 Windows 相容的程式碼，使用`CWindow::GetWindowLongPtr`。  
  
##  <a name="a-namegetwindowplacementa--cwindowgetwindowplacement"></a><a name="getwindowplacement"></a>CWindow::GetWindowPlacement  
 擷取的顯示狀態和位置。  
  
```
BOOL GetWindowPlacement(WINDOWPLACEMENT FAR* lpwndpl) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowPlacement](http://msdn.microsoft.com/library/windows/desktop/ms633518)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowprocessida--cwindowgetwindowprocessid"></a><a name="getwindowprocessid"></a>CWindow::GetWindowProcessID  
 擷取建立視窗的視窗程序的識別項。  
  
```
DWORD GetWindowProcessID() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowThreadProcessID](http://msdn.microsoft.com/library/windows/desktop/ms633522)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&15;](../../atl/codesnippet/cpp/cwindow-class_15.cpp)]  
  
##  <a name="a-namegetwindowrecta--cwindowgetwindowrect"></a><a name="getwindowrect"></a>CWindow::GetWindowRect  
 擷取視窗的週框的大小。  
  
```
BOOL GetWindowRect(LPRECT lpRect) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowRect](http://msdn.microsoft.com/library/windows/desktop/ms633519)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowrgna--cwindowgetwindowrgn"></a><a name="getwindowrgn"></a>CWindow::GetWindowRgn  
 取得視窗的視窗區域的複本。  
  
```
int GetWindowRgn(HRGN hRgn) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowRgn](http://msdn.microsoft.com/library/windows/desktop/dd144950)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowtexta--cwindowgetwindowtext"></a><a name="getwindowtext"></a>CWindow::GetWindowText  
 擷取視窗的文字。  
  
```
int GetWindowText(LPTSTR lpszStringBuf, int nMaxCount) const throw();
BOOL GetWindowText(BSTR& bstrText) throw();
int GetWindowText(CSimpleString& strText) const;
```  
  
### <a name="parameters"></a>參數  
 `lpszStringBuf`  
 要寫入視窗文字的緩衝區。  
  
 `nMaxCount`  
 緩衝區大小以字元為單位，同時也是最大的寫入字元數。  
  
 `bstrText`  
 視窗文字儲存所在的 `BSTR`。  
  
 `strText`  
 視窗文字儲存所在的 `CString`。  
  
### <a name="return-value"></a>傳回值  
 如果成功地複製文字，則傳回值是**TRUE**; 否則傳回的值是**FALSE**。  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowText](http://msdn.microsoft.com/library/windows/desktop/ms633520)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法的第二個版本可讓您儲存中的文字`BSTR`; 第三個版本可讓您儲存中的結果[CString](../../atl-mfc-shared/reference/cstringt-class.md)，因為`CSimpleString`是基底類別`CString`。  
  
##  <a name="a-namegetwindowtextlengtha--cwindowgetwindowtextlength"></a><a name="getwindowtextlength"></a>CWindow::GetWindowTextLength  
 擷取視窗的文字的長度。  
  
```
int GetWindowTextLength() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowTextLength](http://msdn.microsoft.com/library/windows/desktop/ms633521)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowthreadida--cwindowgetwindowthreadid"></a><a name="getwindowthreadid"></a>CWindow::GetWindowThreadID  
 擷取建立指定之的視窗的執行緒的識別項。  
  
```
DWORD GetWindowThreadID() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowThreadProcessID](http://msdn.microsoft.com/library/windows/desktop/ms633522)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&16;](../../atl/codesnippet/cpp/cwindow-class_16.cpp)]  
  
##  <a name="a-namegetwindowworda--cwindowgetwindowword"></a><a name="getwindowword"></a>CWindow::GetWindowWord  
 擷取的 16 位元值的指定位移到額外的視窗記憶體。  
  
```
WORD GetWindowWord(int nIndex) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegotodlgctrla--cwindowgotodlgctrl"></a><a name="gotodlgctrl"></a>CWindow::GotoDlgCtrl  
 在對話方塊中，為控制項設定鍵盤焦點。  
  
```
void GotoDlgCtrl(HWND hWndCtrl) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[WM_NEXTDLGCTL](http://msdn.microsoft.com/library/windows/desktop/ms645432)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namehidecareta--cwindowhidecaret"></a><a name="hidecaret"></a>CWindow::HideCaret  
 隱藏系統游標。  
  
```
BOOL HideCaret() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[HideCaret](http://msdn.microsoft.com/library/windows/desktop/ms648403)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&17;](../../atl/codesnippet/cpp/cwindow-class_17.cpp)]  
  
##  <a name="a-namehilitemenuitema--cwindowhilitemenuitem"></a><a name="hilitemenuitem"></a>CWindow::HiliteMenuItem  
 反白顯示，或從最上層功能表項目移除反白顯示。  
  
```
BOOL HiliteMenuItem(  
    HMENU hMenu,
    UINT uHiliteItem,
    UINT uHilite) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[HiliteMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647986)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinvalidatea--cwindowinvalidate"></a><a name="invalidate"></a>CWindow::Invalidate  
 使整個工作區失效。  
  
```
BOOL Invalidate(BOOL bErase = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[InvalidateRect](http://msdn.microsoft.com/library/windows/desktop/dd145002)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 傳遞**NULL**的`RECT`參數`InvalidateRect`Win32 函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&18;](../../atl/codesnippet/cpp/cwindow-class_18.cpp)]  
  
##  <a name="a-nameinvalidaterecta--cwindowinvalidaterect"></a><a name="invalidaterect"></a>CWindow::InvalidateRect  
 使工作區中指定的矩形。  
  
```
BOOL InvalidateRect(LPCRECT lpRect, BOOL bErase = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[InvalidateRect](http://msdn.microsoft.com/library/windows/desktop/dd145002)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinvalidatergna--cwindowinvalidatergn"></a><a name="invalidatergn"></a>CWindow::InvalidateRgn  
 使指定的區域內的用戶端區域。  
  
```
void InvalidateRgn(HRGN hRgn, BOOL bErase = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[InvalidateRgn](http://msdn.microsoft.com/library/windows/desktop/dd145003)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 指定`void`傳回型別，而`InvalidateRgn`Win32 函式一定會傳回**TRUE**。  
  
##  <a name="a-nameischilda--cwindowischild"></a><a name="ischild"></a>CWindow::IsChild  
 判斷指定的視窗是否為子視窗。  
  
```
BOOL IsChild(const HWND hWnd) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsChild](http://msdn.microsoft.com/library/windows/desktop/ms633524)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisdialogmessagea--cwindowisdialogmessage"></a><a name="isdialogmessage"></a>CWindow::IsDialogMessage  
 判斷訊息是否可供指定的對話方塊。  
  
```
BOOL IsDialogMessage(LPMSG lpMsg) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsDialogMessage](http://msdn.microsoft.com/library/windows/desktop/ms645498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisdlgbuttoncheckeda--cwindowisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>CWindow::IsDlgButtonChecked  
 決定按鈕的核取狀態。  
  
```
UINT IsDlgButtonChecked(int nIDButton) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsDlgButtonChecked](http://msdn.microsoft.com/library/windows/desktop/bb761879)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisiconica--cwindowisiconic"></a><a name="isiconic"></a>CWindow::IsIconic  
 決定是否視窗最小化。  
  
```
BOOL IsIconic() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsIconic](http://msdn.microsoft.com/library/windows/desktop/ms633527)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&19;](../../atl/codesnippet/cpp/cwindow-class_19.cpp)]  
  
##  <a name="a-nameisparentdialoga--cwindowisparentdialog"></a><a name="isparentdialog"></a>CWindow::IsParentDialog  
 判斷控制項的父視窗是否為對話方塊視窗。  
  
```
BOOL IsParentDialog() throw();
```  
  
### <a name="return-value"></a>傳回值  
 會傳回 TRUE 如果父視窗 對話方塊中，FALSE 否則。  
  
##  <a name="a-nameiswindowa--cwindowiswindow"></a><a name="iswindow"></a>CWindow::IsWindow  
 判斷指定的視窗控制代碼是否識別現有視窗。  
  
```
BOOL IsWindow() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsWindow](http://msdn.microsoft.com/library/windows/desktop/ms633528)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&20;](../../atl/codesnippet/cpp/cwindow-class_20.cpp)]  
  
##  <a name="a-nameiswindowenableda--cwindowiswindowenabled"></a><a name="iswindowenabled"></a>CWindow::IsWindowEnabled  
 判斷輸入是否已啟用視窗。  
  
```
BOOL IsWindowEnabled() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsWindowEnabled](http://msdn.microsoft.com/library/windows/desktop/ms646303)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&21;](../../atl/codesnippet/cpp/cwindow-class_21.cpp)]  
  
##  <a name="a-nameiswindowvisiblea--cwindowiswindowvisible"></a><a name="iswindowvisible"></a>CWindow::IsWindowVisible  
 決定視窗的可見性狀態。  
  
```
BOOL IsWindowVisible() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsWindowVisible](http://msdn.microsoft.com/library/windows/desktop/ms633530)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&22;](../../atl/codesnippet/cpp/cwindow-class_22.cpp)]  
  
##  <a name="a-nameiswindowunicodea--cwindowiswindowunicode"></a><a name="iswindowunicode"></a>CWindow::IsWindowUnicode  
 判斷指定的視窗是否為原生的 Unicode 視窗。  
  
```
BOOL IsWindowUnicode() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsWindowUnicode](http://msdn.microsoft.com/library/windows/desktop/ms633529)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&23;](../../atl/codesnippet/cpp/cwindow-class_23.cpp)]  
  
##  <a name="a-nameiszoomeda--cwindowiszoomed"></a><a name="iszoomed"></a>CWindow::IsZoomed  
 決定是否要最大化的視窗。  
  
```
BOOL IsZoomed() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IsZoomed](http://msdn.microsoft.com/library/windows/desktop/ms633531)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namekilltimera--cwindowkilltimer"></a><a name="killtimer"></a>CWindow::KillTimer  
 終結所建立的計時器事件`CWindow::SetTimer`。  
  
```
BOOL KillTimer(UINT nIDEvent) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[KillTimer](http://msdn.microsoft.com/library/windows/desktop/ms644903)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namelockwindowupdatea--cwindowlockwindowupdate"></a><a name="lockwindowupdate"></a>CWindow::LockWindowUpdate  
 停用或啟用視窗中繪製呼叫[LockWindowUpdate](http://msdn.microsoft.com/library/windows/desktop/dd145034) Win32 函式。  
  
```
BOOL LockWindowUpdate(BOOL bLock = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `bLock`  
 [in]如果**TRUE** （預設值），將鎖定視窗。 否則，將會解除鎖定。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗是否已成功鎖定，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果`bLock`是**TRUE**，這個方法會傳遞[m_hWnd](#m_hwnd) Win32 函式; 否則它會傳遞**NULL**。  
  
##  <a name="a-namemhwnda--cwindowmhwnd"></a><a name="m_hwnd"></a>CWindow::m_hWnd  
 包含與關聯的視窗控制代碼`CWindow`物件。  
  
```
HWND m_hWnd throw() throw();
```  
  
##  <a name="a-namemapwindowpointsa--cwindowmapwindowpoints"></a><a name="mapwindowpoints"></a>CWindow::MapWindowPoints  
 將一組點視窗的座標空間轉換到另一個視窗的座標空間。  
  
```
int MapWindowPoints(  
    HWND hWndTo,
    LPPOINT lpPoint,
    UINT nCount) const throw();

int MapWindowPoints(  
    HWND hWndTo,
    LPRECT lpRect) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[MapWindowPoints](http://msdn.microsoft.com/library/windows/desktop/dd145046)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法的第二個版本可讓您轉換的座標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
##  <a name="a-namemessageboxa--cwindowmessagebox"></a><a name="messagebox"></a>CWindow::MessageBox  
 顯示訊息方塊。  
  
```
int MessageBox(  
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = NULL,
    UINT nType = MB_OK) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&24;](../../atl/codesnippet/cpp/cwindow-class_24.cpp)]  
  
##  <a name="a-namemodifystylea--cwindowmodifystyle"></a><a name="modifystyle"></a>CWindow::ModifyStyle  
 修改的視窗樣式`CWindow`物件。  
  
```
BOOL ModifyStyle(  
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwRemove`  
 [in]指定要移除樣式修改期間的視窗樣式。  
  
 `dwAdd`  
 [in]指定要加入樣式修改期間的視窗樣式。  
  
 `nFlags`  
 [in]視窗定位旗標。 如需可能的值，請參閱[SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗樣式是修改過的否則如果**FALSE**。  
  
### <a name="remarks"></a>備註  
 加入或移除樣式可以結合使用位元 OR (|) 運算子。 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關可用的視窗樣式資訊。  
  
 如果`nFlags`是零，`ModifyStyle`呼叫 Win32 函式`SetWindowPos`，並且藉由合併重繪視窗`nFlags`具有下列四個旗標︰  
  
- `SWP_NOSIZE`保留目前的大小。  
  
- `SWP_NOMOVE`保留目前的位置。  
  
- `SWP_NOZORDER`會保留目前的 Z 順序。  
  
- `SWP_NOACTIVATE`無法啟動視窗。  
  
 若要修改之視窗的延伸樣式，請呼叫[ModifyStyleEx](#modifystyleex)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&25;](../../atl/codesnippet/cpp/cwindow-class_25.cpp)]  
  
##  <a name="a-namemodifystyleexa--cwindowmodifystyleex"></a><a name="modifystyleex"></a>CWindow::ModifyStyleEx  
 修改的延伸的視窗樣式`CWindow`物件。  
  
```
BOOL ModifyStyleEx(  
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwRemove`  
 [in]指定要移除樣式修改期間的延伸的樣式。  
  
 `dwAdd`  
 [in]指定要加入樣式修改期間的延伸的樣式。  
  
 `nFlags`  
 [in]視窗定位旗標。 如需可能的值，請參閱[SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**延伸的視窗樣式是修改過的否則如果**FALSE**。  
  
### <a name="remarks"></a>備註  
 加入或移除樣式可以結合使用位元 OR (|) 運算子。 請參閱[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有關可延伸樣式。  
  
 如果`nFlags`是零，`ModifyStyleEx`呼叫 Win32 函式`SetWindowPos`，並且藉由合併重繪視窗`nFlags`具有下列四個旗標︰  
  
- `SWP_NOSIZE`保留目前的大小。  
  
- `SWP_NOMOVE`保留目前的位置。  
  
- `SWP_NOZORDER`會保留目前的 Z 順序。  
  
- `SWP_NOACTIVATE`無法啟動視窗。  
  
 若要修改 windows 使用一般的視窗樣式，請呼叫[ModifyStyle](#modifystyle)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&26;](../../atl/codesnippet/cpp/cwindow-class_26.cpp)]  
  
##  <a name="a-namemovewindowa--cwindowmovewindow"></a><a name="movewindow"></a>CWindow::MoveWindow  
 變更視窗的大小和位置。  
  
```
BOOL MoveWindow(  
    int x,
    int y,
    int nWidth,
    int nHeight,
    BOOL bRepaint = TRUE) throw();

BOOL MoveWindow(  
    LPCRECT lpRect,
    BOOL bRepaint = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 最上層視窗物件的 x 和 y 的參數是相對於螢幕左上角。 子視窗物件，它們是相對於父視窗工作區的左上角。  
  
 這個方法的第二個版本會使用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，以決定視窗的新位置、 寬度和高度。  
  
##  <a name="a-namenextdlgctrla--cwindownextdlgctrl"></a><a name="nextdlgctrl"></a>CWindow::NextDlgCtrl  
 在對話方塊中設定的下一個控制項鍵盤焦點。  
  
```
void NextDlgCtrl() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[WM_NEXTDLGCTL](http://msdn.microsoft.com/library/windows/desktop/ms645432)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameopenclipboarda--cwindowopenclipboard"></a><a name="openclipboard"></a>CWindow::OpenClipboard  
 開啟剪貼簿。  
  
```
BOOL OpenClipboard() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoperatorhwnda--cwindowoperator-hwnd"></a><a name="operator_hwnd"></a>CWindow::operator HWND  
 將轉換`CWindow`物件傳遞給`HWND`。  
  
```  
operator HWND() const throw();
```  
  
##  <a name="a-nameoperatoreqa--cwindowoperator-"></a><a name="operator_eq"></a>CWindow::operator =  
 指派`HWND`至`CWindow`藉由設定物件[m_hWnd](#m_hwnd)成員`hWnd`。  
  
```
CWindow& operator= (HWND hWnd) throw();
```  
  
##  <a name="a-namepostmessagea--cwindowpostmessage"></a><a name="postmessage"></a>CWindow::PostMessage  
 將訊息放在建立視窗的執行緒相關聯的訊息佇列中。  
  
```
BOOL PostMessage(  
    UINT message,
    WPARAM wParam = 0,
    LPARAM lParam = 0) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[PostMessage](http://msdn.microsoft.com/library/windows/desktop/ms644944)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 傳回而不需等待的執行緒來處理訊息。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&27;](../../atl/codesnippet/cpp/cwindow-class_27.cpp)]  
  
##  <a name="a-nameprevdlgctrla--cwindowprevdlgctrl"></a><a name="prevdlgctrl"></a>CWindow::PrevDlgCtrl  
 在對話方塊中上, 一個控制項來設定鍵盤焦點。  
  
```
void PrevDlgCtrl() const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[WM_NEXTDLGCTL](http://msdn.microsoft.com/library/windows/desktop/ms645432)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameprinta--cwindowprint"></a><a name="print"></a>CWindow::Print  
 傳送[WM_PRINT](http://msdn.microsoft.com/library/windows/desktop/dd145216)要求，它本身的內容中繪製指定的裝置 視窗的訊息。  
  
```
void Print(HDC hDC, DWORD dwFlags) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDC`  
 [in]裝置內容控制代碼。  
  
 `dwFlags`  
 [in]指定繪圖選項。 您可以結合一或多個下列旗標︰  
  
- `PRF_CHECKVISIBLE`只有當它會顯示繪製視窗。  
  
- `PRF_CHILDREN`繪製所有可見的子視窗。  
  
- `PRF_CLIENT`繪製視窗的工作區。  
  
- `PRF_ERASEBKGND`清除背景繪製視窗之前。  
  
- `PRF_NONCLIENT`繪製視窗的非工作區。  
  
- `PRF_OWNED`繪製所有已擁有的 windows。  
  
##  <a name="a-nameprintclienta--cwindowprintclient"></a><a name="printclient"></a>CWindow::PrintClient  
 傳送[WM_PRINTCLIENT](http://msdn.microsoft.com/library/windows/desktop/dd145217)要求它繪製指定的裝置內容中的工作區視窗訊息。  
  
```
void PrintClient(HDC hDC, DWORD dwFlags) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDC`  
 [in]裝置內容控制代碼。  
  
 `dwFlags`  
 [in]指定繪圖選項。 您可以結合一或多個下列旗標︰  
  
- `PRF_CHECKVISIBLE`只有當它會顯示繪製視窗。  
  
- `PRF_CHILDREN`繪製所有可見的子視窗。  
  
- `PRF_CLIENT`繪製視窗的工作區。  
  
- `PRF_ERASEBKGND`清除背景繪製視窗之前。  
  
- `PRF_NONCLIENT`繪製視窗的非工作區。  
  
- `PRF_OWNED`繪製所有已擁有的 windows。  
  
##  <a name="a-namercdefaulta--cwindowrcdefault"></a><a name="rcdefault"></a>CWindow::rcDefault  
 包含預設視窗大小。  
  
```
static RECT rcDefault;
```  
  
##  <a name="a-nameredrawwindowa--cwindowredrawwindow"></a><a name="redrawwindow"></a>CWindow::RedrawWindow  
 更新指定的矩形或工作區中的區域。  
  
```
BOOL RedrawWindow(  
    LPCRECT lpRectUpdate = NULL,
    HRGN hRgnUpdate = NULL,
    UINT flags = RDW_INVALIDATE | RDW_UPDATENOW | RDW_ERASE);

throw()
```  
  
### <a name="remarks"></a>備註  
 請參閱[RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&28;](../../atl/codesnippet/cpp/cwindow-class_28.cpp)]  
  
##  <a name="a-namereleasedca--cwindowreleasedc"></a><a name="releasedc"></a>CWindow::ReleaseDC  
 釋放裝置內容。  
  
```
int ReleaseDC(HDC hDC);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&9;](../../atl/codesnippet/cpp/cwindow-class_9.cpp)]  
  
##  <a name="a-nameresizeclienta--cwindowresizeclient"></a><a name="resizeclient"></a>CWindow::ResizeClient  
 將視窗調整至指定的用戶端區域的大小。  
  
```
BOOL ResizeClient(  
    int nWidth,
    int nHeight,
    BOOL bRedraw = FALSE) throw();
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 新視窗寬度的像素為單位。  
  
 `nHeight`  
 新視窗高度的像素為單位。  
  
 `bRedraw`  
 旗標，指出是否要重繪其變更。 預設值是**FALSE**，指出視窗不會重新繪製的變更。  
  
##  <a name="a-namescreentoclienta--cwindowscreentoclient"></a><a name="screentoclient"></a>CWindow::ScreenToClient  
 將螢幕座標轉換為工作區座標。  
  
```
BOOL ScreenToClient(LPPOINT lpPoint) const throw();
BOOL ScreenToClient(LPRECT lpRect) const throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ScreenToClient](http://msdn.microsoft.com/library/windows/desktop/dd162952)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法的第二個版本可讓您轉換的座標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
##  <a name="a-namescrollwindowa--cwindowscrollwindow"></a><a name="scrollwindow"></a>CWindow::ScrollWindow  
 將指定的用戶端區域的捲動。  
  
```
BOOL ScrollWindow(  
    int xAmount,
    int yAmount,
    LPCRECT lpRect = NULL,
    LPCRECT lpClipRect = NULL) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ScrollWindow](http://msdn.microsoft.com/library/windows/desktop/bb787591)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namescrollwindowexa--cwindowscrollwindowex"></a><a name="scrollwindowex"></a>CWindow::ScrollWindowEx  
 將額外的功能在指定的用戶端區域的捲動。  
  
```
int ScrollWindowEx(  
    int dx,
    int dy,
    LPCRECT lpRectScroll,
    LPCRECT lpRectClip,
    HRGN hRgnUpdate,
    LPRECT lpRectUpdate,
    UINT flags) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ScrollWindowEx](http://msdn.microsoft.com/library/windows/desktop/bb787593)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesenddlgitemmessagea--cwindowsenddlgitemmessage"></a><a name="senddlgitemmessage"></a>CWindow::SendDlgItemMessage  
 傳送訊息至控制項。  
  
```
LRESULT SendDlgItemMessage(  
    int nID,
    UINT message,
    WPARAM wParam = 0,
    LPARAM lParam = 0) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SendDlgItemMessage](http://msdn.microsoft.com/library/windows/desktop/ms645515)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesendmessagea--cwindowsendmessage"></a><a name="sendmessage"></a>CWindow::SendMessage  
 將訊息傳送至視窗，並不會傳回之前處理訊息的視窗程序之後。  
  
```
LRESULT SendMessage(  
    UINT message,
    WPARAM wParam = 0,
    LPARAM lParam = 0) throw();

static LRESULT SendMessage(  
    HWND hWnd,
    UINT message,
    WPARAM wParam,
    LPARAM lParam) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SendMessage](http://msdn.microsoft.com/library/windows/desktop/ms644950)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&29;](../../atl/codesnippet/cpp/cwindow-class_29.cpp)]  
  
##  <a name="a-namesendmessagetodescendantsa--cwindowsendmessagetodescendants"></a><a name="sendmessagetodescendants"></a>CWindow::SendMessageToDescendants  
 將指定的訊息傳送至所有直接子系`CWindow`物件。  
  
```
void SendMessageToDescendants(  
    UINT message,
    WPARAM wParam = 0,
    LPARAM lParam = 0,
    BOOL bDeep = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `message`  
 [in]要傳送的訊息。  
  
 `wParam`  
 [in]其他訊息特定資訊。  
  
 `lParam`  
 [in]其他訊息特定資訊。  
  
 `bDeep`  
 [in]如果**TRUE** （預設值），訊息會傳送至所有子系的視窗; 否則它將只能傳送到的立即子視窗。  
  
### <a name="remarks"></a>備註  
 如果`bDeep`是**TRUE**，此外將訊息傳送到其他子系的所有視窗。  
  
##  <a name="a-namesendnotifymessagea--cwindowsendnotifymessage"></a><a name="sendnotifymessage"></a>CWindow::SendNotifyMessage  
 傳送訊息至視窗。  
  
```
BOOL SendNotifyMessage(  
    UINT message,
    WPARAM wParam = 0,
    LPARAM lParam = 0) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SendNotifyMessage](http://msdn.microsoft.com/library/windows/desktop/ms644953)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果呼叫的執行緒，所建立視窗`SendNotifyMessage`等到處理訊息的視窗程序之後才會傳回。 否則，它會立即傳回。  
  
##  <a name="a-namesetactivewindowa--cwindowsetactivewindow"></a><a name="setactivewindow"></a>CWindow::SetActiveWindow  
 啟用視窗。  
  
```
HWND SetActiveWindow() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646311)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&30;](../../atl/codesnippet/cpp/cwindow-class_30.cpp)]  
  
##  <a name="a-namesetcapturea--cwindowsetcapture"></a><a name="setcapture"></a>CWindow::SetCapture  
 傳送至視窗的所有後續的滑鼠輸入。  
  
```
HWND SetCapture() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetCapture](http://msdn.microsoft.com/library/windows/desktop/ms646262)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetclipboardviewera--cwindowsetclipboardviewer"></a><a name="setclipboardviewer"></a>CWindow::SetClipboardViewer  
 將剪貼簿檢視器鏈結中的視窗。  
  
```
HWND SetClipboardViewer() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetClipboardViewer](http://msdn.microsoft.com/library/windows/desktop/ms649052)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetdlgctrlida--cwindowsetdlgctrlid"></a><a name="setdlgctrlid"></a>CWindow::SetDlgCtrlID  
 將視窗的識別項設定指定的值。  
  
```
int SetDlgCtrlID(int nID) throw();
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 [in]要設定視窗的識別項的新值。  
  
### <a name="return-value"></a>傳回值  
 如果成功，視窗中，前一個識別碼否則為 0。  
  
##  <a name="a-namesetdlgiteminta--cwindowsetdlgitemint"></a><a name="setdlgitemint"></a>CWindow::SetDlgItemInt  
 變更控制項的文字字串表示的整數值。  
  
```
BOOL SetDlgItemInt(  
    int nID,
    UINT nValue,
    BOOL bSigned = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetDlgItemInt](http://msdn.microsoft.com/library/windows/desktop/ms645518)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetdlgitemtexta--cwindowsetdlgitemtext"></a><a name="setdlgitemtext"></a>CWindow::SetDlgItemText  
 變更控制項的文字。  
  
```
BOOL SetDlgItemText(int nID, LPCTSTR lpszString) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetDlgItemText](http://msdn.microsoft.com/library/windows/desktop/ms645521)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetfocusa--cwindowsetfocus"></a><a name="setfocus"></a>CWindow::SetFocus  
 將輸入的焦點設定為視窗。  
  
```
HWND SetFocus() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&31;](../../atl/codesnippet/cpp/cwindow-class_31.cpp)]  
  
##  <a name="a-namesetfonta--cwindowsetfont"></a><a name="setfont"></a>CWindow::SetFont  
 藉由傳送變更視窗的目前字型[WM_SETFONT](http://msdn.microsoft.com/library/windows/desktop/ms632642)至視窗的訊息。  
  
```
void SetFont(HFONT hFont, BOOL bRedraw = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `hFont`  
 [in]新字型的控制代碼。  
  
 `bRedraw`  
 [in]如果**TRUE** （預設值），視窗會重新繪製。 否則，它不是。  
  
##  <a name="a-namesethotkeya--cwindowsethotkey"></a><a name="sethotkey"></a>CWindow::SetHotKey  
 將熱鍵與視窗相關聯傳送**WM_SETHOTKEY**訊息。  
  
```
int SetHotKey(WORD wVirtualKeyCode, WORD wModifiers) throw();
```  
  
### <a name="parameters"></a>參數  
 `wVirtualKeyCode`  
 [in]熱鍵虛擬按鍵碼。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.。  
  
 `wModifiers`  
 [in]熱鍵修飾詞。 如需可能的值，請參閱**WM_SETHOTKEY**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 可能的清單傳回值，請參閱[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameseticona--cwindowseticon"></a><a name="seticon"></a>CWindow::SetIcon  
 將視窗的大型或小型圖示所識別的圖示`hIcon`。  
  
```
HICON SetIcon(HICON hIcon, BOOL bBigIcon = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `hIcon`  
 [in]新圖示的控制代碼。  
  
 `bBigIcon`  
 [in]如果**TRUE** （預設值），這個方法會設定大型圖示。 否則，它會將小圖示。  
  
### <a name="return-value"></a>傳回值  
 上一個圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
 `SetIcon`傳送[WM_SETICON](http://msdn.microsoft.com/library/windows/desktop/ms632643)至視窗的訊息。  
  
##  <a name="a-namesetmenua--cwindowsetmenu"></a><a name="setmenu"></a>CWindow::SetMenu  
 變更目前的視窗的功能表。  
  
```
BOOL SetMenu(HMENU hMenu) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetMenu](http://msdn.microsoft.com/library/windows/desktop/ms647995)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetparenta--cwindowsetparent"></a><a name="setparent"></a>CWindow::SetParent  
 變更父視窗。  
  
```
HWND SetParent(HWND hWndNewParent) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetParent](http://msdn.microsoft.com/library/windows/desktop/ms633541)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&32;](../../atl/codesnippet/cpp/cwindow-class_32.cpp)]  
  
##  <a name="a-namesetredrawa--cwindowsetredraw"></a><a name="setredraw"></a>CWindow::SetRedraw  
 設定或清除所傳送的重繪旗標[WM_SETREDRAW](http://msdn.microsoft.com/library/windows/desktop/dd145219)至視窗的訊息。  
  
```
void SetRedraw(BOOL bRedraw = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRedraw`  
 [in]指定的重繪旗標的狀態。 如果**TRUE** （預設值），重繪旗標設定; 如果**FALSE**，會清除此旗標。  
  
### <a name="remarks"></a>備註  
 呼叫`SetRedraw`允許重新繪製，或防止重繪變更的變更。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&33;](../../atl/codesnippet/cpp/cwindow-class_33.cpp)]  
  
##  <a name="a-namesetscrollinfoa--cwindowsetscrollinfo"></a><a name="setscrollinfo"></a>CWindow::SetScrollInfo  
 設定捲軸上的參數。  
  
```
int SetScrollInfo(  
    int nBar,
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetScrollInfo](http://msdn.microsoft.com/library/windows/desktop/bb787595)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetscrollposa--cwindowsetscrollpos"></a><a name="setscrollpos"></a>CWindow::SetScrollPos  
 變更的捲動方塊的位置。  
  
```
int SetScrollPos(  
    int nBar,
    int nPos,
    BOOL bRedraw = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetscrollrangea--cwindowsetscrollrange"></a><a name="setscrollrange"></a>CWindow::SetScrollRange  
 變更捲軸列範圍。  
  
```
BOOL SetScrollRange(  
    int nBar,
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetScrollRange](http://msdn.microsoft.com/library/windows/desktop/bb787599)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesettimera--cwindowsettimer"></a><a name="settimer"></a>CWindow::SetTimer  
 建立計時器事件。  
  
```
UINT SetTimer(  
    UINT nIDEvent,
    UINT nElapse,
    void (CALLBACK* lpfnTimer)(HWND, UINT, UINT, DWORD) = NULL) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetTimer](http://msdn.microsoft.com/library/windows/desktop/ms644906)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetwindowcontexthelpida--cwindowsetwindowcontexthelpid"></a><a name="setwindowcontexthelpid"></a>CWindow::SetWindowContextHelpId  
 設定視窗的說明內容識別碼。  
  
```
BOOL SetWindowContextHelpId(DWORD dwContextHelpId) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowContextHelpId](http://msdn.microsoft.com/library/windows/desktop/bb762101)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetwindowlonga--cwindowsetwindowlong"></a><a name="setwindowlong"></a>CWindow::SetWindowLong  
 32 位元值的指定位移設定額外的視窗記憶體。  
  
```
LONG SetWindowLong(int nIndex, LONG dwNewLong) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  若要撰寫與 32 位元和 64 位元版本的 Windows 相容的程式碼，使用[CWindow::SetWindowLongPtr](#setwindowlongptr)。  
  
##  <a name="a-namesetwindowlongptra--cwindowsetwindowlongptr"></a><a name="setwindowlongptr"></a>CWindow::SetWindowLongPtr  
 指定的視窗中，屬性變更，也會將值設定額外的視窗記憶體中指定的位移。  
  
```
LONG_PTR SetWindowLongPtr(int nIndex, LONG_PTR dwNewLong) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowLongPtr](http://msdn.microsoft.com/library/windows/desktop/ms644898)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個函數會取代`CWindow::SetWindowLong`方法。 若要撰寫與 32 位元和 64 位元版本的 Windows 相容的程式碼，使用`CWindow::SetWindowLongPtr`。  
  
##  <a name="a-namesetwindowplacementa--cwindowsetwindowplacement"></a><a name="setwindowplacement"></a>CWindow::SetWindowPlacement  
 設定顯示狀態和位置。  
  
```
BOOL SetWindowPlacement(const WINDOWPLACEMENT FAR* lpwndpl);
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowPlacement](http://msdn.microsoft.com/library/windows/desktop/ms633544)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetwindowposa--cwindowsetwindowpos"></a><a name="setwindowpos"></a>CWindow::SetWindowPos  
 設定大小、 位置和 Z 順序。  
  
```
BOOL SetWindowPos(  
    HWND hWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags) throw();

BOOL SetWindowPos(  
    HWND hWndInsertAfter,
    LPCRECT lpRect,
    UINT nFlags) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這個方法的第二個版本會使用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構來設定視窗的新位置、 寬度和高度。  
  
##  <a name="a-namesetwindowrgna--cwindowsetwindowrgn"></a><a name="setwindowrgn"></a>CWindow::SetWindowRgn  
 設定視窗的視窗區域。  
  
```
int SetWindowRgn(HRGN hRgn, BOOL bRedraw = FALSE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowRgn](http://msdn.microsoft.com/library/windows/desktop/dd145102)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetwindowtexta--cwindowsetwindowtext"></a><a name="setwindowtext"></a>CWindow::SetWindowText  
 變更視窗的文字。  
  
```
BOOL SetWindowText(LPCTSTR lpszString) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowText](http://msdn.microsoft.com/library/windows/desktop/ms633546)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&34;](../../atl/codesnippet/cpp/cwindow-class_34.cpp)]  
  
##  <a name="a-namesetwindowworda--cwindowsetwindowword"></a><a name="setwindowword"></a>CWindow::SetWindowWord  
 設定中指定位移的 16 位元值到額外的視窗記憶體。  
  
```
WORD SetWindowWord(int nIndex, WORD wNewWord) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameshowcareta--cwindowshowcaret"></a><a name="showcaret"></a>CWindow::ShowCaret  
 顯示系統游標。  
  
```
BOOL ShowCaret() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ShowCaret](http://msdn.microsoft.com/library/windows/desktop/ms648406)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&35;](../../atl/codesnippet/cpp/cwindow-class_35.cpp)]  
  
##  <a name="a-nameshowownedpopupsa--cwindowshowownedpopups"></a><a name="showownedpopups"></a>CWindow::ShowOwnedPopups  
 顯示或隱藏視窗所擁有的快顯視窗。  
  
```
BOOL ShowOwnedPopups(BOOL bShow = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ShowOwnedPopups](http://msdn.microsoft.com/library/windows/desktop/ms633547)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameshowscrollbara--cwindowshowscrollbar"></a><a name="showscrollbar"></a>CWindow::ShowScrollBar  
 顯示或隱藏捲軸。  
  
```
BOOL ShowScrollBar(UINT nBar, BOOL bShow = TRUE) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ShowScrollBar](http://msdn.microsoft.com/library/windows/desktop/bb787601)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameshowwindowa--cwindowshowwindow"></a><a name="showwindow"></a>CWindow::ShowWindow  
 設定視窗的顯示狀態。  
  
```
BOOL ShowWindow(int nCmdShow) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms633548)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&36;](../../atl/codesnippet/cpp/cwindow-class_36.cpp)]  
  
##  <a name="a-nameshowwindowasynca--cwindowshowwindowasync"></a><a name="showwindowasync"></a>CWindow::ShowWindowAsync  
 設定不同的執行緒所建立之視窗的顯示狀態。  
  
```
BOOL ShowWindowAsync(int nCmdShow) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ShowWindowAsync](http://msdn.microsoft.com/library/windows/desktop/ms633549)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameupdatewindowa--cwindowupdatewindow"></a><a name="updatewindow"></a>CWindow::UpdateWindow  
 更新工作區。  
  
```
BOOL UpdateWindow() throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[UpdateWindow](http://msdn.microsoft.com/library/windows/desktop/dd145167)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&37;](../../atl/codesnippet/cpp/cwindow-class_37.cpp)]  
  
##  <a name="a-namevalidaterecta--cwindowvalidaterect"></a><a name="validaterect"></a>CWindow::ValidateRect  
 驗證指定的矩形內的用戶端區域。  
  
```
BOOL ValidateRect(LPCRECT lpRect) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ValidateRect](http://msdn.microsoft.com/library/windows/desktop/dd145194)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namevalidatergna--cwindowvalidatergn"></a><a name="validatergn"></a>CWindow::ValidateRgn  
 驗證指定的區域內的用戶端區域。  
  
```
BOOL ValidateRgn(HRGN hRgn) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[ValidateRgn](http://msdn.microsoft.com/library/windows/desktop/dd145195)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namewinhelpa--cwindowwinhelp"></a><a name="winhelp"></a>CWindow::WinHelp  
 啟動 Windows 說明。  
  
```
BOOL WinHelp(  
    LPCTSTR lpszHelp,
    UINT nCmd = HELP_CONTEXT,
    DWORD dwData = 0) throw();
```  
  
### <a name="remarks"></a>備註  
 請參閱[WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

