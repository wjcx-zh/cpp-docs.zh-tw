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
ms.openlocfilehash: 70d700197e3d249812e8b09a2cba744a0fbc9803
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649276"
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

|名稱|描述|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|取得索引的指定的指標的識別碼。|
|[CStatusBar::Create](#create)|建立狀態列，將它附加至`CStatusBar`物件，並設定初始的字型和列高度。|
|[CStatusBar::CreateEx](#createex)|會建立`CStatusBar`物件具有其他樣式的內嵌`CStatusBarCtrl`物件。|
|[CStatusBar::DrawItem](#drawitem)|當主控描繪狀態列控制項會變更的視覺外觀時呼叫。|
|[CStatusBar::GetItemID](#getitemid)|取得指定的索引指標識別碼。|
|[CStatusBar::GetItemRect](#getitemrect)|取得顯示給定索引的矩形。|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|取得指定的索引指標 ID、 樣式和寬度。|
|[CStatusBar::GetPaneStyle](#getpanestyle)|取得指定的索引指標樣式。|
|[CStatusBar::GetPaneText](#getpanetext)|取得指定的索引指標文字。|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允許直接存取基礎的通用控制項。|
|[CStatusBar::SetIndicators](#setindicators)|設定指標識別碼。|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|設定指標 ID、 樣式和寬度指定的索引。|
|[CStatusBar::SetPaneStyle](#setpanestyle)|設定給定索引的指標樣式。|
|[CStatusBar::SetPaneText](#setpanetext)|設定給定索引的標記文字。|

## <a name="remarks"></a>備註

輸出窗格通常會用做為訊息列和狀態指示器。 範例包括簡要說明所選取的功能表命令的功能表說明訊息行和顯示狀態的 SCROLL LOCK、 NUM LOCK 和其他索引鍵的指標。

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成員函式新增到 MFC 4.0 可讓您善加利用狀態列自訂和其他功能的 Windows 通用控制項的支援。 `CStatusBar` 成員函式可讓您大部分的 Windows 通用控制項; 的功能不過，當您呼叫`GetStatusBarCtrl`，您可以提供給您的狀態列更多 Windows 95/98 狀態列的特性。 當您呼叫`GetStatusBarCtrl`，它會傳回參考`CStatusBarCtrl`物件。 請參閱[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)如需有關設計使用 Windows 通用控制項的工具列。 更多一般通用控制項的詳細資訊，請參閱[通用控制項](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

架構會將標記資訊儲存在具有在位置 0 的最左邊指標的陣列。 當您建立狀態列時，您會使用字串陣列，架構會將對應的指標的識別碼。 您接著可以使用字串識別碼或索引來存取指標。

根據預設，第一個指標是 「 彈性 」: 它會佔用狀態列長度不是由其他指標窗格，以便將其他窗格會靠右對齊。

若要建立狀態 列，請遵循下列步驟：

1. 建構 `CStatusBar` 物件。

1. 呼叫[Create](#create) (或[CreateEx](#createex)) 函式來建立 [狀態列] 視窗，並將其附加至`CStatusBar`物件。

1. 呼叫[SetIndicators](#setindicators)每一個指標相關聯的字串識別碼。

有三種方式可以更新狀態列窗格中的文字：

1. 呼叫[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新窗格只有 0 中的文字。

1. 呼叫[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) [狀態] 列 ON_UPDATE_COMMAND_UI 處理常式中。

1. 呼叫[SetPaneText](#setpanetext)更新任何窗格的文字。

呼叫[SetPaneStyle](#setpanestyle)更新狀態列窗格的樣式。

如需有關使用`CStatusBar`，請參閱文章[MFC 中的狀態列實作](../../mfc/status-bar-implementation-in-mfc.md)並[技術提示 31： 控制列](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

取得指標的索引指定的識別碼。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
字串的指標，其索引為要擷取的識別碼。

### <a name="return-value"></a>傳回值

成功; 如果指標的索引如果不成功，為-1。

### <a name="remarks"></a>備註

第一個指標的索引為 0。

##  <a name="create"></a>  CStatusBar::Create

建立狀態列 （子視窗），並將其與相關聯`CStatusBar`物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 視窗是 [狀態] 列的父代的物件。

*cheaderctrl:: Create*<br/>
狀態列樣式。 除了標準的 Windows[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)，支援這些樣式。

- CBRS_TOP 控制列是在框架視窗的頂端。

- CBRS_BOTTOM 控制列是在框架視窗的底部。

- 父代調整大小時，不會重新定位 CBRS_NOALIGN 控制列。

*nID*<br/>
工具列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

也設定初始的字型，並將狀態設定為預設值的長條的高度。

##  <a name="createex"></a>  CStatusBar::CreateEx

呼叫此函式來建立狀態列 （子視窗） 和其關聯`CStatusBar`物件。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 視窗是 [狀態] 列的父代的物件。

*dwCtrlStyle*<br/>
建立內嵌的其他樣式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件。 預設值會指定狀態列，而不需要調整大小底框或工具提示支援。 支援的狀態 列樣式如下：

- SBARS_SIZEGRIP 狀態列控制項包括最右邊的 [狀態] 列的調整大小底框。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

- SBT_TOOLTIPS 狀態列支援工具提示。

如需這些樣式的詳細資訊，請參閱[CStatusBarCtrl 的設定](../../mfc/settings-for-the-cstatusbarctrl.md)。

*cheaderctrl:: Create*<br/>
狀態列樣式。 預設值會指定顯示狀態列，建立框架視窗的底部。 套用狀態列控制項的樣式中所列的任何組合[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)並[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 不過，此參數應該一律包含 WS_CHILD 和 WS_VISIBLE 樣式。

*nID*<br/>
[狀態] 列的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式也會設定初始的字型，並將狀態設定為預設值的長條的高度。

使用`CreateEx`，而不是[建立](#create)，當特定樣式必須存在期間的內嵌的狀態列控制項。 例如，設定*dwCtrlStyle*至 SBT_TOOLTIPS 狀態 列物件中顯示工具提示。

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

建構`CStatusBar`物件會建立如有必要，預設狀態列字型和字型特性設定為預設值。

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

此成員函式稱為架構時為主控描繪狀態列會變更的視覺外觀。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
指標[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)結構，其中包含的所需的繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CStatusBar`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前終止此成員函式。

##  <a name="getitemid"></a>  CStatusBar::GetItemID

會傳回識別碼所指定的指標*nIndex*。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指標，其識別碼是要擷取的索引。

### <a name="return-value"></a>傳回值

指標所指定的識別碼*nIndex*。

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

複製指標所指定的座標*nIndex*所指向的結構*lpRect*。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取其矩形座標的指標的索引。

*lpRect*<br/>
指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)都會有一個指標所指定的座標的物件*nIndex*。

### <a name="remarks"></a>備註

座標是相對於左上角的 [狀態] 列的像素。

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

設定組*nID*， *nStyle*，和*cxWidth* ID、 樣式和所指定的位置指標窗格的寬度*nIndex*。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取其資訊窗格的索引。

*nID*<br/>
參考設定 窗格的識別碼為 UINT。

*nStyle*<br/>
設定窗格的樣式為 UINT 參考。

*cxWidth*<br/>
窗格的寬度設為整數的參考。

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

呼叫此成員函式可擷取的狀態列窗格的樣式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[] 窗格中的樣式為要擷取的索引。

### <a name="return-value"></a>傳回值

[狀態列] 窗格中所指定的樣式*nIndex*。

### <a name="remarks"></a>備註

窗格的樣式會判斷窗格的顯示方式。

如需可用的狀態列樣式的清單，請參閱 <<c0> [ 建立](#create)。

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

呼叫此成員函式，以擷取出現在狀態列窗格的文字。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取其文字窗格的索引。

*rString*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要擷取的文字。

### <a name="return-value"></a>傳回值

A`CString`物件，其中包含窗格的文字。

### <a name="remarks"></a>備註

這個成員的第二種形式的函式會填滿`CString`具有字串文字物件。

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

此成員函式允許直接存取基礎的通用控制項。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>傳回值

包含的參考[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件。

### <a name="remarks"></a>備註

使用`GetStatusBarCtrl`善用 Windows 狀態列上常見的控制項的功能，並利用支援[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供狀態列自訂。 例如，藉由使用通用控制項，您可以指定包含 [狀態] 列上的調整大小底框樣式，或您可以指定將出現在父視窗的工作區頂端的 [狀態] 列的樣式。

更多一般通用控制項的詳細資訊，請參閱[通用控制項](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

每個指標的識別碼設定為陣列的對應項目所指定的值*lpIDArray*、 載入每個識別碼所指定的字串資源，並將指標的文字設為字串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
識別碼的陣列指標。

*nIDCount*<br/>
所指陣列中的項目數*lpIDArray*。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

將指定的指標窗格設定為新的識別碼、 樣式和寬度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
其樣式是設為 [指標] 窗格的索引。

*nID*<br/>
[指標] 窗格中的新識別碼。

*nStyle*<br/>
[指標] 窗格中的新樣式。

*cxWidth*<br/>
[指標] 窗格中的新寬度。

### <a name="remarks"></a>備註

支援下列指標樣式：

- SBPS_NOBORDERS 否 [] 窗格周圍的 3d 框線。

- SBPS_POPOUT 反轉框線，讓文字 「 彈出。 」

- SBPS_DISABLED 不繪製文字。

- SBPS_STRETCH Stretch 窗格，以填滿未使用的空間。 每個狀態 列只有一個窗格可以有此樣式。

- SBPS_NORMAL 否 stretch、 框線或彈出。

##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle

呼叫此成員函式設定的狀態列窗格的樣式。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
是設定其樣式 窗格的索引。

*nStyle*<br/>
是設定其樣式 窗格的樣式。

### <a name="remarks"></a>備註

窗格的樣式會判斷窗格的顯示方式。

如需可用的狀態列樣式的清單，請參閱 < [SetPaneInfo](#setpaneinfo)。

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

呼叫此成員函式，來設定窗格中文字所指向的字串*lpszNewText*。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
設定為其文字窗格的索引。

*lpszNewText*<br/>
新的窗格中文字的指標。

*bUpdate*<br/>
如果為 TRUE，窗格已失效之後設定文字。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

在您呼叫後`SetPaneText`，您必須新增新的文字顯示在狀態列中的 UI 更新處理常式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[MFC 範例 DLGCBR32](../../visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 類別](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
