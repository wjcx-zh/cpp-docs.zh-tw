---
title: CReBar 類別
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: 5a87f70816e9342c7aa203a53d13699659cebb28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372349"
---
# <a name="crebar-class"></a>CReBar 類別

提供 Rebar 控制項配置、持續性和狀態資訊的控制列。

## <a name="syntax"></a>語法

```
class CReBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|將 rebar 群組列。|
|[CReBar::Create](#create)|建立 rebar 控制項，並將它附加至`CReBar`物件。|
|[CReBar::GetReBarCtrl](#getrebarctrl)|允許直接存取基礎的通用控制項。|

## <a name="remarks"></a>備註

Rebar 物件可以包含各種子視窗 (通常是其他控制項)，包括編輯方塊、工具列和清單方塊。 Rebar 物件可以在指定的點陣圖上顯示其子視窗。 您的應用程式可以自動調整 rebar，或使用者可以手動調整 rebar 藉由按一下或拖曳它的移駐夾列。

![Rebarmenu 範例](../../mfc/reference/media/vc4sc61.gif "rebarmenu 範例")

## <a name="rebar-control"></a>Rebar 控制項

Rebar 物件的操作方式類似工具列物件。 Rebar 會使用按一下並拖曳機制，來調整其群組列的大小。 Rebar 控制項可以包含一個或多個群組列，而且每個群組列都具有移駐夾列、點陣圖、文字標籤和子視窗中的任何組合。 不過，群組列不能包含一個以上的子視窗。

`CReBar` 會使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)類別，以提供它的實作。 您可以存取透過 rebar 控制項[GetReBarCtrl](#getrebarctrl)利用控制項的自訂選項。 如需 rebar 控制項的詳細資訊，請參閱`CReBarCtrl`。 如需使用 rebar 控制項的詳細資訊，請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

> [!CAUTION]
>  Rebar 和 rebar 控制項物件不支援 MFC 控制列的停駐。 如果`CRebar::EnableDocking`呼叫時，您的應用程式會判斷提示。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="addbar"></a>  CReBar::AddBar

呼叫此成員函式，將 rebar 群組列。

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>參數

*pBar*<br/>
指標`CWnd`是要插入至 rebar 的子視窗的物件。 參考的物件必須有 WS_CHILD。

*lpszText*<br/>
字串，包含要顯示 rebar 上的文字指標。 預設為 NULL。 中包含的文字*lpszText*不屬於子視窗中，它位於 rebar 本身。

*pbmp*<br/>
指標`CBitmap`rebar 背景上顯示的物件。 預設為 NULL。

*dwStyle*<br/>
DWORD 包含樣式来套用至 rebar。 請參閱`fStyle`函數在 Win32 結構描述[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)的寬線樣式的完整清單。

*clrFore*<br/>
COLORREF 值，表示 rebar 的前景色彩。

*clrBack*<br/>
COLORREF 值，表示 rebar 的背景色彩。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>  CReBar::Create

呼叫此成員函式建立 rebar。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指標`CWnd`其 Windows 視窗是 [狀態] 列的父代的物件。 通常框架視窗。

*dwCtrlStyle*<br/>
Rebar 控制項樣式。 根據預設，RBS_BANDBORDERS，它會顯示有限的幾行，以分隔相鄰的群組列的 rebar 控制項中。 請參閱[Rebar 控制項的樣式](/windows/desktop/Controls/rebar-control-styles)Windows SDK，如需樣式的清單中。

*dwStyle*<br/>
Rebar 的視窗樣式。

*nID*<br/>
Rebar 的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CReBar::AddBar](#addbar)。

##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl

此成員函式允許直接存取基礎的通用控制項。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

參考[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)物件。

### <a name="remarks"></a>備註

呼叫此成員函式，以善用 Windows rebar 通用控制項，自訂您 rebar 的功能。 當您呼叫`GetReBarCtrl`，它會傳回參考物件，以`CReBarCtrl`物件，以便您可以使用任一組成員函式。

如需使用詳細資訊`CReBarCtrl`若要自訂您 rebar，請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
