---
title: "CStatusBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- indicators, status bar
- CStatusBar class
- status bars
- indicators
- status indicators
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
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
ms.openlocfilehash: e96070041ef5bcee0865991a14b6484082d8fc91
ms.lasthandoff: 02/24/2017

---
# <a name="cstatusbar-class"></a>CStatusBar 類別
具有一列文字輸出窗格或「指示器」的控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|建構 `CStatusBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|取得索引的指定的指標識別碼。|  
|[CStatusBar::Create](#create)|建立狀態列，附加至該`CStatusBar`物件，並設定初始字型和列的高度。|  
|[CStatusBar::CreateEx](#createex)|建立`CStatusBar`具有其他樣式的內嵌物件`CStatusBarCtrl`物件。|  
|[CStatusBar::DrawItem](#drawitem)|主控描繪狀態列控制項會變更的視覺外觀時呼叫。|  
|[CStatusBar::GetItemID](#getitemid)|取得指定索引的指標識別碼。|  
|[CStatusBar::GetItemRect](#getitemrect)|取得顯示給定索引的矩形。|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|取得指定索引的指標識別碼、 樣式和寬度。|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|取得指定索引的指標樣式。|  
|[CStatusBar::GetPaneText](#getpanetext)|取得指定索引的指標文字。|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允許直接存取基礎的通用控制項。|  
|[CStatusBar::SetIndicators](#setindicators)|設定指標識別碼。|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|設定指標 ID、 樣式和特定索引的寬度。|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|設定給定索引的指標樣式。|  
|[CStatusBar::SetPaneText](#setpanetext)|設定給定索引的標記文字。|  
  
## <a name="remarks"></a>備註  
 輸出窗格通常用來做為訊息列和狀態指示器。 範例包括簡要說明所選取的功能表命令的功能表說明訊息行，以及顯示 SCROLL LOCK、 NUM LOCK 和其他按鍵的狀態指標。  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成員函式新增到 MFC 4.0 可讓您利用狀態列上的自訂及其他功能的 Windows 通用控制項的支援。 `CStatusBar`成員函式可讓您大部分的 Windows 通用控制項; 的功能但是，當您呼叫`GetStatusBarCtrl`，您可以授與您狀態列甚至多個 Windows 95/98 狀態列的特性。 當您呼叫`GetStatusBarCtrl`，它會傳回參考`CStatusBarCtrl`物件。 請參閱[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)如需有關設計 Windows 通用控制項的工具列。 關於通用控制項的一般資訊，請參閱[通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 架構會標記資訊儲存至位置 0 的最左邊指標的陣列。 當您建立狀態列時，您會使用字串 Id，架構會將具有對應的指標的陣列。 您接著可以使用字串識別碼或索引來存取指標。  
  
 根據預設，第一個指標是 「 彈性 」: 它會佔用狀態列長度不供其他指標窗格，使其他窗格靠右對齊。  
  
 若要建立狀態列，請依照下列步驟執行︰  
  
1.  建構 `CStatusBar` 物件。  
  
2.  呼叫[建立](#create)(或[CreateEx](#createex)) 函式來建立 [狀態列] 視窗，並將其附加至`CStatusBar`物件。  
  
3.  呼叫[SetIndicators](#setindicators)與每一個指標相關聯的字串識別碼。  
  
 有三種方式來更新狀態列窗格中的文字︰  
  
1.  呼叫[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新窗格僅 0 中的文字。  
  
2.  呼叫[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext)在狀態列上`ON_UPDATE_COMMAND_UI`處理常式。  
  
3.  呼叫[SetPaneText](#setpanetext)更新任何窗格的文字。  
  
 呼叫[SetPaneStyle](#setpanestyle)更新狀態列窗格的樣式。  
  
 如需有關使用`CStatusBar`，請參閱文章[MFC 中的狀態列實作](../../mfc/status-bar-implementation-in-mfc.md)和[技術提示 31︰ 控制列](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 指標的索引取得指定的識別碼。  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIDFind`  
 指標的索引是要擷取的字串識別碼。  
  
### <a name="return-value"></a>傳回值  
 指標成功; 如果索引如果不成功，傳回 –&1;。  
  
### <a name="remarks"></a>備註  
 第一個指標的索引為 0。  
  
##  <a name="create"></a>CStatusBar::Create  
 建立狀態列 （子視窗），並將它與相關聯`CStatusBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)物件 Windows 視窗狀態列的父系。  
  
 `dwStyle`  
 狀態列樣式。 除了標準的 Windows[樣式](../../mfc/reference/window-styles.md)，支援這些樣式。  
  
- `CBRS_TOP`控制列是在框架視窗的頂端。  
  
- `CBRS_BOTTOM`控制列是在框架視窗的底部。  
  
- `CBRS_NOALIGN`父代重新調整大小時，控制列是不會重新調整位置。  
  
 `nID`  
 工具列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 也會將初始字型並將狀態設為預設值的長條的高度。  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 呼叫此函式可建立狀態列 （子視窗），並將它與關聯`CStatusBar`物件。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)物件 Windows 視窗狀態列的父系。  
  
 `dwCtrlStyle`  
 建立內嵌的其他樣式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件。 預設值會指定狀態列，而不需要調整大小底框或工具提示支援。 支援的狀態 列樣式為︰  
  
- **SBARS_SIZEGRIP**狀態列控制項包含可調整大小的底框右邊的 [狀態] 列。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。  
  
- **SBT_TOOLTIPS**狀態列支援工具提示。  
  
 如需有關這些樣式的詳細資訊，請參閱[CStatusBarCtrl 的設定](../../mfc/settings-for-the-cstatusbarctrl.md)。  
  
 `dwStyle`  
 狀態的列樣式。 預設值會指定要建立框架視窗底部的顯示狀態列。 套用狀態列控制項樣式中列出的任何結合[視窗樣式](../../mfc/reference/window-styles.md)和[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 不過，此參數應該一律包含 WS_CHILD 和 WS_VISIBLE 樣式。  
  
 `nID`  
 [狀態] 列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式也會設定初始的字型，並將狀態設定為預設值的長條的高度。  
  
 使用`CreateEx`，而不是[建立](#create)，當特定樣式必須要有內嵌的狀態列控制項的建立期間。 例如，設定`dwCtrlStyle`至**SBT_TOOLTIPS**狀態列物件中顯示工具提示。  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 建構`CStatusBar`物件，會建立預設狀態列字型有必要，並設定成預設值的字型特性。  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 此成員函式會呼叫架構中，當主控描繪狀態列會變更的視覺外觀。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 覆寫此成員函式實作繪圖的主控描繪`CStatusBar`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前終止此成員函式。  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 傳回所指定的標記識別碼`nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指標的 ID 是要擷取的索引。  
  
