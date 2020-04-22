---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: c2f8ea48bf9a1f015928650085b07198b152771a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754795"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控制件欄類 CStatusBar、CToolBar、CDialogBar、CRebar[CReBar](../../mfc/reference/crebar-class.md)和[COleResizebar](../../mfc/reference/coleresizebar-class.md)[CStatusBar](../../mfc/reference/cstatusbar-class.md)[CToolBar](../../mfc/reference/ctoolbar-class.md)[CDialogBar](../../mfc/reference/cdialogbar-class.md)的基類。

## <a name="syntax"></a>語法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[C控制列:C控制列](#ccontrolbar)|建構 `CControlBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C控制列::CalcDynamic佈局](#calcdynamiclayout)|將動態控制欄的大小作為[CSize](../../atl-mfc-shared/reference/csize-class.md)物件返回。|
|[C控制欄::卡爾卡固定佈局](#calcfixedlayout)|將控制列的大小作為[CSize](../../atl-mfc-shared/reference/csize-class.md)物件返回。|
|[C控制欄::卡爾卡內雷茨](#calcinsiderect)|返回控制條區域的當前尺寸;包括邊界。|
|[C控制欄::DoPaint](#dopaint)|渲染控制欄的邊框和夾持器。|
|[C控制列::D原始邊界](#drawborders)|渲染控制欄的邊框。|
|[C控制欄::D原始夾鉗](#drawgripper)|渲染控制條的夾持器。|
|[C控制列::啟用停靠](#enabledocking)|允許停靠或浮動控制欄。|
|[C控制列:抓取欄樣式](#getbarstyle)|檢索控制欄樣式設置。|
|[C控制列:抓取邊框](#getborders)|檢索控制欄的邊框值。|
|[C控制列:取得計數](#getcount)|返回控制欄中非 HWND 元素的數量。|
|[C控制列:取得延伸幀](#getdockingframe)|返回指向控件欄停靠到的幀的指標。|
|[C控制列:是浮動的](#isfloating)|如果有問題的控制欄是浮動控制欄,則返回非零值。|
|[C控制列::更新CmdUI](#onupdatecmdui)|呼叫命令 UI 處理程式。|
|[C控制列::設定列樣式](#setbarstyle)|修改控件欄樣式設置。|
|[C控制列::設定邊框](#setborders)|設置控制欄的邊框值。|
|[C控制列::設定位置擁有者](#setinplaceowner)|更改控件欄的就地擁有者。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C控制列:m_bAutoDelete](#m_bautodelete)|如果為非零,`CControlBar`則在銷毀 Windows 控制欄時將刪除該物件。|
|[C控制列:m_pInPlaceOwner](#m_pinplaceowner)|控制欄的就地擁有者。|

## <a name="remarks"></a>備註

控制欄是通常與框架視窗的左側或右側對齊的視窗。 它可能包含基於 HWND 的控制項的子項,這些控制項是生成和回應 Windows 訊息的視窗,或者非基於 HWND 的專案,它們不是視窗,由應用程式碼或框架代碼管理。 清單框和編輯控制項是基於 HWND 的控制項的範例;狀態列窗格和位圖按鈕是基於 HWND 的控制項的範例。

控制欄視窗通常是父框架視窗的子視窗,通常是框架視窗的用戶端檢視或 MDI 用戶端的同級視窗。 對`CControlBar`象 使用有關父視窗的用戶端矩形的資訊來定位自身。 然後,它會通知父視窗在父視窗的工作區中有多少空間未分配。

有關 的詳細`CControlBar`資訊 ,請參閱:

- [控制列](../../mfc/control-bars.md)

- [技術說明31:控制欄](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>C控制列::CalcDynamic佈局

框架調用此成員函數以計算動態工具列的尺寸。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>參數

*N 長度*<br/>
控制列的所需尺寸,水平或垂直,根據*dwMode*。

*nMode*<br/>
以下預定義標誌用於確定動態控制欄的高度和寬度。 使用位 OR (&#124;) 運算符組合標誌。

|配置模式旗標|意義|
|-----------------------|-------------------|
|LM_STRETCH|指示控制欄是否應拉伸到框架的大小。 如果條形不是停靠欄(不適用於停靠),則設置。 未設置柱線停靠或浮動時(可用於停靠)。 如果設置,LM_STRETCH忽略*nLength 並根據*LM_HORZ狀態返回維度。 LM_STRETCH工作原理與[CalcFixedLayout](#calcfixedlayout)中使用的*b 拉伸*參數類似;有關拉伸和方向之間關係的更多資訊,請參閱該成員函數。|
|LM_HORZ|指示條形是水準或垂直方向的。 設置如果條形是水準方向的,並且如果它是垂直方向的,則不設置它。 LM_HORZ工作原理與[CalcFixedLayout](#calcfixedlayout)中使用的*bHorz*參數類似;有關拉伸和方向之間關係的更多資訊,請參閱該成員函數。|
|LM_MRUWIDTH|最近使用的動態寬度。 忽略*nLength 參數*並使用記住最近使用的寬度。|
|LM_HORZDOCK|水準停靠尺寸。 忽略*nLength 參數*並返回寬度最大的動態大小。|
|LM_VERTDOCK|垂直停靠尺寸。 忽略*nLength 參數*並傳回具有最大高度的動態大小。|
|LM_LENGTHY|設置*nLength*是否指示高度(Y 方向)而不是寬度。|
|LM_COMMIT|將LM_MRUWIDTH重置為浮動控制欄的當前寬度。|

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件的控制欄大小(以像素為單位)。

### <a name="remarks"></a>備註

重寫此成員函數,在派生自`CControlBar`的 類中提供您自己的動態佈局。 派生自`CControlBar`(CToolbar)[CToolbar](../../mfc/reference/ctoolbar-class.md)的 MFC 類將重寫此成員函數並提供其自己的實現。

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>C控制欄::卡爾卡固定佈局

調用此成員函數以計算控制條的水準大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*b 伸*<br/>
指示是否應將條形拉伸到框架的大小。 當條形不是停靠柱(不適用於停靠條)時 *,bStretch*參數為非零,在停靠或浮動時為 0(可用於停靠)。

*布霍茲*<br/>
指示條形是水準或垂直方向的。 如果條形是水準方向,*則 bHorz*參數為非零;如果條形是垂直方向,則為 0。

### <a name="return-value"></a>傳回值

`CSize`物件的控制列列大小(以像素為單位)。

### <a name="remarks"></a>備註

工具列等控制欄可以水準或垂直拉伸,以適應控制欄中包含的按鈕。

如果*bStretch*為 TRUE,則沿*bHorz*提供的方向拉伸尺寸。 換句話說,如果*bHorz*是 FALSE,則控制條是垂直拉伸的。 如果*b 拉伸*為 FALSE,則不拉伸。 下表顯示了*bStretch*和*bHorz*的可能排列和生成的控制欄樣式。

|b 伸|布霍茲|伸展|方向|停靠/未停靠|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|水平拉伸|橫向|不停靠|
|TRUE|FALSE|垂直拉伸|垂直方向|不停靠|
|FALSE|TRUE|無拉伸可用|橫向|停駐|
|FALSE|FALSE|無拉伸可用|垂直方向|停駐|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>C控制欄::卡爾卡內雷茨

框架調用此函數以計算控制欄的工作區。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>參數

*矩形*<br/>
包含控制欄的當前尺寸;包括邊界。

*布霍茲*<br/>
指示條形是水準或垂直方向的。 如果條形是水準方向,*則 bHorz*參數為非零;如果條形是垂直方向,則為 0。

### <a name="remarks"></a>備註

在繪製控制條之前調用此功能。

重寫此函數以自定義控制欄邊框和夾持欄的渲染。

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>C控制列:C控制列

建構 `CControlBar` 物件。

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>C控制欄::DoPaint

由框架調用,以呈現控制欄的邊框和夾持桿。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於渲染控制欄邊框和夾持器的設備上下文。

### <a name="remarks"></a>備註

重寫此函數以自定義控制欄的繪圖行為。

另一種自定義方法是重寫`DrawBorders``DrawGripper`和函數,併為邊框和夾持器添加自定義繪圖代碼。 由於這些方法由預設`DoPaint`方法調用,因此不需要重寫`DoPaint`。

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>C控制列::D原始邊界

由框架調用以呈現控制欄的邊框。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於呈現控制欄邊框的設備上下文。

*矩形*<br/>
包含`CRect`控制欄尺寸的物件。

### <a name="remarks"></a>備註

重寫此函數以自定義控制欄邊框的外觀。

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>C控制欄::D原始夾鉗

由框架調用以呈現控制條的夾持器。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於渲染控制欄夾持器的設備上下文。

*矩形*<br/>
包含`CRect`控制條夾持器尺寸的物件。

### <a name="remarks"></a>備註

重寫此函數以自定義控制欄夾持器的外觀。

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>C控制列::啟用停靠

調用此函數以啟用停靠控制欄。

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDock 風格*<br/>
指定控制列是否支援停靠,以及控制欄可以停靠到的父視窗的兩側(如果受支援)。 可以是以下一種或多項:

- CBRS_ALIGN_TOP 允許在工作區的頂部停靠。

- CBRS_ALIGN_BOTTOM允許在工作區的底部停靠。

- CBRS_ALIGN_LEFT 允許在工作區左側停靠。

- CBRS_ALIGN_RIGHT允許在工作區的右側停靠。

- CBRS_ALIGN_ANY 允許在工作區的任何一側停靠。

- CBRS_FLOAT_MULTI 允許在單個微型框架視窗中浮動多個控制欄。

如果 0(即表示沒有標誌),則控制欄將不會停靠。

### <a name="remarks"></a>備註

指定的邊必須與啟用在目標幀視窗中停靠的一個邊匹配,或者控制欄無法停靠到該幀視窗。

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>C控制列:抓取欄樣式

呼叫此函數以確定目前為控制欄設定了哪些**CBRS_(** 控制欄樣式)設置。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>傳回值

控制列的目前**CBRS_(** 控制列樣式)設定。 有關可用樣式的完整清單,請參閱[CControlBar:設定列樣式](#setbarstyle)。

### <a name="remarks"></a>備註

不處理**WS_(** 視窗樣式)樣式。

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>C控制列:抓取邊框

返回控制欄的當前邊框值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>傳回值

包含`CRect`控制欄物件每側的當前寬度(以像素為單位)的物件。 例如[,CRect](../../atl-mfc-shared/reference/crect-class.md)物件的*左側*成員的值是左側邊框的寬度。

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>C控制列:取得計數

返回`CControlBar`物件上的非 HWND 項數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

`CControlBar`物件上的非 HWND 項數。 對於[CDialogBar](../../mfc/reference/cdialogbar-class.md)物件,此功能返回 0。

### <a name="remarks"></a>備註

項的類型取決於派生物件[:CStatusBar](../../mfc/reference/cstatusbar-class.md)物件的窗格,[以及 CToolBar](../../mfc/reference/ctoolbar-class.md)物件的按鈕和分隔符。

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>C控制列:取得延伸幀

呼叫此成員函數以獲取指向控制列列停靠的當前幀視窗的指標。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>傳回值

指向幀視窗的指標(如果成功);如果成功,則指向框架視窗的指標。否則 NULL。

如果控制欄未停靠到框架視窗(即,如果控制欄是浮動的),則此函數將返回指向其父[CMiniFrameWnd 的](../../mfc/reference/cminiframewnd-class.md)指標。

### <a name="remarks"></a>備註

有關可停靠控制欄的詳細資訊,請參閱[CControlBar:啟用停靠](#enabledocking)和[CFramewnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>C控制列:是浮動的

調用此成員函數以確定控制欄是浮動還是停靠。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>傳回值

如果控制條是浮動的,則非零;否則 0。

### <a name="remarks"></a>備註

要將控制列的狀態從停靠更改為浮動,請致電[CFrameWnd::floatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>C控制列:m_bAutoDelete

如果為非零,`CControlBar`則在銷毀 Windows 控制欄時將刪除該物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

*m_bAutoDelete*是 BOOL 類型的公共變數。

控制列物件通常嵌入到框架視窗物件中。 在這種情況下 *,m_bAutoDelete*為 0,因為在破壞幀視窗時,嵌入的控制欄物件將被摧毀。

如果在堆上分配`CControlBar`物件,並且不打算調用**delete**, 則此變數將設置為非零值。

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>C控制列:m_pInPlaceOwner

控制欄的就地擁有者。

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>C控制列::更新CmdUI

框架調用此成員函數以更新工具列或狀態列的狀態。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>參數

*p 目標*<br/>
指向應用程式的主框架視窗。 此指標用於路由更新消息。

*b 關閉IfNoHndler*<br/>
指示是否應自動顯示為禁用的控制件的標誌。

### <a name="remarks"></a>備註

要更新單個按鈕或窗格,請使用消息映射中的ON_UPDATE_COMMAND_UI宏來適當地設置更新處理程式。 有關使用此宏的詳細資訊,請參閱[ON_UPDATE_COMMAND_UI。](message-map-macros-mfc.md#on_update_command_ui)

`OnUpdateCmdUI`當應用程序處於空閒狀態時,框架調用。 要更新的幀窗口必須是可見框架視窗的子視窗,至少間接是。 `OnUpdateCmdUI`是一個先進的超易。

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>C控制列::設定列樣式

調用此函數以設置控制件欄所需的**CBRS_** 樣式。

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
控制欄所需的樣式。 可以是以下一種或多項:

- CBRS_ALIGN_TOP 允許將控制欄停靠到框架視窗的工作區頂部。

- CBRS_ALIGN_BOTTOM 允許控制列停靠到框架視窗的工作區的底部。

- CBRS_ALIGN_LEFT允許控制欄停靠到框架視窗的工作區的左側。

- CBRS_ALIGN_RIGHT 允許控制欄停靠到框架視窗的工作區的右側。

- CBRS_ALIGN_ANY 允許控制欄停靠到框架視窗的工作區的任何一側。

- CBRS_BORDER_TOP 使邊框在控制欄的頂部邊緣上繪製時可見。

- CBRS_BORDER_BOTTOM 使邊框在控制欄的底部邊緣上繪製時可見。

- CBRS_BORDER_LEFT 使邊框在控制欄的左邊緣上繪製時可見。

- CBRS_BORDER_RIGHT 使邊框在控制欄的右邊緣上繪製時可見。

- CBRS_FLOAT_MULTI 允許在單個微型框架視窗中浮動多個控制欄。

- CBRS_TOOLTIPS 使工具提示顯示在控制欄上。

- CBRS_FLYBY 使郵件文本與工具提示同時更新。

- CBRS_GRIPPER 使抓手(類似`CReBar`於 物件中波段中使用的抓手)繪製`CControlBar`為任何 派生類。

### <a name="remarks"></a>備註

不影響**WS_(** 視窗樣式)設定。

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>C控制列::設定邊框

呼叫此函數以設置控制欄邊框的大小。

```cpp
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*cx 左*<br/>
控件欄左邊框的寬度(以像素為單位)。

*cyTop*<br/>
控制欄頂部邊框的高度(以像素為單位)。

*cxRight*<br/>
控件欄右邊框的寬度(以像素為單位)。

*cyBottom*<br/>
控制欄底部邊框的高度(以像素為單位)。

*lpRect*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標,其中包含控制項欄物件每個邊框的當前寬度(以圖元為單位)。

### <a name="example"></a>範例

以下代碼示例將控制欄的頂部和底部邊框設定為 5 像素,左側和右側邊框為 2 圖元:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>C控制列::設定位置擁有者

更改控件欄的就地擁有者。

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
`CWnd` 物件的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 類別](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 類別](../../mfc/reference/crebar-class.md)
