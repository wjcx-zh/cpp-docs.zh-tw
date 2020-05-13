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
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363935"
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
|[CReBar:新增條](#addbar)|將帶添加到鋼筋。|
|[CReBar:建立](#create)|創建鋼筋控件並將其附加到`CReBar`物件。|
|[CReBar::取得 RebarCtrl](#getrebarctrl)|允許直接訪問基礎公共控件。|

## <a name="remarks"></a>備註

Rebar 物件可以包含各種子視窗 (通常是其他控制項)，包括編輯方塊、工具列和清單方塊。 Rebar 物件可以在指定的點陣圖上顯示其子視窗。 應用程式可以自動調整鋼筋的大小,或者使用者可以通過單擊或拖動其夾持欄手動調整鋼筋的大小。

![RebarMenu 範例](../../mfc/reference/media/vc4sc61.gif "RebarMenu 範例")

## <a name="rebar-control"></a>鋼筋控制

鋼筋對象的行為與工具欄對象類似。 鋼筋使用單擊和拖動機制調整其波段的大小。 Rebar 控制項可以包含一個或多個群組列，而且每個群組列都具有移駐夾列、點陣圖、文字標籤和子視窗中的任何組合。 不過，群組列不能包含一個以上的子視窗。

`CReBar`使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)類來提供其實現。 您可以通過[GetReBarCtrl](#getrebarctrl)訪問鋼筋控制項,以利用控制項的自定義選項。 有關鋼筋控件的詳細資訊,請參閱`CReBarCtrl`。 有關使用鋼筋控制件的詳細資訊,請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

> [!CAUTION]
> 鋼筋和鋼筋控制物件不支援 MFC 控制條停靠。 如果`CRebar::EnableDocking`調用,您的應用程式將斷言。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制列](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar:新增條

調用此成員函數以向鋼筋添加帶。

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
指向要插入鋼筋`CWnd`的子視窗的物件的指標。 引用的物件必須具有WS_CHILD。

*lpszText*<br/>
指向要顯示在鋼筋上的文本的字串的指標。 預設情況下為 NULL。 *lpszText*中包含的文本不是子視窗的一部分;因此,該文本中的文本不是子視窗的一部分。它在鋼筋本身。

*pbmp*<br/>
指向要顯示在鋼筋`CBitmap`背景上的對象的指標。 預設情況下為 NULL。

*dwStyle*<br/>
包含要應用於鋼筋的樣式的 DWORD。 有關波段`fStyle`樣式的完整清單,請參閱 Win32 結構[REBARBANDINFO 中的](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)函數說明。

*clrFore*<br/>
表示鋼筋前景顏色的 COLORREF 值。

*clrBack*<br/>
表示鋼筋背景顏色的 COLORREF 值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar:建立

調用此成員函數以創建鋼筋。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向其`CWnd`Windows 視窗是狀態列的父級的物件的指標。 通常,您的框架視窗。

*dwCtrl風格*<br/>
鋼筋控制樣式。 默認情況下,RBS_BANDBORDERS,它顯示窄線以分隔鋼筋控件中的相鄰波段。 有關樣式清單,請參閱 Windows SDK 中的[鋼筋控制樣式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
鋼筋視窗樣式。

*nID*<br/>
鋼筋的子窗口 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CReBar::addBar](#addbar)的範例。

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CReBar::取得 RebarCtrl

此成員函數允許直接訪問基礎公共控件。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

對[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)物件的引用。

### <a name="remarks"></a>備註

調用此成員函數以利用 Windows 鋼筋通用控件在自訂鋼筋時的功能。 呼叫`GetReBarCtrl`時,它將引用物件返回到該`CReBarCtrl`物件 ,以便可以使用任一組成員函數。

有關使用自訂`CReBarCtrl`鋼筋的詳細資訊,請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
