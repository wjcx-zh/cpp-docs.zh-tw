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
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372247"
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
|[連結::CLinkCtrl](#clinkctrl)|建構 `CLinkCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[連結::建立](#create)|創建連結控制項並將其附加到`CLinkCtrl`物件。|
|[連結:建立Ex](#createex)|創建具有擴展樣式的連結控制項並將其附加到`CLinkCtrl`物件。|
|[連結::取得理想高度](#getidealheight)|檢索鏈路控件的理想高度。|
|[連結::取得理想尺寸](#getidealsize)|根據連結的指定寬度計算當前連結控制件的連結文本的首選高度。|
|[連結:抓取項目](#getitem)|檢索連結控制項的狀態和屬性。|
|[連結::取得項目ID](#getitemid)|檢索連結控制項項的識別碼。|
|[連結::取得項目狀態](#getitemstate)|檢索連結控制項的狀態。|
|[連結::取得項目網址](#getitemurl)|檢索連結控制項表示的 URL。|
|[連結::HitTest](#hittest)|確定使用者是否按下指定的連結。|
|[連結:設定項目](#setitem)|設置連結控制項項的狀態和屬性。|
|[連結::設定項目ID](#setitemid)|設置連結控制項項的 ID。|
|[連結::設定項目狀態](#setitemstate)|設置連結控制項項的狀態。|
|[連結::設定項目網址](#setitemurl)|設置由連結控制項項表示的 URL。|

## <a name="remarks"></a>備註

連結控制件'提供了一種在視窗中嵌入超文字連結的便捷方法。 實際控件是一個視窗,用於呈現標記的文本,並在使用者單擊嵌入連結時啟動相應的應用程式。 一個控件中支援多個連結,並且可以通過基於零的索引訪問。

此控件(因此是`CLinkCtrl`類)僅適用於在 Windows XP 下運行的程式以及更高版本的程式。

有關詳細資訊,請參閱 Windows SDK 中的[SysLink 控制件](/windows/win32/Controls/syslink-overview)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>連結::CLinkCtrl

建構 `CLinkCtrl` 物件。

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>連結::建立

創建連結控制項並將其附加到`CLinkCtrl`物件。

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
指向包含要顯示的標記的向上文本的零端接字串的指標。 有關詳細資訊,請參閱[「SysLink 控件概述](/windows/win32/Controls/syslink-overview)」主題中的「標記和連結存取」部分。

*dwStyle*<br/>
指定連結控制件的樣式。 應用控件樣式的任意組合。 有關詳細資訊,請參閱中的`Windows SDK`[通用控制樣式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定連結控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定連結控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

分兩步`CLinkCtrl`構造物件。 首先調用構造函數,然後調用`Create`,這將創建連結控制件並將其附加`CLinkCtrl`到 物件。 如果要將延伸視窗樣式與控制項一起使用,請致電[CLinkCtrl::createEx](#createex)而不是`Create`。

方法的第`Create`二種形式被棄用。 使用指定*lpszLinkMarkup*參數的第一個窗體。

### <a name="example"></a>範例

以下代碼示例定義用於訪問兩個連結控制項的`m_Link1`兩`m_Link2`個變數,名為和,用於存取兩個連結控制項。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例基於另一個連結控制項的位置創建一個連結控制項。 應用程式啟動時,資源載入程式將創建第一個連結控制項。 當應用程式進入 OnInitDialog 方法時,您將創建相對於第一個連結控制項的位置的第二個連結控制項。 然後調整第二個連結控制項的大小,以適合它顯示的文本。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>連結:建立Ex

創建具有擴展樣式的連結控制項並將其附加到`CLinkCtrl`物件。

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
指向包含要顯示的標記的向上文本的零端接字串的指標。 有關詳細資訊,請參閱[「SysLink 控件概述](/windows/win32/Controls/syslink-overview)」主題中的「標記和連結存取」部分。

*dwExStyle*<br/>
指定連結控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定連結控制件的樣式。 應用控件樣式的任意組合。 有關詳細資訊,請參閱 Windows SDK 中的[通用控制元件樣式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定連結控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定連結控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定連結控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式常量。

方法的第`CreateEx`二種形式被棄用。 使用指定*lpszLinkMarkup*參數的第一個窗體。

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>連結::取得理想高度

檢索鏈路控件的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>傳回值

控件的理想高度(以像素為單位)。

### <a name="remarks"></a>備註

此成員函數實現 win32 消息[的行為LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight),如Windows SDK中所述。

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>連結::取得理想尺寸

根據連結的指定寬度計算當前連結控制件的連結文本的首選高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*cxMaxWidth*|[在]連結的最大寬度(以像素為單位)。|
|[出]\* *pSize*|指向 Windows [SIZE](/windows/win32/api/windef/ns-windef-size)結構的指標。 當此方法傳回時`SIZE`, 結構的*cy*成員包含*cxMaxWidth*指定的連結文字寬度的理想連結文本高度。 結構的*cx*成員包含實際需要的連結文本寬度。|

### <a name="return-value"></a>傳回值

連結文本的首選高度(以像素為單位)。 返回值與`SIZE`結構的*cy*成員的值相同。

### <a name="remarks"></a>備註

有關方法的範例,`GetIdealSize`請參閱[CLinkCtrl::::創建](#create)中的範例。

此方法發送[LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize)消息,這在 Windows SDK 中介紹。

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>連結:抓取項目

檢索連結控制項的狀態和屬性。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構的指標,用於接收項資訊。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem)的行為,如 Windows SDK 中所述。

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>連結::取得項目ID

檢索連結控制項項的識別碼。

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

*i 連結*<br/>
連結控項項的索引。

*斯特裡德*<br/>
包含指定項 ID 的[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件。

*szID*<br/>
包含指定的代碼的 null 中止字串。

*cchID*<br/>
*szID*緩衝區的大小(以字元表示)。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

> [!NOTE]
> 如果*szID 或 strID*的緩衝區小於 MAX_LINKID_TEXT,則此功能也會返回 FALSE。

### <a name="remarks"></a>備註

檢索特定連結控制項項的識別碼。 有關詳細資訊,請參閱 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>連結::取得項目狀態

檢索連結控制項的狀態。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>參數

*i 連結*<br/>
連結控項項的索引。

*pnState*<br/>
指定狀態項的值。

*狀態遮罩*<br/>
描述要獲取的狀態項的標誌的組合。 有關值清單,請參閱[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)`state`結構中 成員的說明。 允許的專案與 中允許的`state`專案 相同。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

檢索特定連結控制項項的指定狀態項的值。 有關詳細資訊,請參閱 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>連結::取得項目網址

檢索連結控制項表示的 URL。

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

*i 連結*<br/>
連結控項項的索引。

*斯特魯*<br/>
包含指定的名稱表示的網址的[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)物件

*szUrl*<br/>
包含指定的網址的 null 連接檔

*cchUrl*<br/>
*szURL*緩衝區的大小(以字元表示)。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

> [!NOTE]
> 如果*szUrl 或 strUrl*的緩衝區小於 MAX_LINKID_TEXT,則此功能也會返回 FALSE。

### <a name="remarks"></a>備註

檢索由指定的連結控制項表示的 URL。 有關詳細資訊,請參閱 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlhittest"></a><a name="hittest"></a>連結::HitTest

確定使用者是否按下指定的連結。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>參數

*菲蒂*<br/>
指向包含使用者`LHITTESTINFO`按一下的連結的任何資訊的結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[LM_HITTEST](/windows/win32/Controls/lm-hittest)的行為,如 Windows SDK 中所述。

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>連結:設定項目

設置連結控制項項的狀態和屬性。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)結構的指標,其中包含要設置的資訊。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為LM_SETITEM](/windows/win32/Controls/lm-setitem),如 Windows SDK 中所述。

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>連結::設定項目ID

檢索連結控制項項的識別碼。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>參數

*i 連結*<br/>
連結控項項的索引。

*szID*<br/>
包含指定的代碼的 null 中止字串。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

設置特定連結控制項項的 ID。 有關詳細資訊,請參閱 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>連結::設定項目狀態

檢索連結控制項的狀態。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>參數

*i 連結*<br/>
連結控項項的索引。

*pnState*<br/>
正在設定的指定狀態項的值。

*狀態遮罩*<br/>
描述要設置的狀態項的標誌的組合。 有關值清單,請參閱[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)`state`結構中 成員的說明。 允許的專案與 中允許的`state`專案 相同。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

設置特定連結控制項項的指定狀態項的值。 有關詳細資訊,請參閱 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>連結::設定項目網址

設置由連結控制項項表示的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>參數

*i 連結*<br/>
連結控項項的索引。

*szUrl*<br/>
包含指定的網址的 null 連接檔

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

設置由指定的連結控制項表示的 URL。 有關詳細資訊,請參閱 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