### <a name="return-value"></a>傳回值  
 指標所指定的識別碼`nIndex`。  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 複製所指定指標的座標`nIndex`成指向結構`lpRect`。  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其矩形座標的指標的索引。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，將會收到指定指標的座標`nIndex`。  
  
### <a name="remarks"></a>備註  
 座標是相對於左上角的 [狀態] 列的像素為單位。  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 設定`nID`， `nStyle`，和`cxWidth`以 ID、 樣式和寬度所指定的位置 [指標] 窗格的`nIndex`。  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其資訊 窗格的索引。  
  
 `nID`  
 若要參考**UINT**設窗格的識別碼。  
  
 `nStyle`  
 若要參考**UINT**設窗格的樣式。  
  
 `cxWidth`  
 窗格的寬度設為整數的參考。  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 呼叫此成員函式擷取狀態列窗格的樣式。  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其樣式 窗格的索引。  
  
### <a name="return-value"></a>傳回值  
 [狀態列] 窗格中所指定的樣式`nIndex`。  
  
### <a name="remarks"></a>備註  
 窗格的樣式會決定如何顯示 窗格。  
  
 狀態列的可用樣式清單，請參閱[建立](#create)。  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 呼叫此成員函式，以擷取出現在狀態列上窗格中的文字。  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  ```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be retrieved.  
  
 `rString`  
 A reference to a [CString](../../atl-mfc-shared/reference/cstringt-class.md) object that contains the text to be retrieved.  
  
### Return Value  
 A `CString` object containing the pane's text.  
  
### Remarks  
 The second form of this member function fills a `CString` object with the string text.  
  
##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl  
 This member function allows direct access to the underlying common control.  
  
```  
CStatusBarCtrl i GetStatusBarCtrl() const;  
```  
  
### Return Value  
 Contains a reference to a [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) object.  
  
### Remarks  
 Use `GetStatusBarCtrl` to take advantage of the functionality of the Windows status-bar common control, and to take advantage of the support [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) provides for status-bar customization. For example, by using the common control, you can specify a style that includes a sizing grip on the status bar, or you can specify a style to have the status bar appear at the top of the parent window's client area.  
  
 For more general information about common controls, See [Common Controls](http://msdn.microsoft.com/library/windows/desktop/bb775493) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setindicators"></a>  CStatusBar::SetIndicators  
 Sets each indicator's ID to the value specified by the corresponding element of the array `lpIDArray`, loads the string resource specified by each ID, and sets the indicator's text to the string.  
  
```  
BOOL SetIndicators (lpIDArray const UINT *，  
    int nIDCount);
```  
  
### Parameters  
 `lpIDArray`  
 Pointer to an array of IDs.  
  
 `nIDCount`  
 Number of elements in the array pointed to by `lpIDArray`.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo  
 Sets the specified indicator pane to a new ID, style, and width.  
  
```  
void SetPaneInfo (int nIndex，  
    UINT nID  
    UINT nStyle  
    int cxWidth);
```  
  
### Parameters  
 `nIndex`  
 Index of the indicator pane whose style is to be set.  
  
 `nID`  
 New ID for the indicator pane.  
  
 `nStyle`  
 New style for the indicator pane.  
  
 `cxWidth`  
 New width for the indicator pane.  
  
### Remarks  
 The following indicator styles are supported:  
  
- **SBPS_NOBORDERS** No 3-D border around the pane.  
  
- **SBPS_POPOUT** Reverse border so that text "pops out."  
  
- **SBPS_DISABLED** Do not draw text.  
  
- **SBPS_STRETCH** Stretch pane to fill unused space. Only one pane per status bar can have this style.  
  
- **SBPS_NORMAL** No stretch, borders, or pop-out.  
  
##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle  
 Call this member function to set the style of a status bar's pane.  
  
```  
void SetPaneStyle (int nIndex，  
    UINT nStyle);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose style is to be set.  
  
 `nStyle`  
 Style of the pane whose style is to be set.  
  
### Remarks  
 A pane's style determines how the pane appears.  
  
 For a list of styles available for status bars, see [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>  CStatusBar::SetPaneText  
 Call this member function to set the pane text to the string pointed to by `lpszNewText`.  
  
```  
BOOL SetPaneText (int nIndex，  
    LPCTSTR lpszNewText  
    BOOL bUpdate = TRUE);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be set.  
  
 `lpszNewText`  
 Pointer to the new pane text.  
  
 *bUpdate*  
 If **TRUE**, the pane is invalidated after the text is set.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
### Remarks  
 After you call `SetPaneText`, you must add a UI update handler to display the new text in the status bar.  
  
### Example  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## See Also  
 [MFC Sample CTRLBARS](../../visual-cpp-samples.md)   
 [MFC Sample DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)

