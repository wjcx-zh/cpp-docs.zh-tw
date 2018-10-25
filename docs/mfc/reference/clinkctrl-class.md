---
title: CLinkCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
dev_langs:
- C++
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b760cd1f548fc4d5dd2c4ce78cb0e16bca64474
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070266"
---
# <a name="clinkctrl-class"></a>CLinkCtrl 類別

提供 Windows 通用 SysLink 控制項的功能。

## <a name="syntax"></a>語法

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|建構 `CLinkCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|建立連結控制項，並將它附加至`CLinkCtrl`物件。|
|[CLinkCtrl::CreateEx](#createex)|使用延伸樣式中建立連結控制項，並將它附加至`CLinkCtrl`物件。|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|擷取連結控制項的理想高度。|
|[CLinkCtrl::GetIdealSize](#getidealsize)|計算目前的連結控制，根據指定的寬度，連結的連結文字的慣用的高度。|
|[CLinkCtrl::GetItem](#getitem)|擷取狀態和連結控制項項目的屬性。|
|[CLinkCtrl::GetItemID](#getitemid)|擷取連結控制項項目的識別碼。|
|[CLinkCtrl::GetItemState](#getitemstate)|擷取連結控制項項目的狀態。|
|[CLinkCtrl::GetItemUrl](#getitemurl)|擷取連結控制項項目所代表的 URL。|
|[CLinkCtrl::HitTest](#hittest)|判斷使用者是否按下指定的連結。|
|[CLinkCtrl::SetItem](#setitem)|設定的狀態和屬性的連結控制項項目。|
|[CLinkCtrl::SetItemID](#setitemid)|設定連結控制項項目的識別碼。|
|[CLinkCtrl::SetItemState](#setitemstate)|設定連結控制項項目的狀態。|
|[CLinkCtrl::SetItemUrl](#setitemurl)|設定連結控制項目所代表的 URL。|

## <a name="remarks"></a>備註

[連結控制] 提供便利的方式，在視窗中內嵌超文字連結。 實際的控制項是一個視窗，呈現標記文字，並啟動適當的應用程式，當使用者按一下內嵌的連結。 多個連結其中一個控制項內支援，並可以存取的以零為起始的索引。

這個控制項 (並因此`CLinkCtrl`類別) 僅適用於在 Windows XP 及更新版本執行的程式。

如需詳細資訊，請參閱 < [SysLink 控制項](/windows/desktop/Controls/syslink-overview)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

建構 `CLinkCtrl` 物件。

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

建立連結控制項，並將它附加至`CLinkCtrl`物件。

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*lpszLinkMarkup*<br/>
要顯示的文字包含標示的零結尾字串的指標。 如需詳細資訊，請參閱主題中的 「 標記和連結存取 」 一節[SysLink 控制項概觀](/windows/desktop/Controls/syslink-overview)。

*cheaderctrl:: Create*<br/>
指定連結控制項的樣式。 適用於任何控制項樣式的組合。 請參閱[常見的控制項樣式](/windows/desktop/Controls/common-control-styles)在`Windows SDK`如需詳細資訊。

*rect*<br/>
指定連結控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。

*pParentWnd*<br/>
指定連結控制項的父視窗。 它必須不是 NULL。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

您建構`CLinkCtrl`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，這會建立連結的控制，並將它附加至`CLinkCtrl`物件。 如果您想要使用擴充的 windows 樣式和控制項，呼叫[CLinkCtrl::CreateEx](#createex)而不是`Create`。

第二個形式`Create`方法已被取代。 使用指定的第一個表單*lpszLinkMarkup*參數。

### <a name="example"></a>範例

下列程式碼範例會定義兩個變數，名為`m_Link1`和`m_Link2`，用來存取兩個連結控制項。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會建立一個連結控制，根據另一個連結控制項的位置。 資源載入器應用程式啟動時，會建立第一個連結控制項。 當您的應用程式進入 OnInitDialog 方法時，您會建立第二個連結控制項的第一個連結控制項的相對位置。 然後，您要調整第二個連結控制項以符合它所顯示的文字。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

使用延伸樣式中建立連結控制項，並將它附加至`CLinkCtrl`物件。

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>參數

*lpszLinkMarkup*<br/>
要顯示的文字包含標示的零結尾字串的指標。 如需詳細資訊，請參閱主題中的 「 標記和連結存取 」 一節[SysLink 控制項概觀](/windows/desktop/Controls/syslink-overview)。

*dwExStyle*<br/>
指定連結控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*cheaderctrl:: Create*<br/>
指定連結控制項的樣式。 適用於任何控制項樣式的組合。 如需詳細資訊，請參閱 <<c0> [ 常見的控制項樣式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。

*rect*<br/>
指定連結控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。

*pParentWnd*<br/>
指定連結控制項的父視窗。 它必須不是 NULL。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式常數。

第二個形式`CreateEx`方法已被取代。 使用指定的第一個表單*lpszLinkMarkup*參數。

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

擷取連結控制項的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>傳回值

控制項，像素為單位的理想高度。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight)、 Windows SDK 中所述。

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

計算目前的連結控制，根據指定的寬度，連結的連結文字的慣用的高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*cxMaxWidth*|[in]連結，像素為單位的最大寬度。|
|[out]\* *pSize*|Windows 的指標[大小](https://msdn.microsoft.com/library/windows/desktop/dd145106)結構。 當這個方法傳回時， *cy*隸屬`SIZE`結構中包含所指定的連結文字寬度的理想的連結文字高度*cxMaxWidth*。 *Cx*結構成員會包含實際所需的連結文字寬度。|

### <a name="return-value"></a>傳回值

連結文字、 像素為單位的慣用的高度。 傳回值是相同的值*cy*隸屬`SIZE`結構。

### <a name="remarks"></a>備註

如需`GetIdealSize`方法，請參閱中的範例[CLinkCtrl::Create](#create)。

這個方法會傳送[LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize)訊息，Windows SDK 中所述。

##  <a name="getitem"></a>  CLinkCtrl::GetItem

擷取狀態和連結控制項項目的屬性。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>參數

*pItem*<br/>
指標[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)接收項目資訊的結構。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[LM_GETITEM](/windows/desktop/Controls/lm-getitem)、 Windows SDK 中所述。

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

擷取連結控制項項目的識別碼。

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*strID*<br/>
A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含指定項目的識別碼。

*szID*<br/>
以 null 結束的字串，包含指定項目的識別碼。

*cchID*<br/>
以字元為單位的大小*szID*緩衝區。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

> [!NOTE]
>  此函式也會傳回 FALSE，如果緩衝區*szID 或 strID*小於 MAX_LINKID_TEXT。

### <a name="remarks"></a>備註

擷取特定連結控制項項目的識別碼。 如需詳細資訊，請參閱 Win32 訊息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

擷取連結控制項項目的狀態。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*pnState*<br/>
指定的狀態項目的值。

*stateMask*<br/>
描述要取得的狀態項目旗標的組合。 如需值的清單，請參閱說明`state`中的成員[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)結構。 允許的項目是相同中允許`state`。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

擷取的特定連結控制項項目指定的狀態項目的值。 如需詳細資訊，請參閱 Win32 訊息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

擷取連結控制項項目所代表的 URL。

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*strUrl*<br/>
A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含指定的項目所代表的 URL

*szUrl*<br/>
Null 終止的字串，包含指定的項目所代表的 URL

*cchUrl*<br/>
以字元為單位的大小*szURL*緩衝區。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

> [!NOTE]
>  此函式也會傳回 FALSE，如果緩衝區*szUrl 或 strUrl*小於 MAX_LINKID_TEXT。

### <a name="remarks"></a>備註

擷取指定的連結控制項項目所代表的 URL。 如需詳細資訊，請參閱 Win32 訊息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="hittest"></a>  CLinkCtrl::HitTest

判斷使用者是否按指定的連結。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>參數

*phti*<br/>
指標`LHITTESTINFO`結構，其中包含連結的相關使用者已按下任何資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[LM_HITTEST](/windows/desktop/Controls/lm-hittest)、 Windows SDK 中所述。

##  <a name="setitem"></a>  CLinkCtrl::SetItem

設定的狀態和屬性的連結控制項項目。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指標[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)結構，其中包含要設定的資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[LM_SETITEM](/windows/desktop/Controls/lm-setitem)、 Windows SDK 中所述。

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

擷取連結控制項項目的識別碼。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*szID*<br/>
以 null 結束的字串，包含指定項目的識別碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

設定特定連結控制項項目的識別碼。 如需詳細資訊，請參閱 Win32 訊息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

擷取連結控制項項目的狀態。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*pnState*<br/>
設定指定的狀態項目的值。

*stateMask*<br/>
描述狀態項目的所設定的旗標的組合。 如需值的清單，請參閱說明`state`中的成員[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)結構。 允許的項目是相同中允許`state`。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

設定的特定連結控制項項目指定的狀態項目的值。 如需詳細資訊，請參閱 Win32 訊息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

設定連結控制項目所代表的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項項目的索引。

*szUrl*<br/>
Null 終止的字串，包含指定的項目所代表的 URL

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

設定指定的連結控制項項目所代表的 URL。 如需詳細資訊，請參閱 Win32 訊息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
