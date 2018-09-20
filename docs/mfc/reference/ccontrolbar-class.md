---
title: CControlBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd69813251a96051f844051f27155e1d4ed404d6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393414"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控制列類別的基底類別[CStatusBar](../../mfc/reference/cstatusbar-class.md)， [CToolBar](../../mfc/reference/ctoolbar-class.md)， [CDialogBar](../../mfc/reference/cdialogbar-class.md)， [CReBar](../../mfc/reference/crebar-class.md)，和[COleResizeBar](../../mfc/reference/coleresizebar-class.md)。

## <a name="syntax"></a>語法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|建構 `CControlBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|傳回做為動態的控制列的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|傳回做為控制列的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|
|[CControlBar::CalcInsideRect](#calcinsiderect)|傳回目前維度的控制列的區域。包括框線。|
|[CControlBar::DoPaint](#dopaint)|呈現的框線和移駐夾的控制列。|
|[CControlBar::DrawBorders](#drawborders)|呈現控制列的框線。|
|[CControlBar::DrawGripper](#drawgripper)|呈現的移駐夾的控制列。|
|[CControlBar::EnableDocking](#enabledocking)|可讓控制列是停駐或浮動。|
|[CControlBar::GetBarStyle](#getbarstyle)|擷取控制項的列樣式設定。|
|[CControlBar::GetBorders](#getborders)|擷取控制列的邊界值。|
|[CControlBar::GetCount](#getcount)|控制列中傳回非 HWND 項目數目。|
|[CControlBar::GetDockingFrame](#getdockingframe)|傳回要停駐控制列的框架指標。|
|[CControlBar::IsFloating](#isfloating)|如果有問題的控制列是浮動的控制列，則傳回非零值。|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|呼叫命令 UI 處理常式。|
|[CControlBar::SetBarStyle](#setbarstyle)|修改控制項的列樣式設定。|
|[CControlBar::SetBorders](#setborders)|設定控制列的邊界值。|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|變更一種控制列的就地擁有者。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|如果是非零值，`CControlBar`終結 Windows 控制列時，會刪除物件。|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|控制列的就地擁有者。|

## <a name="remarks"></a>備註

一種控制列是通常會對齊框架視窗左邊或右邊的視窗。 它可能包含作為 HWND 型控制項，也就是產生和回應 Windows 訊息的視窗，或是非 HWND 型項目，而且非屬 windows 應用程式程式碼或架構程式碼所管理的子項目。 清單方塊和編輯控制項是作為 HWND 型控制項; 的範例狀態列窗格的點陣圖按鈕等的非 HWND 型控制項範例。

控制列視窗通常是父框架視窗的子視窗，和通常是用戶端檢視或 MDI 框架視窗的用戶端的同層級。 A`CControlBar`物件用來決定本身的位置的父視窗的用戶端矩形的相關資訊。 接著，它會通知父視窗，並在父視窗的工作區中維持未配置多少空間。

如需有關`CControlBar`，請參閱：

- [控制列](../../mfc/control-bars.md)

- [技術提示 31： 控制列](../../mfc/tn031-control-bars.md)。

- 眭妎踱恅 Q242577: PRB： 更新命令 UI 處理常式執行無法運作的功能表附加至對話方塊

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

架構會呼叫此成員函式，來計算的動態工具列的維度。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>參數

*nLength*<br/>
控制列，水平或垂直的取決於要求的維度*dwMode*。

*nMode*<br/>
下列預先定義的旗標用來決定動態控制列的寬度與高度。 使用位元 OR (&#124;) 運算子來結合旗標。

|版面配置模式旗標|意義|
|-----------------------|-------------------|
|LM_STRETCH|表示將控制列是否應該自動縮放以畫面格的大小。 如果列不是一種停駐列 （不適用於停駐），設定。 未設定停駐或浮動列時 （適用於停駐）。 如果設定，LM_STRETCH 會忽略*nLength* ，並傳回 LM_HORZ 狀態為基礎的維度。 LM_STRETCH 運作方式類似*bStretch*中所使用的參數[CalcFixedLayout](#calcfixedlayout); 請參閱該成員函式，如需有關之間自動縮放和方向的關聯性。|
|LM_HORZ|指出軸是水平或垂直方向。 如果軸是水平方向，而且如果是垂直方向，未設定，設定。 LM_HORZ 運作方式類似*bHorz*中所使用的參數[CalcFixedLayout](#calcfixedlayout); 請參閱該成員函式，如需有關之間自動縮放和方向的關聯性。|
|LM_MRUWIDTH|最近使用的動態寬度。 會忽略*nLength*參數，然後使用記住最近使用的寬度。|
|LM_HORZDOCK|水平停駐的維度。 會忽略*nLength*參數並傳回具有最大寬度的動態大小。|
|LM_VERTDOCK|垂直停駐的維度。 會忽略*nLength*參數並傳回具有最大高度動態的大小。|
|LM_LENGTHY|如果設定*nLength*表示高度 （Y 方向），而不是寬度。|
|LM_COMMIT|將 LM_MRUWIDTH 浮動的控制列的目前寬度來重設。|

### <a name="return-value"></a>傳回值

控制列的大小，單位為像素的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

### <a name="remarks"></a>備註

覆寫此成員函式，以提供您自己的衍生的類別中的動態配置`CControlBar`。 MFC 類別衍生自`CControlBar`，這類[CToolbar](../../mfc/reference/ctoolbar-class.md)、 覆寫此成員函式，並提供自己的實作。

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

呼叫此成員函式，來計算的控制列的水平大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*bStretch*<br/>
指出軸是否應該自動縮放以框架的大小。 *BStretch*列 （不適用於停駐） 的停駐列並不是 0 停駐或浮動時 （適用於停駐） 時，參數為非零值。

*bHorz*<br/>
指出軸是水平或垂直方向。 *BHorz*參數為非零值，如果列是水平方向，而是 0，如果是垂直方向。

### <a name="return-value"></a>傳回值

控制列的大小，單位為像素的`CSize`物件。

### <a name="remarks"></a>備註

控制列，例如工具列可以延伸至水平或垂直適應按鈕中含控制列。

如果*bStretch*為 TRUE 時，延伸所提供的方向沿著維度*bHorz*。 換句話說，如果*bHorz*為 FALSE 時，垂直縮放控制列。 如果*bStretch*為 FALSE 時，不支援延展，就會發生。 下表顯示可能的排列方式，以及產生的控制列樣式的*bStretch*並*bHorz*。

|bStretch|bHorz|自動縮放|方向|停駐/未停駐|
|--------------|-----------|----------------|-----------------|--------------------------|
|true|true|水平縮放|水平導向|不停駐|
|true|false|垂直縮放|垂直導向|不停駐|
|false|true|提供沒有自動縮放|水平導向|停駐|
|false|false|提供沒有自動縮放|垂直導向|停駐|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

架構會呼叫此函式來計算工作區的控制列。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>參數

*rect*<br/>
包含目前維度的控制列;包括框線。

*bHorz*<br/>
指出軸是水平或垂直方向。 *BHorz*參數為非零值，如果列是水平方向，而是 0，如果是垂直方向。

### <a name="remarks"></a>備註

控制列繪製之前，會呼叫此函數。

覆寫此函式可自訂的框線和控制列的移駐夾列轉譯。

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

建構 `CControlBar` 物件。

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

由架構呼叫以呈現的框線和控制列的移駐夾列。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要用於呈現的框線和控制列的移駐夾的裝置內容指標。

### <a name="remarks"></a>備註

覆寫此函式以自訂繪製行為的控制列。

另一種自訂方法會覆寫`DrawBorders`和`DrawGripper`函式和加入自訂框線的移駐夾的繪圖程式碼。 根據預設，會呼叫這些方法，因為`DoPaint`方法中，覆寫`DoPaint`不需要。

##  <a name="drawborders"></a>  CControlBar::DrawBorders

由架構呼叫以呈現控制列的框線。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要用於轉譯的控制列框線的裝置內容指標。

*rect*<br/>
A`CRect`物件，包含維度的控制列。

### <a name="remarks"></a>備註

覆寫此函式可自訂的控制項列框線外觀。

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

由架構呼叫以呈現的移駐夾的控制列。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
裝置內容，以用來呈現控制項列移駐夾的點。

*rect*<br/>
A`CRect`物件，其中包含控制列的移駐夾的維度。

### <a name="remarks"></a>備註

覆寫此函式可自訂的控制項列移駐夾的外觀。

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

呼叫此函式，可讓被停駐控制列。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDockStyle*<br/>
如果支援，請指定是否將控制列支援停駐和側邊，可以停駐控制列，其父視窗。 可以是下列其中一個或多個項目：

- CBRS_ALIGN_TOP 可停駐在工作區頂端。

- CBRS_ALIGN_BOTTOM 可讓工作區底部的停駐。

- CBRS_ALIGN_LEFT 可讓用戶端區域左側停駐。

- CBRS_ALIGN_RIGHT 可讓用戶端區域右側的停駐。

- CBRS_ALIGN_ANY 可讓用戶端區域的任一邊的停駐。

- CBRS_FLOAT_MULTI 可讓多個控制列，以在單一的迷你框架視窗中浮動顯示。

如果為 0 （亦即表示沒有旗標），將不會停駐控制列。

### <a name="remarks"></a>備註

指定的側邊必須符合其中一個已啟用在目的地框架視窗中，停駐的側邊或無法至該框架視窗停駐控制列。

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

呼叫此函式可判斷哪些**CBRS_** （控制項的列樣式） 目前設定的控制列。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>傳回值

目前**CBRS_** 控制列 （控制項的列樣式） 設定。 請參閱[CControlBar::SetBarStyle](#setbarstyle)可用樣式的完整清單。

### <a name="remarks"></a>備註

不會處理**WS_** （視窗樣式） 樣式。

##  <a name="getborders"></a>  CControlBar::GetBorders

傳回目前的控制列的邊界值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>傳回值

A`CRect`物件，其中包含控制列物件的每一端的目前寬度 （以像素為單位）。 例如，值*左*成員的[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，是左框線的寬度。

##  <a name="getcount"></a>  CControlBar::GetCount

傳回非 HWND 項目數目上`CControlBar`物件。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

非 HWND 上的項目數`CControlBar`物件。 此函數會傳回 0 代表[CDialogBar](../../mfc/reference/cdialogbar-class.md)物件。

### <a name="remarks"></a>備註

項目類型取決於衍生的物件： 窗格[CStatusBar](../../mfc/reference/cstatusbar-class.md)物件和按鈕和分隔符號以[CToolBar](../../mfc/reference/ctoolbar-class.md)物件。

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

呼叫此成員函式可取得目前的框架視窗的停駐控制列的指標。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>傳回值

如果成功，框架視窗的指標否則為 NULL。

如果控制列未停駐在框架視窗 （亦即，如果浮點控制列），此函式會傳回指標至其父代[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)。

### <a name="remarks"></a>備註

如需有關可停駐控制列的詳細資訊，請參閱[CControlBar::EnableDocking](#enabledocking)並[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

##  <a name="isfloating"></a>  CControlBar::IsFloating

呼叫此成員函式，以判斷是否浮動或停駐控制列。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>傳回值

控制列浮點數; 如果為非零否則為 0。

### <a name="remarks"></a>備註

若要變更狀態的一種控制列從停駐到浮點數，呼叫[CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

如果是非零值，`CControlBar`終結 Windows 控制列時，會刪除物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

*create_suspended*會 BOOL 類型的公用變數。

控制列物件通常內嵌於框架視窗物件。 在此情況下， *create_suspended*為 0，因為內嵌的控制列物件終結時終結框架視窗。

將這個變數設為非零值，如果您配置`CControlBar`物件在堆積和您不打算呼叫**刪除**。

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

控制列的就地擁有者。

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

以更新工具列或狀態列的狀態，架構會呼叫此成員函式。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>參數

*pTarget*<br/>
指向主框架視窗的 應用程式。 此指標使用於路由傳送更新訊息。

*bDisableIfNoHndler*<br/>
旗標，指出是否不有任何更新處理常式的控制項應該自動顯示為已停用。

### <a name="remarks"></a>備註

若要更新的個別按鈕或窗格中，使用訊息對應中 ON_UPDATE_COMMAND_UI 巨集，適當地設定更新處理常式。 請參閱[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)如需使用這個巨集的詳細資訊。

`OnUpdateCmdUI` 是由架構呼叫，當應用程式處於閒置狀態。 更新框架視窗必須是子視窗，至少間接地顯示框架視窗。 `OnUpdateCmdUI` 是一種進階可覆寫。

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

呼叫此函式來設定所需**CBRS_** 控制列的樣式。

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
控制列所需的樣式。 可以是下列其中一個或多個項目：

- CBRS_ALIGN_TOP 可讓被停駐在框架視窗的工作區頂端控制列。

- CBRS_ALIGN_BOTTOM 可以讓框架視窗的 [用戶端] 區域底部停駐控制列。

- CBRS_ALIGN_LEFT 可讓工作區框架視窗的左側停駐控制列。

- CBRS_ALIGN_RIGHT 可讓控制列固定到用戶端區域中，框架視窗的右側。

- CBRS_ALIGN_ANY 可讓控制列可停駐於框架視窗的工作區的任何一側。

- CBRS_BORDER_TOP 會導致在頂端列時，它會是可見的控制項上繪製框線。

- CBRS_BORDER_BOTTOM 會導致要繪製的控制列時要顯示的下邊緣的框線。

- CBRS_BORDER_LEFT 會導致列時，它會是可見的控制項左邊緣上繪製框線。

- CBRS_BORDER_RIGHT 會導致要繪製的列時，它會是可見的控制項右邊緣的框線。

- CBRS_FLOAT_MULTI 可讓多個控制列，以在單一的迷你框架視窗中浮動顯示。

- CBRS_TOOLTIPS 讓工具提示来顯示的控制列。

- CBRS_FLYBY 會導致訊息文字與工具提示同時更新。

- CBRS_GRIPPER 導致移駐夾，類似於使用中的寬線`CReBar`物件，要繪製任何`CControlBar`-衍生的類別。

### <a name="remarks"></a>備註

不會影響**WS_** （視窗樣式） 設定。

##  <a name="setborders"></a>  CControlBar::SetBorders

呼叫此函式可設定的控制列的框線大小。

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*cxLeft*<br/>
控制列的左框線的寬度 （以像素為單位）。

*cyTop*<br/>
控制列的上框線的高度 （以像素為單位）。

*cxRight*<br/>
控制列的右框線的寬度 （以像素為單位）。

*cyBottom*<br/>
控制列的下框線的高度 （以像素為單位）。

*lpRect*<br/>
指標[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含每一種框線的控制列物件的目前寬度 （以像素為單位）。

### <a name="example"></a>範例

下列程式碼範例會將 5 個像素為單位，將控制列的頂端和底端框線和左框線和右框線設定為 2 個像素：

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

變更一種控制列的就地擁有者。

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
`CWnd` 物件的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 類別](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 類別](../../mfc/reference/crebar-class.md)
