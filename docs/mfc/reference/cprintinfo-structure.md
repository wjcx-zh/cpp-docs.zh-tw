---
title: CPrintInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: cf0a1e6b7e742e950663f1ed9cc9ff2ddabd9d6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364030"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 結構

存儲有關列印或列印預覽作業的資訊。

## <a name="syntax"></a>語法

```
struct CPrintInfo
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPrintInfo:從頁面取得](#getfrompage)|返回要列印的第一頁的數量。|
|[CPrintInfo:取得最大頁面](#getmaxpage)|返回文檔最後一頁的編號。|
|[CPrintInfo:取得明頁](#getminpage)|返回文檔的第一頁編號。|
|[CPrintInfo:取得不一頁](#getoffsetpage)|傳回在組合文件物件列印作業中列印的 DocObject 項第一頁前面的頁數。|
|[CPrintInfo:取得頁面](#gettopage)|返回要列印的最後一頁的數量。|
|[CPrintInfo::設定最大頁面](#setmaxpage)|設置文檔最後一頁的編號。|
|[CPrintInfo:設定明頁](#setminpage)|設置文檔第一頁的編號。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPrint資訊:m_bContinuePrinting](#m_bcontinueprinting)|包含指示框架是否應繼續列印迴圈的標誌。|
|[CPrint資訊::m_bDirect](#m_bdirect)|包含指示文件是否直接列印的標誌(不顯示"列印"對話方塊)。|
|[CPrint資訊:m_bDocObject](#m_bdocobject)|包含指示要列印的文件是否為 DocObject 的標誌。|
|[CPrint資訊:m_bPreview](#m_bpreview)|包含指示文檔是否正在預覽的標誌。|
|[CPrint資訊:m_dwFlags](#m_dwflags)|指定文件物件列印操作。|
|[CPrint資訊:m_lpUserData](#m_lpuserdata)|包含指向使用者創建結構的指標。|
|[CPrint資訊:m_nCurPage](#m_ncurpage)|標識當前列印的頁面的編號。|
|[CPrint資訊:m_nJobNumber](#m_njobnumber)|指定作業系統為目前的列印工作配置的工作編號|
|[CPrint資訊:m_nNumPreviewPages](#m_nnumpreviewpages)|標識預覽視窗中顯示的頁數;1或 2。|
|[CPrint資訊:m_nOffsetPage](#m_noffsetpage)|在組合的 DocObject 列印作業中指定特定文件物件的第一頁的偏移量。|
|[CPrint資訊:m_pPD](#m_ppd)|包含指向用於「列印」`CPrintDialog`對話框的物件的指標。|
|[CPrint資訊:m_rectDraw](#m_rectdraw)|指定定義目前可用頁面區域的矩形。|
|[CPrint資訊:m_strPageDesc](#m_strpagedesc)|包含用於頁碼顯示的格式字串。|

## <a name="remarks"></a>備註

`CPrintInfo`是一個結構,沒有基類。

框架`CPrintInfo`在每次選擇「列印預覽」命令時都會創建一個物件,並在命令完成後將其銷毀。

`CPrintInfo`包含有關整個列印作業的資訊,例如要列印的頁面範圍和列印作業的當前狀態,例如當前列印的頁面。 某些資訊存儲在關聯的[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件中;此物件包含使用者在「列印」對話框中輸入的值。

在`CPrintInfo`列印過程中,在框架和視圖類之間傳遞物件,用於在兩者之間交換資訊。 例如,框架透過將值`m_nCurPage``CPrintInfo`配置給視圖類檢索值並執行指定頁面的實際列印。

另一個示例是文檔的長度在列印之前不為人所知的情況。 在此情況下,每次列印頁面時,視圖類都會測試文檔末尾的視圖類。 到達末尾時,視圖類將`m_bContinuePrinting`的成員設置為 FALSE;視圖類將`CPrintInfo`的成員 設置為 FALSE。這將通知框架停止列印迴圈。

`CPrintInfo`由「另請參閱」下`CView`列出的成員函數使用。 有關Microsoft基礎類庫提供的列印體系結構的詳細資訊,請參閱[框架Windows](../../mfc/frame-windows.md)和[文檔/視圖體系結構](../../mfc/document-view-architecture.md)以及[文章"列印](../../mfc/printing.md)和[列印:多頁文件](../../mfc/multipage-documents.md)"。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CPrintInfo`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo:從頁面取得

