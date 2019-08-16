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
ms.openlocfilehash: 434232e8f99bf914b00379db53d4b4a37d24fe36
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502787"
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
|[CReBar::AddBar](#addbar)|將寬線加入至 Rebar。|
|[CReBar::Create](#create)|建立 Rebar 控制項並將其附加至`CReBar`物件。|
|[CReBar::GetReBarCtrl](#getrebarctrl)|允許直接存取基礎通用控制項。|

## <a name="remarks"></a>備註

Rebar 物件可以包含各種子視窗 (通常是其他控制項)，包括編輯方塊、工具列和清單方塊。 Rebar 物件可以在指定的點陣圖上顯示其子視窗。 您的應用程式可以自動調整 Rebar 的大小, 或者使用者可以按一下或拖曳其移駐夾列來手動調整 Rebar 大小。

![RebarMenu 的範例](../../mfc/reference/media/vc4sc61.gif "RebarMenu 的範例")

## <a name="rebar-control"></a>Rebar 控制項

Rebar 物件的行為類似工具列物件。 Rebar 會使用按一下和拖曳機制來調整其群組的大小。 Rebar 控制項可以包含一個或多個群組列，而且每個群組列都具有移駐夾列、點陣圖、文字標籤和子視窗中的任何組合。 不過，群組列不能包含一個以上的子視窗。

`CReBar`會使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)類別來提供其執行。 您可以透過[GetReBarCtrl](#getrebarctrl)存取 Rebar 控制項, 以利用控制項的自訂選項。 如需 Rebar 控制項的詳細資訊, `CReBarCtrl`請參閱。 如需有關使用 Rebar 控制項的詳細資訊, 請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

> [!CAUTION]
>  Rebar 和 Rebar 控制項物件不支援 MFC 控制列銜接。 如果`CRebar::EnableDocking`呼叫, 您的應用程式將會判斷提示。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>需求

**標頭:** afxext.h。h

##  <a name="addbar"></a>CReBar:: AddBar

呼叫這個成員函式, 將一個寬線加入至 Rebar。

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
`CWnd`物件的指標, 這是要插入 Rebar 中的子視窗。 參考的物件必須有 WS_CHILD。

*lpszText*<br/>
字串的指標, 其中包含要出現在 Rebar 上的文字。 預設值為 Null。 包含在*lpszText*中的文字不是子視窗的一部分;它是在 Rebar 本身。

*pbmp*<br/>
要在 Rebar 背景`CBitmap`上顯示之物件的指標。 預設值為 Null。

*dwStyle*<br/>
包含要套用至 Rebar 之樣式的 DWORD。 如需`fStyle`頻外樣式的完整清單, 請參閱 Win32 結構[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)中的函數描述。

*clrFore*<br/>
代表 Rebar 前景色彩的 COLORRE光圈值。

*clrBack*<br/>
代表 Rebar 背景色彩的 COLORRE光圈值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>CReBar:: Create

呼叫這個成員函式以建立 Rebar。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
`CWnd`物件的指標, 其 Windows 視窗為狀態列的父系。 通常是您的框架視窗。

*dwCtrlStyle*<br/>
Rebar 控制項樣式。 根據預設, RBS_BANDBORDERS 會顯示窄行, 以分隔 Rebar 控制項內的相鄰等區。 如需樣式清單, 請參閱 Windows SDK 中的[Rebar 控制項樣式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
Rebar 視窗樣式。

*nID*<br/>
Rebar 的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CReBar:: AddBar](#addbar)的範例。

##  <a name="getrebarctrl"></a>CReBar:: GetReBarCtrl

這個成員函式可讓您直接存取基礎通用控制項。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)物件的參考。

### <a name="remarks"></a>備註

呼叫這個成員函式可在自訂 Rebar 中利用 Windows Rebar 通用控制項的功能。 當您呼叫`GetReBarCtrl`時, 它會將參考物件傳回`CReBarCtrl`給物件, 讓您可以使用一組成員函式。

如需使用`CReBarCtrl`自訂 Rebar 的詳細資訊, 請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
