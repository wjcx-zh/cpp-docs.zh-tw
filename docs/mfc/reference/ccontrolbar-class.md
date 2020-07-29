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
ms.openlocfilehash: 7a08efb7cbe848ec6d8ccba57671f3ef0dc8e74c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212562"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控制列類別[CStatusBar](../../mfc/reference/cstatusbar-class.md)、 [CToolBar](../../mfc/reference/ctoolbar-class.md)、 [CDialogBar](../../mfc/reference/cdialogbar-class.md)、 [CReBar](../../mfc/reference/crebar-class.md)和[COleResizeBar](../../mfc/reference/coleresizebar-class.md)的基類。

## <a name="syntax"></a>語法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[CControlBar：： CControlBar](#ccontrolbar)|建構 `CControlBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CControlBar：： CalcDynamicLayout](#calcdynamiclayout)|傳回動態控制列的大小，做為[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|
|[CControlBar：： CalcFixedLayout](#calcfixedlayout)|以[CSize](../../atl-mfc-shared/reference/csize-class.md)物件的形式傳回控制列的大小。|
|[CControlBar：： CalcInsideRect](#calcinsiderect)|傳回控制欄區域的目前維度。包括框線。|
|[CControlBar：:D oPaint](#dopaint)|呈現控制列的框線和移駐夾。|
|[CControlBar：:D rawBorders](#drawborders)|呈現控制列的框線。|
|[CControlBar：:D rawGripper](#drawgripper)|呈現控制列的移駐夾。|
|[CControlBar：： EnableDocking](#enabledocking)|允許固定或浮動控制列。|
|[CControlBar：： GetBarStyle](#getbarstyle)|抓取控制列樣式設定。|
|[CControlBar：：可以 getborders 擷取](#getborders)|抓取控制列的框線值。|
|[CControlBar：： GetCount](#getcount)|傳回控制列中的非 HWND 元素數目。|
|[CControlBar：： GetDockingFrame](#getdockingframe)|傳回控制項列停駐所在之框架的指標。|
|[CControlBar：： IsFloating](#isfloating)|如果有問題的控制列是浮動控制列，則會傳回非零值。|
|[CControlBar：： OnUpdateCmdUI](#onupdatecmdui)|呼叫命令 UI 處理常式。|
|[CControlBar：： SetBarStyle](#setbarstyle)|修改控制列樣式設定。|
|[CControlBar：： SetBorders](#setborders)|設定控制列的框線值。|
|[CControlBar：： SetInPlaceOwner](#setinplaceowner)|變更控制列的就地擁有者。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CControlBar：： m_bAutoDelete](#m_bautodelete)|如果是非零值，則 `CControlBar` 當 Windows 控制列終結時，就會刪除該物件。|
|[CControlBar：： m_pInPlaceOwner](#m_pinplaceowner)|控制列的就地擁有者。|

## <a name="remarks"></a>備註

控制列是一個視窗，通常會對齊框架視窗的左側或右側。 它可能會包含一個 HWND 型控制項的子專案，也就是產生和回應 Windows 訊息的 windows，或是非以 HWND 為基礎的專案（不是 windows，而且是由應用程式代碼或架構程式碼所管理）。 清單方塊和編輯控制項都是以 HWND 為基礎的控制項範例。[狀態列窗格] 和 [點陣圖] 按鈕是非 HWND 控制項的範例。

控制列視窗通常是父框架視窗的子視窗，通常是在框架視窗的用戶端視圖或 MDI 用戶端的同級。 `CControlBar`物件會使用父視窗的用戶端矩形的相關資訊來定位其本身。 然後，它會通知父視窗，指出父視窗的工作區中有多少空間維持未配置。

如需有關的詳細資訊 `CControlBar` ，請參閱：

- [控制列](../../mfc/control-bars.md)

- [技術提示31：控制](../../mfc/tn031-control-bars.md)列。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h。h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar：： CalcDynamicLayout

架構會呼叫這個成員函式來計算動態工具列的維度。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>參數

*nLength*<br/>
控制項列的要求維度（水準或垂直），視*dwMode*而定。

*nMode*<br/>
下列預先定義的旗標是用來決定動態控制列的高度和寬度。 使用位 OR （&#124;）運算子來結合旗標。

|版面配置模式旗標|代表的意義|
|-----------------------|-------------------|
|LM_STRETCH|指出是否應將控制列延展到框架的大小。 如果橫條不是停駐列（無法用於停駐），則設定為。 當橫條停駐或浮動（可供停駐）時設定。 如果設定，LM_STRETCH 會忽略*nLength* ，並根據 LM_HORZ 狀態傳回維度。 LM_STRETCH 的運作方式類似于[CalcFixedLayout](#calcfixedlayout)中所使用的*bStretch*參數;如需有關延展和方向之間關聯性的詳細資訊，請參閱該成員函式。|
|LM_HORZ|表示橫條是水準或垂直方向。 如果橫條是水準方向，則設定為，如果它是垂直方向，則不會設定。 LM_HORZ 的運作方式類似于[CalcFixedLayout](#calcfixedlayout)中所使用的*bHorz*參數;如需有關延展和方向之間關聯性的詳細資訊，請參閱該成員函式。|
|LM_MRUWIDTH|最近使用過的動態寬度。 忽略*nLength*參數，並使用記住的最近使用寬度。|
|LM_HORZDOCK|水準停駐的維度。 忽略*nLength*參數，並傳回具有最大寬度的動態大小。|
|LM_VERTDOCK|垂直停駐的維度。 忽略*nLength*參數，並傳回具有最大高度的動態大小。|
|LM_LENGTHY|如果*nLength*表示高度（Y 方向）而不是寬度，則設定為。|
|LM_COMMIT|將 LM_MRUWIDTH 重設為浮動控制列的目前寬度。|

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件的控制列大小（以圖元為單位）。

### <a name="remarks"></a>備註

覆寫這個成員函式，以在衍生自的類別中提供您自己的動態配置 `CControlBar` 。 衍生自的 MFC 類別 `CControlBar` （例如[CToolbar](../../mfc/reference/ctoolbar-class.md)）會覆寫這個成員函式，並提供自己的實作為。

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar：： CalcFixedLayout

呼叫這個成員函式以計算控制項列的水準大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*bStretch*<br/>
指出是否要將橫條延展到框架的大小。 當橫條不是停駐列（無法用於停駐）時， *bStretch*參數為非零，而當停駐或浮動（可供停駐）時為0。

*bHorz*<br/>
表示橫條是水準或垂直方向。 如果橫條是水準方向， *bHorz*參數是非零，如果是垂直方向，則為0。

### <a name="return-value"></a>傳回值

物件的控制列大小（以圖元為單位） `CSize` 。

### <a name="remarks"></a>備註

工具列之類的控制列可以水準或垂直延展，以容納控制列中包含的按鈕。

如果*bStretch*為 TRUE，請沿著*bHorz*所提供的方向來延展維度。 換句話說，如果*bHorz*為 FALSE，則控制列會垂直延展。 如果*bStretch*為 FALSE，則不會發生 stretch。 下表顯示*bStretch*和*bHorz*的可能排列和產生的控制列樣式。

|bStretch|bHorz|因|方向|停駐/不停駐|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|水準延展|水準方向|未停駐|
|TRUE|FALSE|垂直延展|垂直方向|未停駐|
|FALSE|TRUE|沒有可用的延展|水準方向|停駐|
|FALSE|FALSE|沒有可用的延展|垂直方向|停駐|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar：： CalcInsideRect

架構會呼叫這個函式來計算控制列的工作區。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>參數

*各種*<br/>
包含控制項列的目前維度;包括框線。

*bHorz*<br/>
表示橫條是水準或垂直方向。 如果橫條是水準方向， *bHorz*參數是非零，如果是垂直方向，則為0。

### <a name="remarks"></a>備註

在繪製控制列之前，會呼叫這個函式。

覆寫這個函式，以自訂控制項列的框線和移駐夾列的呈現。

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar：： CControlBar

建構 `CControlBar` 物件。

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar：:D oPaint

由架構呼叫來呈現控制列的框線和移駐夾列。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要用來呈現控制列框線和移駐夾的裝置內容。

### <a name="remarks"></a>備註

覆寫此函式以自訂控制項列的繪製行為。

另一個自訂方法是覆寫和函式 `DrawBorders` `DrawGripper` ，並加入框線和移駐夾的自訂繪圖程式碼。 因為這些方法是由預設方法所呼叫 `DoPaint` ，所以 `DoPaint` 不需要覆寫。

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar：:D rawBorders

由架構呼叫來呈現控制列的框線。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用來呈現控制列框線的裝置內容。

*各種*<br/>
`CRect`物件，包含控制列的維度。

### <a name="remarks"></a>備註

覆寫此函式以自訂控制列框線的外觀。

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar：:D rawGripper

由架構呼叫來呈現控制列的移駐夾。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於呈現控制列移駐夾的裝置內容。

*各種*<br/>
物件，包含控制列移駐夾的 `CRect` 維度。

### <a name="remarks"></a>備註

覆寫此函式以自訂控制列移駐夾的外觀。

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar：： EnableDocking

呼叫此函式可讓控制列固定。

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

*dwDockStyle*<br/>
指定控制列是否支援停駐以及控制列可以停駐的父視窗側邊（如果支援的話）。 可以是下列一或多個：

- CBRS_ALIGN_TOP 允許停駐在工作區的頂端。

- CBRS_ALIGN_BOTTOM 允許在工作區的底部停駐。

- CBRS_ALIGN_LEFT 允許停駐在工作區的左邊。

- CBRS_ALIGN_RIGHT 允許在工作區的右側停駐。

- CBRS_ALIGN_ANY 允許在工作區的任何一邊停駐。

- CBRS_FLOAT_MULTI 允許在單一迷你框架視窗中浮動多個控制列。

如果為0（亦即，表示沒有旗標），控制列將不會停駐。

### <a name="remarks"></a>備註

指定的側邊必須符合目的地框架視窗中啟用停駐的其中一個邊，否則控制列無法停駐于該框架視窗。

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar：： GetBarStyle

呼叫此函式可判斷目前為控制項列設定的**CBRS_** （控制列樣式）設定。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>傳回值

控制項列的目前**CBRS_** （控制列樣式）設定。 如需可用樣式的完整清單，請參閱[CControlBar：： SetBarStyle](#setbarstyle) 。

### <a name="remarks"></a>備註

不會處理**WS_** （視窗樣式）樣式。

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar：：可以 getborders 擷取

傳回控制項列的目前框線值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>傳回值

`CRect`物件，包含控制列物件之每一端的目前寬度（以圖元為單位）。 例如，*左側*成員的值（ [CRect](../../atl-mfc-shared/reference/crect-class.md)物件）是左邊框線的寬度。

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar：： GetCount

傳回物件上非 HWND 專案的數目 `CControlBar` 。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

物件上的非 HWND 專案數目 `CControlBar` 。 針對[CDialogBar](../../mfc/reference/cdialogbar-class.md)物件，此函式會傳回0。

### <a name="remarks"></a>備註

專案的類型取決於 [衍生物件： [CStatusBar](../../mfc/reference/cstatusbar-class.md)物件的窗格] 和 [ [CToolBar](../../mfc/reference/ctoolbar-class.md)物件的按鈕和分隔符號]。

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar：： GetDockingFrame

呼叫這個成員函式可取得控制項列停駐所在之目前框架視窗的指標。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為框架視窗的指標;否則為 Null。

如果控制列未停駐在框架視窗（也就是，如果控制列是浮動的），此函式會傳回其父[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)的指標。

### <a name="remarks"></a>備註

如需可停駐控制列的詳細資訊，請參閱[CControlBar：： EnableDocking](#enabledocking)和[CFrameWnd：:D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar：： IsFloating

呼叫這個成員函式，以判斷控制列是浮動或停駐的。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>傳回值

如果控制列是浮動的，則為非零。否則為0。

### <a name="remarks"></a>備註

若要將控制列的狀態從停駐變更為浮動，請呼叫[CFrameWnd：： FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar：： m_bAutoDelete

如果是非零值，則 `CControlBar` 當 Windows 控制列終結時，就會刪除該物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

*m_bAutoDelete*是 BOOL 類型的公用變數。

控制列物件通常內嵌于框架視窗物件中。 在此情況下， *m_bAutoDelete*是0，因為在終結框架視窗時，內嵌的控制列物件會終結。

如果您在 `CControlBar` 堆積上設定物件，而不打算呼叫，請將此變數設定為非零值 **`delete`** 。

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar：： m_pInPlaceOwner

控制列的就地擁有者。

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar：： OnUpdateCmdUI

此成員函式是由架構呼叫，以更新工具列或狀態列的狀態。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>參數

*pTarget*<br/>
指向應用程式的主框架視窗。 此指標用於路由更新訊息。

*bDisableIfNoHndler*<br/>
旗標，指出沒有更新處理常式的控制項是否應該自動顯示為停用。

### <a name="remarks"></a>備註

若要更新個別的按鈕或窗格，請使用訊息對應中的 ON_UPDATE_COMMAND_UI 宏，適當地設定更新處理常式。 如需使用此宏的詳細資訊，請參閱[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 。

`OnUpdateCmdUI`應用程式處於閒置狀態時，架構會呼叫。 要更新的框架視窗必須是一個子視窗（至少間接）可見的框架視窗。 `OnUpdateCmdUI`是先進的可覆寫。

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar：： SetBarStyle

呼叫此函式可設定控制項列所需的**CBRS_** 樣式。

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
控制項列的所需樣式。 可以是下列一或多個：

- CBRS_ALIGN_TOP 允許控制列停駐在框架視窗的工作區頂端。

- CBRS_ALIGN_BOTTOM 允許控制列停駐在框架視窗的工作區底部。

- CBRS_ALIGN_LEFT 允許控制列停駐在框架視窗的工作區左邊。

- CBRS_ALIGN_RIGHT 允許控制列停駐在框架視窗工作區的右側。

- CBRS_ALIGN_ANY 允許控制列停駐在框架視窗的工作區的任何一邊。

- CBRS_BORDER_TOP 會在控制項列的上邊緣繪製框線（當它可見時）。

- CBRS_BORDER_BOTTOM 會在控制項列的下邊緣繪製框線，而這是可見的。

- CBRS_BORDER_LEFT 會在控制項列的左邊緣繪製框線，而這是可見的。

- CBRS_BORDER_RIGHT 會在控制項列的右邊緣繪製框線，使其可見。

- CBRS_FLOAT_MULTI 允許在單一迷你框架視窗中浮動多個控制列。

- CBRS_TOOLTIPS 會導致控制項列顯示工具提示。

- CBRS_FLYBY 會導致郵件內文與工具提示同時更新。

- CBRS_GRIPPER 會使移駐夾（類似于物件中的條紋上所使用的） `CReBar` 繪製到任何 `CControlBar` 衍生類別。

### <a name="remarks"></a>備註

不會影響**WS_** （視窗樣式）設定。

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar：： SetBorders

呼叫此函式可設定控制列框線的大小。

```cpp
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*cxLeft*<br/>
控制列左框線的寬度（以圖元為單位）。

*cyTop*<br/>
控制列上框線的高度（以圖元為單位）。

*cxRight*<br/>
控制列右框線的寬度（以圖元為單位）。

*cyBottom*<br/>
控制列下框線的高度（以圖元為單位）。

*lpRect*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標，其中包含控制列物件之每個框線的目前寬度（以圖元為單位）。

### <a name="example"></a>範例

下列程式碼範例會將控制列的上邊界和下框線設定為5圖元，左邊和右框線設為2圖元：

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar：： SetInPlaceOwner

變更控制列的就地擁有者。

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
`CWnd` 物件的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 類別](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 類別](../../mfc/reference/crebar-class.md)