調用此函數以檢索要列印的第一頁的編號。

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>傳回值

要列印的第一頁的數量。

### <a name="remarks"></a>備註

這是使用者在「列印」對話框中指定的值,它存儲在`CPrintDialog``m_pPD`成員引用的物件中。 如果使用者未指定值,則預設值為文檔的第一頁。

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo:取得最大頁面

調用此函數以檢索文件最後一頁的編號。

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>傳回值

文檔最後一頁的編號。

### <a name="remarks"></a>備註

此值儲存在成員引用`CPrintDialog`的物件中。 `m_pPD`

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo:取得明頁

調用此函數以檢索文檔第一頁的編號。

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>傳回值

文檔第一頁的編號。

### <a name="remarks"></a>備註

此值儲存在成員引用`CPrintDialog`的物件中。 `m_pPD`

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo:取得不一頁

呼叫此函數以從 DocObject 用戶端列印多個 DocObject 項時檢索偏移量。

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>傳回值

在組合的 DocObject 列印工作中列印的 DocObject 項第一頁前面的頁數。

### <a name="remarks"></a>備註

此值由`m_nOffsetPage`成員引用。 當文件的第一頁與其他活動文件一起`m_nOffsetPage`列印為 DocObject 時,將編號為值 = 1。 僅當`m_nOffsetPage`值為`m_bDocObject`TRUE 時 ,該成員才有效。

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo:取得頁面

調用此函數以檢索要列印的最後一頁的數量。

```
UINT GetToPage() const;
```

### <a name="return-value"></a>傳回值

要列印的最後一頁數。

### <a name="remarks"></a>備註

這是使用者在「列印」對話框中指定的值,它存儲在`CPrintDialog``m_pPD`成員引用的物件中。 如果使用者未指定值,則預設值是文檔的最後一頁。

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrint資訊:m_bContinuePrinting

包含指示框架是否應繼續列印迴圈的標誌。

### <a name="remarks"></a>備註

如果要執行列印時間分頁,則可以在到達文檔末`CView::OnPrepareDC`尾 後重寫此成員設置為 FALSE。 如果使用`SetMaxPage`成員函數在列印作業的開頭指定文檔的長度,則不必修改此變數。 該`m_bContinuePrinting`成員是 BOOL 類型的公共變數。

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrint資訊::m_bDirect

如果「列印」對話框將繞過以進行直接列印,則框架將此成員設置為 TRUE;否則。

### <a name="remarks"></a>備註

當您從 shell 列印或使用命令 ID ID_FILE_PRINT_DIRECT進行列印時,通常繞過「列印」對話方塊。

您通常不會更改此成員,但如果您更改了它,請先在您重寫[CView :D:::onPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)之前[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)更改它。

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrint資訊:m_bDocObject

包含指示要列印的文件是否為 DocObject 的標誌。

### <a name="remarks"></a>備註

資料成員`m_dwFlags`,`m_nOffsetPage`並且無效,除非此標誌為 TRUE。

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrint資訊:m_bPreview

包含指示文檔是否正在預覽的標誌。

### <a name="remarks"></a>備註

這由框架設置,具體取決於使用者執行的命令。 列印預覽作業不顯示「列印」對話框。 該`m_bPreview`成員是 BOOL 類型的公共變數。

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrint資訊:m_dwFlags

包含指定 DocObject 列印操作的標誌組合。

### <a name="remarks"></a>備註

僅當數據成員`m_bDocObject`為 TRUE 時才有效。

標誌可以是以下一個或多個值:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrint資訊:m_lpUserData

包含指向使用者創建結構的指標。

### <a name="remarks"></a>備註

