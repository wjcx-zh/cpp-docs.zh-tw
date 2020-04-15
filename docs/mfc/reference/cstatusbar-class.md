---
title: CStatusBar 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 0549ee10faa15b80b18a0bee2f115425002e1479
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376253"
---
# <a name="cstatusbar-class"></a>CStatusBar 類別

具有一列文字輸出窗格或「指示器」的控制列。

## <a name="syntax"></a>語法

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C狀態列:CStatusbar](#cstatusbar)|建構 `CStatusBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStatusbar::命令索引](#commandtoindex)|獲取給定指標 ID 的索引。|
|[C 狀態列:建立](#create)|創建狀態列,將其附加到物件,`CStatusBar`並設置初始字型和條形高度。|
|[C 狀態列::建立Ex](#createex)|為`CStatusBar`嵌`CStatusBarCtrl`入 物件創建具有其他樣式的物件。|
|[CStatusBar::D原始專案](#drawitem)|當所有者繪製狀態欄控件的可視方面發生更改時調用。|
|[CStatusBar:取得項目ID](#getitemid)|獲取給定索引的指標 ID。|
|[CStatusBar:取得項目已重新完成](#getitemrect)|獲取給定索引的顯示矩形。|
|[CStatusBar:抓取窗格資訊](#getpaneinfo)|獲取給定索引的指示器 ID、樣式和寬度。|
|[C狀態列::抓取表格樣式](#getpanestyle)|獲取給定索引的指示器樣式。|
|[C 狀態列::抓取窗格文字](#getpanetext)|獲取給定索引的指示器文本。|
|[CStatusBar:取得狀態列](#getstatusbarctrl)|允許直接訪問基礎公共控件。|
|[C 狀態列:設定指標](#setindicators)|設置指示器指示符。|
|[C狀態列::設定窗格資訊](#setpaneinfo)|設置給定索引的指示器 ID、樣式和寬度。|
|[C狀態列::設定窗格樣式](#setpanestyle)|設置給定索引的指示器樣式。|
|[C 狀態列::設定窗格文字](#setpanetext)|設置給定索引的指示器文本。|

## <a name="remarks"></a>備註

輸出窗格通常用作消息行和狀態指示器。 示例包括簡要解釋所選選單命令的功能表説明消息列以及顯示 SCROLL LOCK、NUM LOCK 和其他鍵狀態的指示器。

[CStatusBar:GetStatusBarCtrl](#getstatusbarctrl)是 MFC 4.0 中新成員函數,允許您利用 Windows 通用控件對狀態列自定義和其他功能的支援。 `CStatusBar`成員函數為您提供 Windows 公共控件的大部分功能;但是,當您調用`GetStatusBarCtrl`時,您可以為狀態列提供更多 Windows 95/98 狀態列的特徵。 調用`GetStatusBarCtrl`時,它將返回`CStatusBarCtrl`對 物件的引用。 有關使用 Windows 常見控制程式設計工具列的詳細資訊,請參閱[CStatusBarCtrl。](../../mfc/reference/cstatusbarctrl-class.md) 有關常見控制項的更多一般資訊,請參閱 Windows SDK[中的常見控制項](/windows/win32/Controls/common-controls-intro)。

框架將指標資訊存儲在陣列中,其中最左側的指示器位於位置 0。 創建狀態列時,將使用框架與相應指標關聯字串指示陣列。 然後,可以使用字串 ID 或索引訪問指標。

默認情況下,第一個指標是"彈性的":它佔用其他指標窗格不使用的狀態欄長度,以便其他窗格右對齊。

要建立狀態列,請按照以下步驟操作:

1. 建構 `CStatusBar` 物件。

1. 呼叫["建立](#create)"(或[CreateEx](#createex)) 函數以建立狀態列`CStatusBar`視窗並將其附加到 物件。

1. 呼叫[SetIndicators](#setindicators)將字串 ID 與每個指標相關聯。

有三種方法可以更新狀態列窗格中的文字:

1. 呼叫[CWnd::設定視窗文字](../../mfc/reference/cwnd-class.md#setwindowtext)以僅更新窗格 0 中的文本。

1. 呼叫[CCmdUI:在](../../mfc/reference/ccmdui-class.md#settext)狀態列的ON_UPDATE_COMMAND_UI處理程式中設定文本。

1. 呼叫[SetPaneText](#setpanetext)更新任何窗格的文字。

調用[SetPaneStyle](#setpanestyle)以更新狀態列窗格的樣式。

有關使用`CStatusBar`的詳細資訊,請參閱 MFC[和技術說明 31 中的](../../mfc/tn031-control-bars.md)[狀態列實現](../../mfc/status-bar-implementation-in-mfc.md)文章:控制列 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制列](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusbar::命令索引

獲取給定ID的指標索引。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
要檢索其索引的指標的字串 ID。

### <a name="return-value"></a>傳回值

指標的指數(如果成功);-1 如果不成功。

### <a name="remarks"></a>備註

第一個指標的索引為 0。

## <a name="cstatusbarcreate"></a><a name="create"></a>C 狀態列:建立

創建狀態列(子視窗),並將其與`CStatusBar`物件關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向其 Windows 視窗是狀態列的父級的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

*dwStyle*<br/>
狀態欄樣式。 除了標準 Windows[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)之外,還支援這些樣式。

- CBRS_TOP控制欄位於框架視窗的頂部。

- CBRS_BOTTOM控制欄位於框架視窗的底部。

- CBRS_NOALIGN調整父控件欄的大小時,不會重新置放。

*nID*<br/>
工具列的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此外,還可以設置初始字體並將狀態列的高度設置為預設值。

## <a name="cstatusbarcreateex"></a><a name="createex"></a>C 狀態列::建立Ex

呼叫此函數以創建狀態列(子視窗),並將其與`CStatusBar`物件關聯。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向其 Windows 視窗是狀態列的父級的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

*dwCtrl風格*<br/>
用於創建嵌入式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件的其他樣式。 預設值指定沒有大小調整手柄或工具提示支援的狀態列。 支援的狀態列樣式包括:

- SBARS_SIZEGRIP 狀態列控件包括狀態欄右側的尺寸調整夾。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

- SBT_TOOLTIPS 狀態列支援工具提示。

有關這些樣式的詳細資訊,請參閱[CStatusBarCtrl 的設定](../../mfc/settings-for-the-cstatusbarctrl.md)。

*dwStyle*<br/>
狀態欄樣式。 預設值指定在框架視窗底部創建可見狀態列。 應用[「視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)」和[「CDialog 列」「創建](../../mfc/reference/cdialogbar-class.md#create)」中列出的狀態列控制樣式的任意組合。 但是,此參數應始終包括WS_CHILD和WS_VISIBLE樣式。

*nID*<br/>
狀態列的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此功能還設置初始字體,並將狀態列的高度設置為預設值。

在`CreateEx`創建嵌入狀態列控制項期間需要存在某些樣式時,請使用而不是[Create。](#create) 例如,將*dwCtrlStyle*設置為SBT_TOOLTIPS以在狀態列對象中顯示工具提示。

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>C狀態列:CStatusbar

建構`CStatusBar`物件,如有必要創建預設狀態列字體,並將字體特徵設置為預設值。

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::D原始專案

當擁有者繪製的狀態欄的可視方面發生更改時,框架將調用此成員函數。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CStatusBar`。 應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar:取得項目ID

傳*回 nIndex*指定的指標的識別碼。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其ID的指標的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的指標的 ID。

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar:取得項目已重新完成

將*nIndex*指定的指標的座標複製到*lpRect*指向的結構中。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其矩形座標的指標的索引。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件,該物件將接收*nIndex*指定的指標的座標。

### <a name="remarks"></a>備註

座標相對於狀態列的左上角以像素為單位。

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar:抓取窗格資訊

將*nID* *、nStyle*和*cxWidth*設置到*nIndex*指定位置的指示器窗格的 ID、樣式和寬度。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其資訊的窗格的索引。

*nID*<br/>
對設定為窗格 ID 的 UINT 的引用。

*nStyle*<br/>
對設定為窗格樣式的 UINT 的引用。

*cxWidth*<br/>
引用設置為窗格寬度的整數。

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>C狀態列::抓取表格樣式

調用此成員函數以檢索狀態欄窗格的樣式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其樣式的窗格的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的狀態列窗格的樣式。

### <a name="remarks"></a>備註

窗格的樣式確定窗格的顯示方式。

有關可用於狀態列的樣式清單,請參閱[建立](#create)。

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>C 狀態列::抓取窗格文字

呼叫此成員函數以檢索顯示在狀態列窗格中的文本。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其文本的窗格的索引。

*rString*<br/>
對包含要檢索的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用。

### <a name="return-value"></a>傳回值

包含`CString`窗格文字的物件。

### <a name="remarks"></a>備註

此成員函數的第二種形式使用字串文本填充`CString`物件。

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar:取得狀態列

此成員函數允許直接訪問基礎公共控件。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>傳回值

包含對[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件的引用。

### <a name="remarks"></a>備註

用於`GetStatusBarCtrl`利用 Windows 狀態列通用控制件的功能,並利用[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供的狀態列自定義的支援。 例如,通過使用公共控制項,可以指定包含狀態列上大小調整的夾點的樣式,也可以指定樣式,使狀態列顯示在父視窗工作區的頂部。

有關常見控制項的更多一般資訊,請參閱 Windows SDK 中的[常用控制項](/windows/win32/Controls/common-controls-intro)。

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>C 狀態列:設定指標

將每個指標的 ID 設定到陣列*lpIDArray*的相應元素指定的值,載入每個 ID 指定的字串資源,並將指標的文本設置到字串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
指向指示的I陣列。

*nID( N) Count*<br/>
*lpIDArray*指向的陣列中的元素數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>C狀態列::設定窗格資訊

將指定的指示器窗格設置為新 ID、樣式和寬度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設置其樣式的指標窗格的索引。

*nID*<br/>
指示器窗格的新 ID。

*nStyle*<br/>
指示器窗格的新樣式。

*cxWidth*<br/>
指示器窗格的新寬度。

### <a name="remarks"></a>備註

支援以下指標樣式:

- SBPS_NOBORDERS窗格周圍沒有三維邊框。

- SBPS_POPOUT反向邊框,以便文本"彈出"。

- SBPS_DISABLED不要畫文本。

- SBPS_STRETCH拉伸窗格以填充未使用的空間。 每個狀態列只能有一個窗格具有此樣式。

- SBPS_NORMAL 無拉伸、邊框或彈出。

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>C狀態列::設定窗格樣式

調用此成員函數以設置狀態列窗格的樣式。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設置其樣式的窗格的索引。

*nStyle*<br/>
要設置其樣式的窗格的樣式。

### <a name="remarks"></a>備註

窗格的樣式確定窗格的顯示方式。

有關狀態列可用的樣式清單,請參閱[SetPaneInfo](#setpaneinfo)。

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>C 狀態列::設定窗格文字

呼叫此成員函數將窗格文字設定為*lpszNewText*指向的字串。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設置其文本的窗格的索引。

*lpsz 新文字*<br/>
指向新窗格文本的指標。

*b更新*<br/>
如果為 TRUE,則設置文本後窗格將失效。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

呼叫`SetPaneText`後,必須添加 UI 更新處理程式才能在狀態列中顯示新文本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 類別](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
