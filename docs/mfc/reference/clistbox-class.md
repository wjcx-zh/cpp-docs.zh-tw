---
title: CListBox 類別
description: MFC CListBox 類及其成員函數的說明。
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 171038ebaaed815aa687c200fe3210bde8000be3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753587"
---
# <a name="clistbox-class"></a>CListBox 類別

提供 Windows 清單方塊的功能。

## <a name="syntax"></a>語法

```
class CListBox : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CListBox:CListBox](#clistbox)|建構 `CListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CListBox::AddString](#addstring)|將字串加入清單盒。|
|[CListBox::查理斯](#chartoitem)|覆蓋以為沒有字串的所有者繪製列表框提供自定義WM_CHAR處理。|
|[CListBox:比較項目](#compareitem)|由框架調用以確定新專案在排序的擁有者繪製清單框中的位置。|
|[CListBox:建立](#create)|創建 Windows 清單框並將其`CListBox`附加到 物件。|
|[CListBox::Delete專案](#deleteitem)|當使用者從擁有者繪製清單框中刪除專案時,由框架調用。|
|[CListBox::DeleteString](#deletestring)|從清單框中移除字串。|
|[CListBox::Dir](#dir)|將檔案名、驅動器或兩者從當前目錄添加到清單框。|
|[CListBox::D原始專案](#drawitem)|當所有者繪製清單框的可視方面發生更改時,由框架調用。|
|[CListBox::尋找字串](#findstring)|在清單框中搜尋字串。|
|[CListBox::尋找字串精確](#findstringexact)|尋找與指定字串匹配的第一個清單框字串。|
|[CListBox:取得錨定索引](#getanchorindex)|在清單框中檢索當前錨點項的零基索引。|
|[CListBox:抓取關懷索引](#getcaretindex)|確定在多選擇清單框中具有焦點矩形的項的索引。|
|[CListBox:取得計數](#getcount)|傳回清單框中的字串數。|
|[CListBox:取得CurSel](#getcursel)|在清單框中返回當前選取字串的零基索引。|
|[CListBox:抓取水平範圍](#gethorizontalextent)|返回清單框可以水平滾動的寬度。|
|[CListBox:抓取項目資料](#getitemdata)|返回與列表框項關聯的值。|
|[CListBox:抓取項目資料Ptr](#getitemdataptr)|傳回指向清單框項目的指標。|
|[CListBox:抓取專案高度](#getitemheight)|確定清單框中專案的高度。|
|[CListBox:取得項目已重新完成](#getitemrect)|傳回清單盒項目目前顯示的邊界矩形。|
|[CListBox:抓取清單框資訊](#getlistboxinfo)|檢索每列的項目數。|
|[CListBox:抓取本地化](#getlocale)|檢索清單框的區域設置識別碼。|
|[CListBox:GetSel](#getsel)|傳回清單盒項目的選擇狀態。|
|[CListBox:取得塞爾計數](#getselcount)|傳回在多選清單框中目前選擇的字串數。|
|[CListBox:取得塞爾項目](#getselitems)|返回當前在清單框中選擇的字串的索引。|
|[CListBox:抓取文字](#gettext)|將清單框項目複製到緩衝區中。|
|[CListBox:抓取文字](#gettextlen)|返回清單框項的長度(以位元組為單位)。|
|[CListBox:取得熱門索引](#gettopindex)|返回清單框中第一個可見字串的索引。|
|[CListBox::在內存儲](#initstorage)|預分配清單框項目和字串的記憶體區塊。|
|[CListBox::InsertString](#insertstring)|在清單框中在特定位置插入字串。|
|[CListBox:專案從點](#itemfrompoint)|返回離點最近的清單框項的索引。|
|[CListBox:測量專案](#measureitem)|建立擁有者繪製清單框以確定列表框維度時,由框架調用。|
|[CListBox:重置內容](#resetcontent)|清除清單框中的所有項目。|
|[CListBox:選擇字串](#selectstring)|在單選清單框中搜尋並選擇字串。|
|[CListBox::塞爾項目範圍](#selitemrange)|在多選清單框中選擇或取消選擇一系列字串。|
|[CListBox::設置錨定索引](#setanchorindex)|在多選清單框中設置錨點以開始擴展選擇。|
|[CListBox::設置關懷索引](#setcaretindex)|在多選清單框中將焦點矩形設置到指定索引處的項。|
|[清單盒::設定欄寬](#setcolumnwidth)|設定多列清單框的列寬度。|
|[CListBox::設定CurSel](#setcursel)|選擇清單框字串。|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|設置清單框可以水平滾動的圖元寬度。|
|[CListBox:設定項目資料](#setitemdata)|設置與列表框項關聯的值。|
|[CListBox::設定項目資料Ptr](#setitemdataptr)|設定指向清單框項目的指標。|
|[CListBox:設定專案高度](#setitemheight)|在清單框中設置專案的高度。|
|[CListBox::設定當地語系化](#setlocale)|設定清單框的區域設定識別碼。|
|[CListBox::設定塞爾](#setsel)|在多選清單框中選擇或取消選擇清單框項。|
|[CListBox::設定標籤](#settabstops)|在清單框中設置製表位。|
|[CListBox::設定頂索引](#settopindex)|設置清單框中第一個可見字串的零基索引。|
|[CListBox::Vkeyto專案](#vkeytoitem)|覆蓋以提供具有LBS_WANTKEYBOARDINPUT樣式集的清單框的自定義WM_KEYDOWN處理。|

## <a name="remarks"></a>備註

清單框顯示使用者可以查看和選擇的專案清單(如檔名)。

在單選清單框中,使用者只能選擇一個專案。 在多選清單框中,可以選擇一系列專案。 當使用者選擇專案時,它將突出顯示,清單框向父視窗發送通知消息。

可以從對話框範本或直接在代碼中創建清單框。 要直接創建它,請建構`CListBox`物件,然後調用[Create](#create)成員函數以創建 Windows 列表框控制項`CListBox`並將其附加到 物件。 要在對話框範本中使用清單框,請聲明對話方塊類中的清單框變數,然後在對話方塊類`DDX_Control``DoDataExchange`的函數中使用將成員變數連接到控制項。 (當您向對話方塊類添加控制項變數時,會自動為您完成此操作。

構造可以是派生自`CListBox`的類中的一個步驟。 為派生類編寫一個構造函數,並從`Create`構造函數內部調用。

如果要處理清單框發送到其父項的 Windows 通知消息(通常是從[CDialog](../../mfc/reference/cdialog-class.md)派生的類),則為每個消息向父類添加消息映射條目和消息處理程式成員函數。

每個訊息對應項目以以下的檔案:

`ON_Notification( id, memberFxn )`

其中`id`指定發送通知的清單框控制項的子視窗 ID,以及`memberFxn`您為處理通知而編寫的父成員函數的名稱。

父函數原型如下所示:

`afx_msg void memberFxn( );`

以下是潛在訊息對應項目的清單,以及將它們傳送到父項目的說明:

- ON_LBN_DBLCLK 使用者按兩下清單框中的字串。 只有具有[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單框才會發送此通知訊息。

- ON_LBN_ERRSPACE 清單框無法分配足夠的記憶體以滿足請求。

- ON_LBN_KILLFOCUS 清單框正在失去輸入焦點。

- ON_LBN_SELCANCEL取消當前清單框選擇。 僅當清單框具有LBS_NOTIFY樣式時,才會發送此消息。

- ON_LBN_SELCHANGE 清單框中的選擇已更改。 如果[CListBox:setCurSel](#setcursel)成員函數更改了所選內容,則不會發送此通知。 此通知僅適用於具有LBS_NOTIFY樣式的清單框。 當使用者按箭頭鍵時,都會為多選擇清單框發送LBN_SELCHANGE通知消息,即使所選內容沒有變化也是如此。

- ON_LBN_SETFOCUS 清單框正在接收輸入焦點。

- ON_WM_CHARTOITEM沒有字串的所有者繪製列表框會收到WM_CHAR消息。

- ON_WM_VKEYTOITEM具有LBS_WANTKEYBOARDINPUT樣式的清單框接收WM_KEYDOWN消息。

如果在對話框中創建`CListBox`物件(通過對話框資源),則當使用者關閉對話方塊`CListBox`時, 該物件將自動銷毀。

如果在視窗中創建`CListBox`物件,則可能需要銷毀`CListBox`該 物件。 如果在堆疊上`CListBox`創建物件,則會自動銷毀該物件。 如果使用新函數在`CListBox`堆上創建物件,則必須調**new**用 物件**上的 delete**以在使用者關閉父視窗時銷毀該物件。

如果在`CListBox`物件中分配任何記憶體,請重寫`CListBox`析構函數以釋放分配。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::新增字串

將字串加入清單盒。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
指向要新增的 null 終止字串。

### <a name="return-value"></a>傳回值

清單框中字串的零基索引。 如果發生錯誤,返回值將LB_ERR;如果沒有足夠的空間來存儲新字串,則返回值LB_ERRSPACE。

### <a name="remarks"></a>備註

如果未使用[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式創建清單框,則字串將添加到清單的末尾。 否則,字串將插入到清單中,並排序列表。 如果清單框使用LBS_SORT樣式創建,但未創建[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式,則框架將按對成員函`CompareItem`數的一個或多個調用對清單進行排序。

使用[InsertString](#insertstring)將字串插入到清單框中的特定位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::查理斯

當清單框的父視窗從清單框中接收WM_CHARTOITEM消息時,由框架調用。

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>參數

*N 鍵*<br/>
用戶鍵入的字元的 ANSI 代碼。

*nIndex*<br/>
清單框的目前位置。

### <a name="return-value"></a>傳回值

傳回 - 1 或 - 2,無需進一步操作或非負數來指定清單框項的索引,以執行擊鍵的預設操作。 預設實現返回 - 1。

### <a name="remarks"></a>備註

WM_CHARTOITEM消息在收到WM_CHAR消息時由清單框發送,但僅當清單框滿足以下所有條件時::

- 是擁有者繪製清單框。

- 沒有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式集。

- 至少有一個專案。

您絕不應自行調用此功能。 重寫此函數以提供您自己的鍵盤消息的自定義處理。

在重寫中,必須返回一個值,告訴框架您執行了哪些操作。 傳回值 - 1 或 - 2 表示您處理了選擇項的所有方面,並且不需要清單框執行進一步操作。 在傳回 - 1 或 - 2 之前,您可以設定選擇或行動 caret 或兩者。 要設定選擇,請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 要移動 caret,請使用[SetCaretIndex](#setcaretindex)。

返回值 0 或更高指定清單框中項的索引,並指示列表框應對給定項執行擊鍵的預設操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox:CListBox

建構 `CListBox` 物件。

```
CListBox();
```

### <a name="remarks"></a>備註

分兩步`CListBox`構造物件。 首先呼叫建構函數`ClistBox`,然後呼`Create`叫 ,該呼叫將初始化 Windows 清單框並將`CListBox`其附加到 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox:比較項目

由框架調用以確定新專案在排序的擁有者繪製清單框中的相對位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>參數

*lp比較項目結構*<br/>
指向結構的長`COMPAREITEMSTRUCT`指標。

### <a name="return-value"></a>傳回值

指示[比較專案結構](/windows/win32/api/winuser/ns-winuser-compareitemstruct)中描述的兩個項目的相對位置。 它可能是以下任何值:

|值|意義|
|-----------|-------------|
|-1|專案 1 在專案 2 之前排序。|
|0|專案 1 和專案 2 排序相同。|
|1|專案 1 在專案 2 之後排序。|

有關`COMPAREITEMSTRUCT`結構的說明,請參閱[CWnd:On 比較專案](../../mfc/reference/cwnd-class.md#oncompareitem)。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 如果使用LBS_SORT樣式創建擁有者繪製列表框,則必須重寫此成員函數,以説明框架對添加到清單框的新項進行排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox:建立

創建 Windows 清單框並將其`CListBox`附加到 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定清單框的樣式。 將[清單框樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)的任意組合應用於該框。

*矩形*<br/>
指定清單框大小和位置。 可以是`CRect`對`RECT`象或結構。

*pparentwnd*<br/>
指定清單框的父視窗(通常是`CDialog`物件)。 它不得為 NULL。

*nID*<br/>
指定清單框的控制 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩步`CListBox`構造物件。 首先調用構造函數,然後調用`Create`,該調用將初始化 Windows 列表框並將`CListBox`其附加到 物件。

執行`Create`時,Windows[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)會將WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息發送到清單框[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)[WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)控制項。

默認情況下,這些消息`CWnd`由基類中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)[OnCreate](../../mfc/reference/cwnd-class.md#oncreate)[OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)成員函數處理。 要擴展預設消息處理,從`CListBox`派生類,向新類添加消息映射,並重寫前面的消息處理程式成員函數。 例如`OnCreate`,重寫以執行新類所需的初始化。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)應用於清單框控制元件。

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL捲動動

- WS_HSCROLL 新增水平捲動條

- WS_GROUP元件

- WS_TABSTOP 允許選項卡到此控制項

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::Delete專案

當使用者從擁有者繪製`CListBox`物件中刪除專案或銷毀清單框時,由框架調用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>參數

*lp 刪除項目已移除*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)結構的長指標,其中包含有關已刪除項的資訊。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 根據需要重寫此函數以重繪擁有者繪製清單框。

有關`DELETEITEMSTRUCT`結構的說明,請參閱[CWnd:OnDeleteItem。](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

從清單框中刪除位置*nIndex*中的項目。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要刪除的字串的零基索引。

### <a name="return-value"></a>傳回值

清單中剩餘字串的計數。 如果*nIndex*指定的索引大於清單中的項數,則返回值LB_ERR。

### <a name="remarks"></a>備註

*nIndex*之後的所有項目現在向下移動一個位置。 例如,如果清單框包含兩個項目,刪除第一個項將導致其餘項現在位於第一個位置。 *nIndex*#0 表示第一個位置中的項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::Dir

將檔案名、驅動器或兩者的清單添加到清單框。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>參數

*attr*<br/>
可以是`CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)中描述的**Enrt**的任意組合,也可以是以下值的任意組合:

|值|意義|
|-----------|-------------|
|0x0000|檔可以從讀取或寫入。|
|0x0001|檔可以從讀取,但不能寫入。|
|0x0002|檔案是隱藏的,不會顯示在目錄清單中。|
|0x0004|檔是系統檔。|
|0x0010|*lpszWildCard*指定的名稱指定一個目錄。|
|0x0020|檔已存檔。|
|0x4000|包括與*lpszWildCard*指定的名稱匹配的所有驅動器。|
|0x8000|獨佔標誌。 如果設置了獨佔標誌,則僅列出指定類型的檔。 否則,除了「正常」檔外,還列出指定類型的檔。|

*lpsz通配子*<br/>
指向檔規範字串。 字串可以包含通配符(例如 ,*.\*

### <a name="return-value"></a>傳回值

添加到清單中的姓氏的零基索引。 如果發生錯誤,返回值將LB_ERR;如果沒有足夠的空間來存儲新字串,則返回值LB_ERRSPACE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::D原始專案

當所有者繪製清單框的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

結構`itemAction``itemState`和`DRAWITEMSTRUCT`成員定義要執行的繪圖操作。

默認情況下,此成員函數不執行任何操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CListBox`。 應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

有關`DRAWITEMSTRUCT`結構的說明,請參閱[CWnd:OnDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::尋找字串

在包含指定前置的清單框中尋找第一個字串,而不更改清單框選擇。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>參數

*N 開始後*<br/>
包含要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nStartAfter*指定的項。 如果*nStartAfter*為 -1,則從一開始就搜索整個列表框。

*lpszItem*<br/>
包含要搜尋的前置字串。 搜尋是獨立於大小寫,因此此字串可能包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

匹配項的零基索引,或LB_ERR搜索不成功時。

### <a name="remarks"></a>備註

使用[SelectString](#selectstring)成員函數尋找和選擇字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::尋找字串精確

尋找與*lpszFind*中指定的字串匹配的第一個清單框字串。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>參數

*nIndex 開始*<br/>
指定要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nIndexStart*指定的項。 如果*nIndexStart*為 -1,則從一開始就搜索整個列表框。

*lpszFind*<br/>
指向要搜尋的 null 終止字串。 此字串可以包含完整的檔名,包括副檔名。 搜尋不區分大小寫,因此字串可以包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

匹配項的索引,或LB_ERR搜索不成功。

### <a name="remarks"></a>備註

如果清單框創建時具有擁有者繪製樣式,但沒有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式`FindStringExact`,則成員函數將嘗試將雙字值與*lpszFind*的值匹配。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox:取得錨定索引

在清單框中檢索當前錨點項的零基索引。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>傳回值

當前錨點項的索引(如果成功);否則LB_ERR。

### <a name="remarks"></a>備註

在多選清單框中,錨點項是連續選定項目塊中的第一個或最後一個項。

### <a name="example"></a>範例

  請參考[CListBox::setAnchorIndex 的範例](#setanchorindex)。

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox:抓取關懷索引

確定在多選擇清單框中具有焦點矩形的項的索引。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>傳回值

清單框中具有焦點矩形的項的零基索引。 如果清單框是單選清單框,則返回值是所選項的索引(如果有)。

### <a name="remarks"></a>備註

該專案可能被選中,也可能未被選中。

### <a name="example"></a>範例

  請參考[CListBox::setCaretIndex 的範例](#setcaretindex)。

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox:取得計數

檢索清單框中的項目數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

清單框中的項目數,如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

返回的計數大於最後一個項的索引值(索引為零)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox:取得CurSel

在單選清單框中檢索當前選定項(如果有)的零基索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

當前選定項的零索引(如果是單選清單框)。 如果未當前選擇任何專案,則LB_ERR。

在多選清單框中,具有焦點的項的索引。

### <a name="remarks"></a>備註

不要調用`GetCurSel`多選清單框。 使用[CListBox:而是取得塞爾項目](#getselitems)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox:抓取水平範圍

從清單框檢索可水準滾動的寬度(以像素為單位)。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>傳回值

清單框的可滾動寬度(以像素為單位)。

### <a name="remarks"></a>備註

僅當清單框具有水準滾動條時,才適用此選項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox:抓取項目資料

檢索與指定清單框項關聯的應用程式提供的雙字值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在清單框中指定項的零基索引。

### <a name="return-value"></a>傳回值

與項關聯的值,或LB_ERR發生錯誤時的值。

### <a name="remarks"></a>備註

雙字值是[SetItemData](#setitemdata)呼叫的*dwItemData*參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox:抓取項目資料Ptr

檢索與指定清單框項關聯的應用程式提供的 32 位值作為指標 **(void)。** <strong>\*</strong>

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在清單框中指定項的零基索引。

### <a name="return-value"></a>傳回值

如果發生錯誤,則檢索指標,或 -1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox:抓取專案高度

確定清單框中專案的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在清單框中指定項的零基索引。 僅當清單框具有LBS_OWNERDRAWVARIABLE樣式時,才使用此參數;否則,應將其設置為 0。

### <a name="return-value"></a>傳回值

清單框中專案的高度(以像素為單位)。 如果清單框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式,則返回值是*nIndex*指定的項的高度。 如果發生錯誤,則返回值LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox:取得項目已重新完成

檢索目前顯示在列表框視窗中的列表框項的矩形的尺寸。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定項的零基索引。

*lpRect*<br/>
指定指向接收項的清單框客戶端座標的[RECT 結構](/windows/win32/api/windef/ns-windef-rect)的長指標。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox:抓取清單框資訊

檢索每列的項目數。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>傳回值

`CListBox`物件每列的項數。

### <a name="remarks"></a>備註

此成員函數類比[LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo)消息的功能,如 Windows SDK 中所述。

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox:抓取本地化

檢索清單框使用區域設置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>傳回值

清單框中字串區域設置識別碼 (LCID) 值。

### <a name="remarks"></a>備註

例如,區域設置用於確定排序表框中字串的排序順序。

### <a name="example"></a>範例

  請參考[CListBox::設定區域設定的範例](#setlocale)。

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox:GetSel

檢索項的選擇狀態。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定項的零基索引。

### <a name="return-value"></a>傳回值

如果選擇了指定的項,則為正數;如果選擇了指定項,則為正數。否則,它是 0。 如果發生錯誤,返回值LB_ERR。

### <a name="remarks"></a>備註

此成員函數適用於單選和多選清單框。

要檢查目前選擇的清單框項目的索引,請使用[CListBox::getCurSel](#getcursel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox:取得塞爾計數

檢索多選清單框中所選項的總數。

```
int GetSelCount() const;
```

### <a name="return-value"></a>傳回值

清單框中選取的項目計數。 如果清單框是單選清單框,則返回值LB_ERR。

### <a name="example"></a>範例

  請參考[CListBox 的範例:取得二個項目](#getselitems)。

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox:取得塞爾項目

使用整數陣列填充緩衝區,該陣列在多選清單框中指定選定項的項編號。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>參數

*nMax專案*<br/>
指定要放置在緩衝區中的項目編號的選定專案的最大數量。

*rgIndex*<br/>
指定指向緩衝區的指標,該指標足夠大,以容納*nMaxItems*指定的整數數。

### <a name="return-value"></a>傳回值

放置在緩衝區中的實際項數。 如果清單盒是單選清單框,則傳回值`LB_ERR`為 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox:抓取文字

從清單框中獲取字串。

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要檢索的字串的零基索引。

*lpszBuffer*<br/>
指向接收字串的緩衝區。 緩衝區必須有足夠的空間用於字串和終止空字元。 可以通過調`GetTextLen`用 成員函數提前確定字串的大小。

*rString*<br/>
`CString` 物件的參考。

### <a name="return-value"></a>傳回值

字串的長度(以位元組為單位),不包括終止空字元。 如果*nIndex*未指定有效的索引,則返回值LB_ERR。

### <a name="remarks"></a>備註

此成員函數的第二種形式使用字串文本填充`CString`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox:抓取文字

取得清單框項目中字串的長度。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定字串的零基索引。

### <a name="return-value"></a>傳回值

字串的長度(以字元表示),不包括終止空字元。 如果*nIndex*未指定有效的索引,則返回值LB_ERR。

### <a name="example"></a>範例

  請參考[CListBox 的範例::取得文字](#gettext)。

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox:取得熱門索引

檢索清單框中第一個可見項的零基索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功,清單框中第一個可見項的零基索引(如果成功)LB_ERR。

### <a name="remarks"></a>備註

最初,專案 0 位於清單框的頂部,但如果滾動清單框,則另一項可能位於頂部。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::在內存儲

分配記憶體以儲存清單框項。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>參數

*n 專案*<br/>
指定要添加的項目。

*n 位元組*<br/>
指定要為項字串分配的記憶體量(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果成功,則清單框在需要重新分配記憶體之前可以存儲的最大項數,否則LB_ERRSPACE,這意味著記憶體不足。

### <a name="remarks"></a>備註

在將大量項添加到`CListBox`之前調用此函數。

此功能有助於加快初始化具有大量項(超過 100 個)的清單框。 它預分配指定的記憶體量,以便後續[的 AddString、InsertString](#addstring)和[Dir](#dir)函數花費[InsertString](#insertstring)盡可能短的時間。 您可以使用參數的估計值。 如果高估,將分配一些額外的記憶體;如果估計過高,則分配一些額外的記憶體。如果低估,則正常分配用於超過預分配金額的物料。

僅限 Windows 95/98:nItems 參數限制為 16 位值。 *nItems* 這意味著清單框不能包含超過 32,767 個專案。 儘管專案數受到限制,但列表框中專案的總大小僅受可用記憶體的限制。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::插入字串

將字串插入到清單框中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要插入字串的位置的零基索引。 如果此參數為 -1,則字串將添加到清單的末尾。

*lpszItem*<br/>
指向要插入的 null 結尾字串。

### <a name="return-value"></a>傳回值

已插入字串之位置以零為基底的索引。 如果發生錯誤,返回值將LB_ERR;如果沒有足夠的空間來存儲新字串,則返回值LB_ERRSPACE。

### <a name="remarks"></a>備註

與[AddString](#addstring)成員`InsertString`函數 不同,不會導致對具有[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單進行排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox:專案從點

確定與*pt*中指定的點之近的清單框項目。

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
要查找最近的項的點,相對於列表框的工作區的左上角指定。

*b 外部*<br/>
如果*pt*位於清單框的工作區之外,則對 BOOL 變數的引用將設定為 TRUE;如果*pt*位於清單框的工作區內,則為 FALSE。

### <a name="return-value"></a>傳回值

最接近的項目的索引到*pt*中指定的點。

### <a name="remarks"></a>備註

您可以使用此函數確定滑鼠游標移動的清單框項。

### <a name="example"></a>範例

  請參考[CListBox::setAnchorIndex 的範例](#setanchorindex)。

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox:測量專案

創建具有擁有者繪製樣式的清單框時,由框架調用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lp 測量項目結構*<br/>
指向[測量結構](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的長指標。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 重寫此成員函數並填充`MEASUREITEMSTRUCT`結構以通知 Windows 列表框維度。 如果清單框是使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式創建的,則框架將針對清單框中的每個專案調用此成員函數。 否則,僅調用此成員一次。

有關使用`SubclassDlgItem`成員函數創建的所有者繪製列表框中使用`CWnd`[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的詳細資訊,請參閱[技術說明 14](../../mfc/tn014-custom-controls.md)中的討論。

有關`MEASUREITEMSTRUCT`結構的說明,請參閱[CWnd:onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox:重置內容

從清單框中移除所有專案。

```cpp
void ResetContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox:選擇字串

搜尋與指定字串匹配的列表框項,如果找到匹配項,則選擇該項。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*N 開始後*<br/>
包含要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nStartAfter*指定的項。 如果*nStartAfter*為 -1,則從一開始就搜索整個列表框。

*lpszItem*<br/>
包含要搜尋的前置字串。 搜尋是獨立於大小寫,因此此字串可能包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

如果搜索成功,則所選項的索引。 如果搜索不成功,則返回值LB_ERR,並且當前選擇不會更改。

### <a name="remarks"></a>備註

如有必要,將滾動清單框,以使所選項目進入視圖。

此成員函數不能與具有[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單框一起使用。

僅當項的初始字元(從起始點)與*lpszItem*指定的字串中的字元匹配時,才選擇項。

使用`FindString`成員函數查找字串而不選擇項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::塞爾項目範圍

在多選清單框中選擇多個連續專案。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>參數

*b 選擇*<br/>
指定如何設置所選內容。 如果 bSelect 為 TRUE,則選擇字串並突出顯示;如果*bSelect*為 TRUE,則選擇字串並突出顯示該字串。如果 FALSE,則刪除高光,並且不再選擇字串。

*n 第一項目*<br/>
指定要設置的第一個項的零基索引。

*n 最後項目*<br/>
指定要設置的最後一個項目的零基索引。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

僅對多個選擇清單框使用此成員函數。 如果需要在多選清單框中僅選擇一個專案(即,如果*nFirstItem*等於*nLastItem),* 請改為調用[SetSel](#setsel)成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::設置錨定索引

在多選清單框中設置錨點以開始擴展選擇。

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定將作為錨點的清單框項的零基索引。

### <a name="remarks"></a>備註

在多選清單框中,錨點項是連續選定項目塊中的第一個或最後一個項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::設置關懷索引

在多選清單框中將焦點矩形設置到指定索引處的項。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要在清單框中接收焦點矩形的項的零基索引。

*bScroll*<br/>
如果此值為 0,則滾動該專案,直到完全可見。 如果此值不是 0,則滾動該專案,直到它至少部分可見。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

如果項目不可見,則將其滾動到視圖中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>清單盒::設定欄寬

在多列清單框中設置所有列的寬度(使用[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式創建)。

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>參數

*cxWidth*<br/>
指定所有列的寬度(以像素為單位)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::設定CurSel

如有必要,選擇字串並將其滾動到視圖中。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>參數

*n 選擇*<br/>
指定要選擇的字串的零基索引。 如果*nSelect*為 -1,則列表框設置為沒有選擇。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

選擇新字串後,清單框將從以前選定的字串中刪除高光。

僅對單選清單框使用此成員函數。

在多選取清單框中設定或刪除選擇,請使用[CListBox::SetSel](#setsel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::設定水平範圍

設置寬度(以像素為單位),通過該寬度可以水準滾動清單框。

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>參數

*cx 範圍*<br/>
指定可以水平滾動清單框的像素數。

### <a name="remarks"></a>備註

如果清單框的大小小於此值,則水準滾動條將水準滾動清單框中的專案。 如果清單框大於或大於此值,則水準滾動條將隱藏。

要回應`SetHorizontalExtent`對的調用,清單框必須已使用[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)樣式定義。

此成員函數對多列清單框沒有用處。 對於多列清單框,調用`SetColumnWidth`成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox:設定項目資料

在清單框中設置與指定項關聯的值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定項的零基索引。

*dwItemData*<br/>
指定要與項關聯的值。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::設定項目資料Ptr

將清單框中與指定項關聯的 32 位值設置為指定的指標 **(void)。** <strong>\*</strong>

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定項的零基索引。

*pData*<br/>
指定要與項關聯的指標。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

此指標在清單框的生命週期內仍然有效,即使專案在清單框中的相對位置可能會隨著專案添加或刪除而更改。 因此,框中的項索引可以更改,但指標保持可靠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox:設定專案高度

在清單框中設置專案的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在清單框中指定項的零基索引。 僅當清單框具有LBS_OWNERDRAWVARIABLE樣式時,才使用此參數;否則,應將其設置為 0。

*cyItemHeight*<br/>
指定專案的高度(以像素為單位)。

### <a name="return-value"></a>傳回值

如果索引或高度無效,LB_ERR。

### <a name="remarks"></a>備註

如果清單框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式,則此函數將設置*nIndex*指定的項的高度。 否則,此函數將設置列表框中所有專案的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::設定當地語系化

設定此列表框的區域設定識別碼。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>參數

*n 新地*<br/>
要為清單框設置的新區域設置識別碼 (LCID) 值。

### <a name="return-value"></a>傳回值

此清單框的上一個區域設置標識符 (LCID) 值。

### <a name="remarks"></a>備註

如果未`SetLocale`調用,則從系統獲取預設區域設置。 此系統預設區域設置可以使用控制面板的區域(或國際)應用程式進行修改。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::設定塞爾

在多選清單框中選擇字串。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要設置的字串的零基索引。 如果 -1,則根據*bSelect*的值,將所選內容添加到所有字串或從所有字串中刪除。

*b 選擇*<br/>
指定如何設置所選內容。 如果 bSelect 為 TRUE,則選擇字串並突出顯示;如果*bSelect*為 TRUE,則選擇字串並突出顯示該字串。如果 FALSE,則刪除高光,並且不再選擇字串。 預設情況下,選擇並突出顯示指定的字串。

### <a name="return-value"></a>傳回值

如果發生錯誤,LB_ERR。

### <a name="remarks"></a>備註

僅對多個選擇清單框使用此成員函數。

要從單選清單框中選擇項目,請使用[CListBox::SetCurSel](#setcursel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::設定標籤

在清單框中設置製表位。

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>參數

*cxEachStop*<br/>
在每個*cxEachStop*對話框單元設置製表位。 有關對話框單元的說明,請參閱*rgTabStops。*

*NTabStops*<br/>
指定清單框中要具有的制表符停止數。

*rgTabStops*<br/>
指向包含對話框單元中的制表位位的整陣列的第一個成員。 對話框單位是水準或垂直距離。 一個水平對話框單位等於當前對話框基本寬度單位的四分之一,一個垂直對話框單位等於當前對話框基本高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 Windows`GetDialogBaseUnits`函數返回當前以像素為單位的當前對話框基本單位。 必須按增加的順序對制表位進行排序;不允許返回選項卡。

### <a name="return-value"></a>傳回值

如果設置了所有選項卡,則非零;否則 0。

### <a name="remarks"></a>備註

要將制表符停止設置為 2 個對話方塊單位的預設大小,請調用此成員函數的無參數版本。 要將製表符停止設置為大小 2 以外的大小,請使用*cxEachStop*參數呼叫版本。

要將製表符停止設置為大小陣列,請使用具有*rgTabStops*和*nTabStops*參數的版本。 將在*rgTabStops*中為每個值設置一個制表停止點,最多為*nTabStops*指定的數位。

要回應對成員函數的`SetTabStops`調用,清單框必須使用[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式創建。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::設定頂索引

確保特定清單框項可見。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單框項的零基索引。

### <a name="return-value"></a>傳回值

如果成功,則為零,如果發生錯誤,則LB_ERR。

### <a name="remarks"></a>備註

系統滾動清單框,直到*nIndex*指定的項顯示在列表框的頂部或已達到最大滾動範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::Vkeyto專案

當清單框的父視窗從列表框中接收WM_VKEYTOITEM消息時,由框架調用。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>參數

*N 鍵*<br/>
使用者按下的密鑰的虛擬金鑰代碼。 有關標準虛擬金鑰代碼的清單,請參閱 Winuser.h

*nIndex*<br/>
清單框的目前位置。

### <a name="return-value"></a>傳回值

返回 - 2 表示沒有進一步操作,1 表示預設操作,或非負數,用於指定清單框項的索引,用於執行擊鍵的預設操作。

### <a name="remarks"></a>備註

WM_VKEYTOITEM消息在收到WM_KEYDOWN消息時由清單框發送,但僅當清單框滿足以下兩個消息時才發送:

- 設置了[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式。

- 至少有一個專案。

您絕不應自行調用此功能。 重寫此函數以提供您自己的鍵盤消息的自定義處理。

您必須返回一個值,告訴框架執行了哪些操作。 返回值 - 2 表示應用程式處理了選擇項的所有方面,並且不需要清單框執行進一步操作。 在返回 - 2 之前,您可以設置選擇或移動支援者或兩者。 要設定選擇,請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 要移動 caret,請使用[SetCaretIndex](#setcaretindex)。

返回值 - 1 表示清單框應執行預設操作以回應擊鍵。預設實現返回 - 1。

返回值 0 或更高指定清單框中項的索引,並指示列表框應對給定項執行擊鍵的預設操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)
