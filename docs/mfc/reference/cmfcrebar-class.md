---
title: CMFCReBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs:
- C++
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3b91d0397b1eec53988e7acd5a5b7dce61db4ec
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059879"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 類別

A`CMFCReBar`物件是提供版面配置、 持續性和 rebar 控制項的狀態資訊的控制列。
如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。
## <a name="syntax"></a>語法

```
class CMFCReBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|將 rebar 群組列。|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(覆寫[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CMFCReBar::CanFloat](#canfloat)|(覆寫[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|
|[CMFCReBar::Create](#create)|建立 rebar 控制項，並將它附加至`CMFCReBar`物件。|
|[CMFCReBar::EnableDocking](#enabledocking)|(覆寫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|可直接存取基礎[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)通用控制項。|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(覆寫[cpane:: Onshowcontrolbarmenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(覆寫[CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)。)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(覆寫[CBasePane::OnUpdateCmdUI](cbasepane-class.md)。)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(覆寫[CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)。)|

## <a name="remarks"></a>備註

A`CMFCReBar`物件可以包含各種不同的子視窗。 這包括編輯方塊、 工具列和清單方塊。 您也可以以程式設計的方式，調整 rebar 或使用者可以手動拖曳調整大小 rebar 的移駐夾列。 您也可以設定 rebar 物件的背景，您選擇的點陣圖。

Rebar 物件的操作方式類似工具列物件。 Rebar 控制項可以包含一或多個群組列，而且每個群組列可以包含移駐夾列、 點陣圖、 文字標籤和子視窗。

## <a name="example"></a>範例

下例示範如何在 `CMFCReBar` 類別中使用各種方法。 此範例示範如何建立 rebar 控制項並加入它的頻外。 此群組列做為內部的工具列。 此程式碼片段是一部分[Rebar 測試範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxRebar.h

##  <a name="addbar"></a>  CMFCReBar::AddBar

將 rebar 群組列。

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
[in、 out]要插入至 rebar 的子視窗指標。 參考的物件必須有**WS_CHILD**視窗樣式。

*pszText*<br/>
[in]指定要顯示 rebar 上的文字。 文字不是子視窗的一部分。 相反地，它會顯示 rebar 本身。

*pbmp*<br/>
[in、 out]指定要顯示 rebar 背景點陣圖。

*cheaderctrl:: Create*<br/>
[in]包含要套用至群組列的樣式。 頻外樣式的完整清單，請參閱的描述`fStyle`中[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) Windows SDK 文件中的結構。

*clrFore*<br/>
[in]表示 rebar 的前景色彩。

*clrBack*<br/>
[in]表示 rebar 的背景色彩。

### <a name="return-value"></a>傳回值

如果群組列已成功新增至 rebar;，則為 TRUE。否則為 FALSE。

##  <a name="create"></a>  CMFCReBar::Create

建立 rebar 控制項，並將它附加至[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)物件。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
[in、 out]此 rebar 控制項的父視窗指標。

*dwCtrlStyle*<br/>
[in]指定 rebar 控制項的樣式。 預設樣式值是**RBS_BANDBORDERS**，它會顯示縮小範圍，來分隔相鄰的群組列的 rebar 控制項上的線條。 如需有效的樣式清單，請參閱 < [Rebar 控制項的樣式](/windows/desktop/Controls/rebar-control-styles)Windows SDK 文件。

*cheaderctrl:: Create*<br/>
[in]Rebar 控制項的視窗樣式。 如需有效的樣式清單，請參閱 <<c0> [ 的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
[in]Rebar 的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果已成功; 建立 rebar，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl

可直接存取`CReBarCtrl`為基礎的通用控制項`CMFCReBar`物件。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>傳回值

參考基礎`CReBarCtrl`物件。

### <a name="remarks"></a>備註

呼叫這個方法，以善用 Windows rebar 通用控制項功能自訂您 rebar 時。

##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[in]*bStretch*<br/>
[in]*bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="canfloat"></a>  CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>參數

[in]*dwDockStyle*<br/>

### <a name="remarks"></a>備註

##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>參數

[in]*CPoint*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>參數

[in]*點*<br/>
[in]*pTI*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

[in]*pTarget*<br/>
[in]*bDisableIfNoHndler*<br/>

### <a name="remarks"></a>備註

##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>參數

[in]*dwAlignment*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl 類別](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane 類別](../../mfc/reference/cpane-class.md)