可以使用它存儲不希望存儲在檢視類中的特定於列印的數據。 該`m_lpUserData`成員是LPVOID類型的公共變數。

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrint資訊:m_nCurPage

包含當前頁面的編號。

### <a name="remarks"></a>備註

框架調用`CView::OnPrepareDC`文檔`CView::OnPrint`的每 一頁,每次為該成員指定不同的值;其值範圍從返回`GetFromPage`的值到返回的值。 `GetToPage` 在 重寫 中使用此`CView::OnPrepareDC`成員`CView::OnPrint`, 並列印文件的指定頁面。

首次調用預覽模式時,框架將讀取此成員的值,以確定應首先預覽文檔的哪個頁面。 您可以在重寫中設定此成員的值`CView::OnPreparePrinting`,以在輸入預覽模式時維護使用者在文件中的當前位置。 該`m_nCurPage`成員是 UINT 類型的公共變數。

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrint資訊:m_nJobNumber

指示作業系統為當前列印作業分配的作業編號。

### <a name="remarks"></a>備註

如果作業尚未列印(即`CPrintInfo`物件是新構造且尚未用於列印),或者啟動作業時出現錯誤,則可能會SP_ERROR此值。

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrint資訊:m_nNumPreviewPages

包含預覽模式下顯示的頁數;它可以是 1 或 2。

### <a name="remarks"></a>備註

該`m_nNumPreviewPages`成員是 UINT 類型的公共變數。

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrint資訊:m_nOffsetPage

在組合的 DocObject 列印作業中,包含特定文件物件第一頁前面的頁數。

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrint資訊:m_pPD

包含指向用於顯示列印作業`CPrintDialog`的「列印」對話框的物件的指標。

### <a name="remarks"></a>備註

成員`m_pPD`是作為`CPrintDialog`指向的指標聲明的公共變數。

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrint資訊:m_rectDraw

在邏輯座標中指定頁面的可用繪圖區域。

### <a name="remarks"></a>備註

您可能希望在重寫 中引用這`CView::OnPrint`一點。 您可以使用此成員追蹤列印標題、頁腳等後仍可用的區域。 成員`m_rectDraw`是類型`CRect`的公共變數。

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrint資訊:m_strPageDesc

包含用於在列印預覽期間顯示頁碼的格式字串;此字串由兩個子字串組成,一個用於單頁顯示,一個用於雙頁顯示,每個子字串由"\n"字元終止。

### <a name="remarks"></a>備註

框架使用「頁面 %u\nPages %u-%u\n」作為預設值。 如果希望頁碼具有不同的格式,請在重寫`CView::OnPreparePrinting`中 指定格式字串。 成員`m_strPageDesc`是類型`CString`的公共變數。

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::設定最大頁面

呼叫此函數以指定文件最後一頁的編號。

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>參數

*nMaxPage*<br/>
文檔最後一頁的編號。

### <a name="remarks"></a>備註

此值儲存在成員引用`CPrintDialog`的物件中。 `m_pPD` 如果在列印文檔之前知道文檔的長度,請從重寫`CView::OnPreparePrinting`調用 此函數。 如果文件的長度取決於使用者在「列印」對話框中指定的設置,請從重寫 調`CView::OnBeginPrinting`用 此函數。 如果在列印文檔之前不知道文檔的長度,`m_bContinuePrinting`請使用該成員控制列印迴圈。

### <a name="example"></a>範例

  請參閱[CView 的範例::在準備列印](../../mfc/reference/cview-class.md#onprepareprinting)。

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo:設定明頁

呼叫此函數以指定文件第一頁的編號。

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>參數

*nMinPage*<br/>
文檔第一頁的編號。

### <a name="remarks"></a>備註

頁碼通常從 1 開始。 此值儲存在成員引用`CPrintDialog`的物件中。 `m_pPD`

## <a name="see-also"></a>另請參閱

[MFC 樣品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[C查看::結束列印](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::結束列印預覽](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[C查看::在準備DC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[C查看::準備列印](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[C查看::在列印](../../mfc/reference/cview-class.md#onprint)
