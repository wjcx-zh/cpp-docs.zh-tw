---
title: CLinkCtrl 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 37d9e624c40f0d6aa7f3d3fa1ed3d97ffa478ee7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505708"
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
|[CLinkCtrl::Create](#create)|建立連結控制項, 並將它附加至`CLinkCtrl`物件。|
|[CLinkCtrl::CreateEx](#createex)|建立具有擴充樣式的連結控制項, 並將其附加`CLinkCtrl`至物件。|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|抓取連結控制項的理想高度。|
|[CLinkCtrl::GetIdealSize](#getidealsize)|根據連結的指定寬度, 計算目前連結控制項的連結文字慣用高度。|
|[CLinkCtrl::GetItem](#getitem)|抓取連結控制項專案的狀態和屬性。|
|[CLinkCtrl::GetItemID](#getitemid)|抓取連結控制項專案的識別碼。|
|[CLinkCtrl::GetItemState](#getitemstate)|抓取連結控制項專案的狀態。|
|[CLinkCtrl::GetItemUrl](#getitemurl)|抓取連結控制項專案所代表的 URL。|
|[CLinkCtrl::HitTest](#hittest)|判斷使用者是否已按一下指定的連結。|
|[CLinkCtrl::SetItem](#setitem)|設定連結控制項專案的狀態和屬性。|
|[CLinkCtrl::SetItemID](#setitemid)|設定連結控制項專案的識別碼。|
|[CLinkCtrl::SetItemState](#setitemstate)|設定連結控制項專案的狀態。|
|[CLinkCtrl::SetItemUrl](#setitemurl)|設定連結控制項專案所代表的 URL。|

## <a name="remarks"></a>備註

「連結控制項」提供一個便利的方式, 可在視窗中內嵌超文字連結。 實際的控制項是一種視窗, 可呈現已標記的文字, 並在使用者按一下內嵌連結時啟動適當的應用程式。 一個控制項內支援多個連結, 而且可以透過以零為起始的索引來存取。

這個控制項 (因此`CLinkCtrl`類別) 僅適用于在 Windows XP 和更新版本下執行的程式。

如需詳細資訊, 請參閱 Windows SDK 中的[SysLink 控制項](/windows/win32/Controls/syslink-overview)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="clinkctrl"></a>CLinkCtrl:: CLinkCtrl

建構 `CLinkCtrl` 物件。

```
CLinkCtrl();
```

##  <a name="create"></a>CLinkCtrl:: Create

建立連結控制項, 並將它附加至`CLinkCtrl`物件。

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
以零結束的字串指標, 其中包含已標示要顯示的文字。 如需詳細資訊, 請參閱[SysLink 控制項的總覽](/windows/win32/Controls/syslink-overview)主題中的「標記和連結存取」一節。

*dwStyle*<br/>
指定連結控制項的樣式。 套用控制項樣式的任何組合。 如需詳細資訊, 請`Windows SDK`參閱中的[通用控制項樣式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定連結控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pParentWnd*<br/>
指定連結控制項的父視窗。 不得為 Null。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用`CLinkCtrl`兩個步驟來建立物件。 首先, 呼叫此函式, 然後`Create`呼叫, 它會建立連結控制項並將其附加`CLinkCtrl`至物件。 如果您想要搭配控制項使用擴充的 windows 樣式, 請呼叫[CLinkCtrl:: CreateEx](#createex) , `Create`而不是。

第二種形式的`Create`方法已被取代。 使用指定*lpszLinkMarkup*參數的第一個表單。

### <a name="example"></a>範例

下列程式碼範例會定義兩個名`m_Link1`為`m_Link2`和的變數, 用來存取兩個連結控制項。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會根據另一個連結控制項的位置, 建立一個連結控制項。 當您的應用程式啟動時, 資源載入器會建立第一個連結控制項。 當您的應用程式進入 OnInitDialog 方法時, 您會建立相對於第一個連結控制項位置的第二個連結控制項。 然後, 調整第二個連結控制項的大小, 以符合它所顯示的文字。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>CLinkCtrl:: CreateEx

建立具有擴充樣式的連結控制項, 並將其附加`CLinkCtrl`至物件。

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
以零結束的字串指標, 其中包含已標示要顯示的文字。 如需詳細資訊, 請參閱[SysLink 控制項的總覽](/windows/win32/Controls/syslink-overview)主題中的「標記和連結存取」一節。

*dwExStyle*<br/>
指定連結控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定連結控制項的樣式。 套用控制項樣式的任何組合。 如需詳細資訊, 請參閱 Windows SDK 中的[通用控制項樣式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定連結控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pParentWnd*<br/>
指定連結控制項的父視窗。 不得為 Null。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用`CreateEx`而非[Create](#create)來套用擴充的 Windows 樣式常數。

第二種形式的`CreateEx`方法已被取代。 使用指定*lpszLinkMarkup*參數的第一個表單。

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

抓取連結控制項的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>傳回值

控制項的理想高度 (以圖元為單位)。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)的行為, 如 Windows SDK 中所述。

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

根據連結的指定寬度, 計算目前連結控制項的連結文字慣用高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*cxMaxWidth*|在連結的最大寬度 (以圖元為單位)。|
|脫銷\* *pSize*|Windows[大小](/windows/win32/api/windef/ns-windef-size)結構的指標。 當這個方法傳回時, `SIZE`結構的 cy 成員會包含*cxMaxWidth*所指定之連結文字寬度的理想連結文字高度。 結構的*cx*成員包含實際需要的連結文字寬度。|

### <a name="return-value"></a>傳回值

連結文字的慣用高度 (以圖元為單位)。 傳回值與`SIZE`結構的*cy*成員值相同。

### <a name="remarks"></a>備註

如需`GetIdealSize`方法的範例, 請參閱[CLinkCtrl:: Create](#create)中的範例。

這個方法會傳送[LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize)訊息, 如 Windows SDK 中所述。

##  <a name="getitem"></a>CLinkCtrl:: GetItem

抓取連結控制項專案的狀態和屬性。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>參數

*pItem*<br/>
接收專案資訊之[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem)的行為, 如 Windows SDK 中所述。

##  <a name="getitemid"></a>CLinkCtrl:: GetItemID

抓取連結控制項專案的識別碼。

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
連結控制項專案的索引。

*strID*<br/>
[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含指定專案的識別碼。

*szID*<br/>
以 null 終止的字串, 其中包含指定專案的識別碼。

*cchID*<br/>
*SzID*緩衝區的大小 (以字元為單位)。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

> [!NOTE]
>  如果*szID 或 strID*的緩衝區小於 MAX_LINKID_TEXT, 此函數也會傳回 FALSE。

### <a name="remarks"></a>備註

抓取特定連結控制項專案的識別碼。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="getitemstate"></a>CLinkCtrl:: GetItemState

抓取連結控制項專案的狀態。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項專案的索引。

*pnState*<br/>
指定之狀態專案的值。

*stateMask*<br/>
旗標的組合, 描述要取得的狀態專案。 如需值清單, 請參閱[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構中的`state`成員描述。 允許的專案與中`state`允許的專案完全相同。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

抓取特定連結控制項專案之指定狀態專案的值。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="getitemurl"></a>CLinkCtrl:: GetItemUrl

抓取連結控制項專案所代表的 URL。

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
連結控制項專案的索引。

*strUrl*<br/>
[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含指定專案所代表的 URL。

*szUrl*<br/>
以 null 終止的字串, 其中包含指定專案所代表的 URL

*cchUrl*<br/>
*SzURL*緩衝區的大小 (以字元為單位)。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

> [!NOTE]
>  如果*szUrl 或 strUrl*的緩衝區小於 MAX_LINKID_TEXT, 此函數也會傳回 FALSE。

### <a name="remarks"></a>備註

抓取指定的連結控制項專案所代表的 URL。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="hittest"></a>CLinkCtrl:: HitTest

判斷使用者是否已按一下指定的連結。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>參數

*phti*<br/>
`LHITTESTINFO`結構的指標, 其中包含使用者所按之連結的任何相關資訊。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [LM_HITTEST](/windows/win32/Controls/lm-hittest)的行為, 如 Windows SDK 中所述。

##  <a name="setitem"></a>CLinkCtrl:: SetItem

設定連結控制項專案的狀態和屬性。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構的指標, 其中包含要設定的資訊。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem)的行為, 如 Windows SDK 中所述。

##  <a name="setitemid"></a>CLinkCtrl:: SetItemID

抓取連結控制項專案的識別碼。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項專案的索引。

*szID*<br/>
以 null 終止的字串, 其中包含指定專案的識別碼。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

設定特定連結控制項專案的識別碼。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

##  <a name="setitemstate"></a>CLinkCtrl:: SetItemState

抓取連結控制項專案的狀態。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項專案的索引。

*pnState*<br/>
所設定之指定狀態專案的值。

*stateMask*<br/>
旗標的組合, 用來描述所設定的狀態專案。 如需值清單, 請參閱[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構中的`state`成員描述。 允許的專案與中`state`允許的專案完全相同。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

設定特定連結控制項專案之指定狀態專案的值。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

##  <a name="setitemurl"></a>CLinkCtrl:: SetItemUrl

設定連結控制項專案所代表的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>參數

*iLink*<br/>
連結控制項專案的索引。

*szUrl*<br/>
以 null 終止的字串, 其中包含指定專案所代表的 URL

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

設定指定的連結控制項專案所代表的 URL。 如需詳細資訊, 請參閱 Windows SDK 中的 Win32 message [LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
