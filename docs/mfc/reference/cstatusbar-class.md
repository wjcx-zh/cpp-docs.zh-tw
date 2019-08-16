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
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502341"
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
|[CStatusBar::CStatusBar](#cstatusbar)|建構 `CStatusBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|取得給定指標識別碼的索引。|
|[CStatusBar::Create](#create)|建立狀態列, 將其附加至`CStatusBar`物件, 並設定初始字型和橫條高度。|
|[CStatusBar::CreateEx](#createex)|使用內嵌`CStatusBarCtrl`物件的其他樣式建立物件。`CStatusBar`|
|[CStatusBar::DrawItem](#drawitem)|當主控描繪狀態列控制項的視覺外觀變更時呼叫。|
|[CStatusBar::GetItemID](#getitemid)|取得指定索引的指標識別碼。|
|[CStatusBar::GetItemRect](#getitemrect)|取得指定索引的顯示矩形。|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|取得指定索引的指標識別碼、樣式和寬度。|
|[CStatusBar::GetPaneStyle](#getpanestyle)|取得指定索引的指標樣式。|
|[CStatusBar::GetPaneText](#getpanetext)|取得指定索引的指標文字。|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允許直接存取基礎通用控制項。|
|[CStatusBar::SetIndicators](#setindicators)|設定指標識別碼。|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|設定指定索引的指標識別碼、樣式和寬度。|
|[CStatusBar::SetPaneStyle](#setpanestyle)|設定指定索引的指標樣式。|
|[CStatusBar::SetPaneText](#setpanetext)|設定指定索引的指標文字。|

## <a name="remarks"></a>備註

輸出窗格通常用來做為訊息行和狀態指示器。 範例包括 [功能表] [說明]-[訊息行], 可簡短解說選取的功能表命令, 以及顯示滾動鎖狀態、NUM LOCK 和其他索引鍵的指標。

[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)是 MFC 4.0 的新成員函式, 可讓您利用 Windows 通用控制項的狀態列自訂支援和其他功能。 `CStatusBar`成員函式提供您大部分的 Windows 通用控制項功能;不過, 當您呼叫`GetStatusBarCtrl`時, 可以提供您的狀態列更多 Windows 95/98 狀態列的特性。 當您呼叫`GetStatusBarCtrl`時, 它會傳回`CStatusBarCtrl`物件的參考。 如需使用 Windows 通用控制項來設計工具列的詳細資訊, 請參閱[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 。 如需有關通用控制項的一般資訊, 請參閱 Windows SDK 中的[通用控制項](/windows/win32/Controls/common-controls-intro)。

架構會將指標資訊儲存在陣列中, 最左邊的指標位於位置0。 當您建立狀態列時, 會使用架構與對應指標相關聯的字串識別碼陣列。 接著, 您可以使用字串識別碼或索引來存取指標。

根據預設, 第一個指標是「彈性」: 它會佔用其他指標窗格未使用的狀態列長度, 因此其他窗格會靠右對齊。

若要建立狀態列, 請遵循下列步驟:

1. 建構 `CStatusBar` 物件。

1. 呼叫[create](#create) (或[CreateEx](#createex)) 函式來建立狀態列視窗, 並將`CStatusBar`它附加至物件。

1. 呼叫[SetIndicators](#setindicators) , 將字串識別碼與每個指標產生關聯。

有三種方式可以更新狀態列窗格中的文字:

1. 呼叫[CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)以僅更新窗格0中的文字。

1. 在狀態列的 ON_UPDATE_COMMAND_UI 處理常式中呼叫[CCmdUI:: SetText](../../mfc/reference/ccmdui-class.md#settext) 。

1. 呼叫[SetPaneText](#setpanetext)以更新任何窗格的文字。

呼叫[SetPaneStyle](#setpanestyle)以更新狀態列窗格的樣式。

如需使用`CStatusBar`的詳細資訊, 請參閱[MFC](../../mfc/status-bar-implementation-in-mfc.md)和[技術提示31中的狀態列的執行方式:控制列](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>需求

**標頭:** afxext.h。h

##  <a name="commandtoindex"></a>CStatusBar:: CommandToIndex

取得指定識別碼的指標索引。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
要抓取其索引之指標的字串識別碼。

### <a name="return-value"></a>傳回值

如果成功, 則為指標的索引;-1 (如果不成功)。

### <a name="remarks"></a>備註

第一個指標的索引為0。

##  <a name="create"></a>CStatusBar:: Create

建立狀態列 (子視窗), 並將它與`CStatusBar`物件產生關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 其 Windows 視窗為狀態列的父系。

*dwStyle*<br/>
狀態列樣式。 除了標準的 Windows[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)之外, 也支援這些樣式。

- CBRS_TOP 控制列位於框架視窗的頂端。

- CBRS_BOTTOM 控制列位於框架視窗的底部。

- 當父代調整大小時, CBRS_NOALIGN 控制列不會重新置放。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

也會設定初始字型, 並將狀態列的高度設定為預設值。

##  <a name="createex"></a>CStatusBar:: CreateEx

呼叫此函式以建立狀態列 (子視窗), 並將它與`CStatusBar`物件產生關聯。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 其 Windows 視窗為狀態列的父系。

*dwCtrlStyle*<br/>
建立內嵌[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件的其他樣式。 預設會指定沒有調整大小的底框或工具提示支援的狀態列。 支援的狀態列樣式包括:

- SBARS_SIZEGRIP 狀態列控制項在狀態列的右端包含調整大小的底框。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

- SBT_TOOLTIPS 狀態列支援工具提示。

如需這些樣式的詳細資訊, 請參閱[CStatusBarCtrl 的設定](../../mfc/settings-for-the-cstatusbarctrl.md)。

*dwStyle*<br/>
狀態列樣式。 預設值指定在框架視窗底部建立可見的狀態列。 套用[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create)中列出之狀態列控制項樣式的任何組合。 不過, 這個參數應該一律包含 WS_CHILD 和 WS_VISIBLE 樣式。

*nID*<br/>
狀態列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式也會設定初始字型, 並將狀態列的高度設定為預設值。

使用`CreateEx`, 而不是[建立](#create), 在建立內嵌狀態列控制項期間需要有特定樣式時。 例如, 將*dwCtrlStyle*設定為 SBT_TOOLTIPS, 以在狀態列物件中顯示工具提示。

##  <a name="cstatusbar"></a>CStatusBar:: CStatusBar

會建立`CStatusBar`物件, 並視需要建立預設的狀態列字型, 並將字型特性設定為預設值。

```
CStatusBar();
```

##  <a name="drawitem"></a>CStatusBar::D rawItem

當主控描繪狀態列的視覺外觀變更時, 架構會呼叫這個成員函式。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標, 其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構的成員會定義要執行的繪圖動作。 `itemAction` 覆寫這個成員函式, 以執行主控描繪`CStatusBar`物件的繪圖。 在此成員函式終止之前, 應用程式應該還原針對*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面 (GDI) 物件。

##  <a name="getitemid"></a>CStatusBar:: GetItemID

傳回*nIndex*指定之指標的識別碼。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其識別碼的指標索引。

### <a name="return-value"></a>傳回值

*NIndex*指定之指標的識別碼。

##  <a name="getitemrect"></a>CStatusBar:: GetItemRect

將*nIndex*指定之指標的座標複製到*lpRect*所指向的結構中。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其矩形座標的指標索引。

*lpRect*<br/>
指向[矩形](/previous-versions/dd162897\(v=vs.85\))結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件, 其會接收*nIndex*所指定之指標的座標。

### <a name="remarks"></a>備註

座標是以圖元為單位, 相對於狀態列的左上角。

##  <a name="getpaneinfo"></a>CStatusBar:: GetPaneInfo

將*nID*、 *nStyle*和*cxWidth*設定為*nIndex*所指定位置上指標窗格的識別碼、樣式和寬度。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其資訊之窗格的索引。

*nID*<br/>
參考設定為窗格識別碼的 UINT。

*nStyle*<br/>
參考設定為窗格樣式的 UINT。

*cxWidth*<br/>
參考設定為窗格寬度的整數。

##  <a name="getpanestyle"></a>CStatusBar:: GetPaneStyle

呼叫這個成員函式, 以取得狀態列窗格的樣式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其樣式之窗格的索引。

### <a name="return-value"></a>傳回值

*NIndex*所指定之狀態列窗格的樣式。

### <a name="remarks"></a>備註

窗格的樣式會決定窗格的顯示方式。

如需狀態列可用的樣式清單, 請參閱[Create](#create)。

##  <a name="getpanetext"></a>CStatusBar:: GetPaneText

呼叫這個成員函式, 以抓取狀態列窗格中顯示的文字。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要抓取其文字之窗格的索引。

*rString*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考, 其中包含要抓取的文字。

### <a name="return-value"></a>傳回值

包含窗格文字的物件。`CString`

### <a name="remarks"></a>備註

此成員函式的第二種形式`CString`會以字串文字填入物件。

##  <a name="getstatusbarctrl"></a>CStatusBar:: GetStatusBarCtrl

這個成員函式可讓您直接存取基礎通用控制項。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>傳回值

包含[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件的參考。

### <a name="remarks"></a>備註

使用`GetStatusBarCtrl`來利用 Windows 狀態列通用控制項的功能, 並利用支援[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供的狀態列自訂。 例如, 藉由使用通用控制項, 您可以指定在狀態列上包含調整大小底框的樣式, 或者可以指定樣式, 讓狀態列出現在父視窗工作區的頂端。

如需有關通用控制項的一般資訊, 請參閱 Windows SDK 中的[通用控制項](/windows/win32/Controls/common-controls-intro)。

##  <a name="setindicators"></a>CStatusBar:: SetIndicators

將每個指標的識別碼設定為數組*lpIDArray*之對應元素所指定的值、載入每個識別碼所指定的字串資源, 並將指標的文字設定為字串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
識別碼陣列的指標。

*nIDCount*<br/>
*LpIDArray*中所指向之陣列中的元素數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="setpaneinfo"></a>CStatusBar:: SetPaneInfo

將指定的指標窗格設定為新的識別碼、樣式和寬度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其樣式的指標窗格索引。

*nID*<br/>
指標窗格的新識別碼。

*nStyle*<br/>
指標窗格的新樣式。

*cxWidth*<br/>
指標窗格的新寬度。

### <a name="remarks"></a>備註

支援下列指標樣式:

- SBPS_NOBORDERS 窗格周圍沒有3D 框線。

- SBPS_POPOUT 反轉框線, 讓文字「彈出」。

- SBPS_DISABLED 不繪製文字。

- SBPS_STRETCH Stretch 窗格 以填滿未使用的空間。 每個狀態列只有一個窗格可以有此樣式。

- 不 SBPS_NORMAL 延展、框線或快顯。

##  <a name="setpanestyle"></a>CStatusBar:: SetPaneStyle

呼叫這個成員函式可設定狀態列窗格的樣式。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其樣式的窗格索引。

*nStyle*<br/>
要設定其樣式的窗格樣式。

### <a name="remarks"></a>備註

窗格的樣式會決定窗格的顯示方式。

如需狀態列可用的樣式清單, 請參閱[SetPaneInfo](#setpaneinfo)。

##  <a name="setpanetext"></a>CStatusBar:: SetPaneText

呼叫這個成員函式, 將窗格文字設定為*lpszNewText*所指向的字串。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設定其文字之窗格的索引。

*lpszNewText*<br/>
新窗格文字的指標。

*bUpdate*<br/>
若為 TRUE, 則在設定文字之後, 窗格就會失效。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

呼叫`SetPaneText`之後, 您必須加入 UI 更新處理常式, 以在狀態列中顯示新的文字。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 類別](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
