---
title: CPrintInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 96b6204fe46cb624d22506b2d3e5c1d7621b1865
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372474"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 結構

儲存列印或預覽列印工作的相關資訊。

## <a name="syntax"></a>語法

```
struct CPrintInfo
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|傳回列印的第一頁的數目。|
|[CPrintInfo::GetMaxPage](#getmaxpage)|傳回文件的最後一頁的數目。|
|[CPrintInfo::GetMinPage](#getminpage)|傳回文件的第一頁的數目。|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|傳回之前在結合的 DocObject 列印工作列印 DocObject 項目的第一頁的頁數。|
|[CPrintInfo::GetToPage](#gettopage)|傳回列印的最後一頁的數目。|
|[CPrintInfo::SetMaxPage](#setmaxpage)|設定文件的最後一頁的數目。|
|[CPrintInfo::SetMinPage](#setminpage)|設定文件的第一頁的數目。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|包含旗標，指出架構是否應該繼續列印迴圈。|
|[CPrintInfo::m_bDirect](#m_bdirect)|包含旗標，指出是否要列印文件直接 （不顯示 [列印] 對話方塊中）。|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|包含旗標，指出是否要列印的文件為 DocObject。|
|[CPrintInfo::m_bPreview](#m_bpreview)|包含旗標，指出是否正開放預覽文件。|
|[CPrintInfo::m_dwFlags](#m_dwflags)|指定 DocObject 列印作業。|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|包含使用者所建立的結構的指標。|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|識別目前正在列印的頁面數目。|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|指定目前的列印工作的作業系統所指派的作業數目|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|識別顯示在 [預覽] 視窗中; 中的頁面數目1 或 2。|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|合併的 DocObject 列印工作中指定特定 DocObject 的第一頁的位移。|
|[CPrintInfo::m_pPD](#m_ppd)|包含一個指向`CPrintDialog`用於 [列印] 對話方塊中的物件。|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|指定定義在目前的可用頁面區域的矩形。|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|包含頁碼顯示格式字串。|

## <a name="remarks"></a>備註

`CPrintInfo` 是一種結構，而且沒有基底類別。

此架構會建立的物件`CPrintInfo`每次列印或預覽列印 命令和選擇的命令完成時將其終結。

`CPrintInfo` 包含列印工作，整體而言，例如為要列印的頁面範圍和列印工作，例如目前正在列印的頁面的目前狀態的相關資訊。 有些資訊會儲存在相關聯[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件; 此物件包含使用者在 [列印] 對話方塊中輸入的值。

A`CPrintInfo`物件架構與您的檢視類別之間傳遞列印程序期間，用來交換兩者之間的資訊。 比方說，架構會告知檢視類別的文件列印的指派值給哪一頁`m_nCurPage`隸屬`CPrintInfo`; 類別，擷取值，並執行指定的頁面的實際列印的檢視。

另一個範例是以文件的長度不知道會在列印之前的情況。 在此情況下，檢視類別測試文件結尾的每個列印頁面的時間。 當到達結尾時，檢視類別設定`m_bContinuePrinting`隸屬`CPrintInfo`為 FALSE，這會通知架構，來停止列印迴圈。

`CPrintInfo` 成員函式會使用`CView`列在 「 另請參閱。 」 如需 Microsoft Foundation Class Library 所提供的列印架構的詳細資訊，請參閱[框架 Windows](../../mfc/frame-windows.md)並[文件/檢視架構](../../mfc/document-view-architecture.md)以及文件[列印](../../mfc/printing.md)和[列印：多頁文件](../../mfc/multipage-documents.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CPrintInfo`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage

呼叫此函式來擷取要列印的第一頁的數目。

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>傳回值

要列印的第一頁數目。

### <a name="remarks"></a>備註

這是在 [列印] 對話方塊中，使用者所指定的值，而且它會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者尚未指定值，預設會為文件的第一頁。

##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage

呼叫此函式可擷取文件的最後一頁的數目。

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>傳回值

文件的最後一頁數目。

### <a name="remarks"></a>備註

這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。

##  <a name="getminpage"></a>  CPrintInfo::GetMinPage

呼叫此函式可擷取文件的第一頁的數目。

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>傳回值

文件的第一頁數目。

### <a name="remarks"></a>備註

這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。

##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage

呼叫此函式可擷取位移列印 DocObject 用戶端的多個 DocObject 項目時。

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>傳回值

先前在結合的 DocObject 列印工作列印 DocObject 項目的第一頁的頁面數目。

### <a name="remarks"></a>備註

此值所參考`m_nOffsetPage`成員。 您的文件的第一頁編號`m_nOffsetPage`值 + 1 時列印出 DocObject 與其他使用中的文件。 `m_nOffsetPage`是有效的成員才`m_bDocObject`值為 TRUE。

##  <a name="gettopage"></a>  CPrintInfo::GetToPage

呼叫此函式來擷取要列印的最後一頁的數目。

```
UINT GetToPage() const;
```

### <a name="return-value"></a>傳回值

要列印的最後一頁數目。

### <a name="remarks"></a>備註

這是在 [列印] 對話方塊中，使用者所指定的值，而且它會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者尚未指定值，預設會為文件的最後一頁。

##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting

包含旗標，指出架構是否應該繼續列印迴圈。

### <a name="remarks"></a>備註

如果您要進行列印時分頁，您可以將這個成員設定為 FALSE 的覆寫中`CView::OnPrepareDC`一旦觸達文件結尾。 您沒有修改此變數，如果您已經指定列印工作使用的開始處的文件長度`SetMaxPage`成員函式。 `m_bContinuePrinting`成員是型別 BOOL 的公用變數。

##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect

架構，則為 TRUE 來設定這個成員 [列印] 對話方塊將會略過直接列印;FALSE 否則。

### <a name="remarks"></a>備註

當您從殼層或完成列印時列印時列印對話方塊通常略過使用命令識別碼 ID_FILE_PRINT_DIRECT。

您通常不會變更這個成員，但如果您變更它，將它變更之前呼叫[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)中的覆寫[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。

##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject

包含旗標，指出是否要列印的文件為 DocObject。

### <a name="remarks"></a>備註

資料成員`m_dwFlags`和`m_nOffsetPage`是無效的除非此旗標為 TRUE。

##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview

包含旗標，指出是否正開放預覽文件。

### <a name="remarks"></a>備註

這是依據執行命令的使用者，架構中設定。 [列印] 對話方塊中，不會顯示預覽列印工作。 `m_bPreview`成員是型別 BOOL 的公用變數。

##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags

包含指定 DocObject 列印作業的旗標的組合。

### <a name="remarks"></a>備註

有效的只有當資料成員`m_bDocObject`為 TRUE。

旗標可以是下列一或多個下列值：

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData

包含使用者所建立的結構的指標。

### <a name="remarks"></a>備註

您可以使用此儲存不想將儲存在您的檢視類別的特定列印的資料。 `m_lpUserData`成員是型別 LPVOID 的公用變數。

##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage

包含目前的頁面數目。

### <a name="remarks"></a>備註

這個架構會呼叫`CView::OnPrepareDC`並`CView::OnPrint`一次每一頁的文件中，指定不同的值，這個成員每次; 其值的範圍所傳回的值從`GetFromPage`所傳回的`GetToPage`。 使用這個成員中的覆寫`CView::OnPrepareDC`和`CView::OnPrint`列印文件指定的頁面。

第一次叫用預覽模式時，架構就會讀取這個成員來決定一開始應該先預覽文件的哪一頁的值。 您可以設定這個成員的值中的覆寫`CView::OnPreparePrinting`維護使用者的目前位置的文件中，輸入 [預覽] 模式時。 `m_nCurPage`成員是型別是 UINT 的公用變數。

##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber

指出目前的列印工作的作業系統所指派的作業數目。

### <a name="remarks"></a>備註

如果還未列印工作，這個值可以是 SP_ERROR (亦即，如果`CPrintInfo`物件新建構的而且尚未使用列印)，或如果正在啟動工作時發生錯誤。

##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages

包含以預覽模式; 顯示的頁面數目它可以是 1 或 2。

### <a name="remarks"></a>備註

`m_nNumPreviewPages`成員是型別是 UINT 的公用變數。

##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage

包含在結合的 DocObject 列印工作之前特定 DocObject 的第一頁的頁數。

##  <a name="m_ppd"></a>  CPrintInfo::m_pPD

包含一個指向`CPrintDialog`物件，用來顯示列印工作的 [列印] 對話方塊。

### <a name="remarks"></a>備註

`m_pPD`成員是宣告為指標的公用變數`CPrintDialog`。

##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw

在邏輯座標中指定頁面的可用繪圖區域。

### <a name="remarks"></a>備註

您可以把這在覆寫`CView::OnPrint`。 您可以使用這個成員來追蹤在列印標頭、 頁尾等等之後，仍可以使用哪一個區域。 `m_rectDraw`成員是公用類型的變數`CRect`。

##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc

包含用來在預覽列印; 期間顯示的頁面數字格式字串此字串是由兩個子字串，一個用於單一頁面顯示，另一個用於每個以 '\n' 字元結尾的雙精度浮點數頁面顯示所組成。

### <a name="remarks"></a>備註

架構會使用 「 頁面 %u\npages%u-%u\n"為預設值。 如果您想要以不同格式列印的頁碼，格式字串，指定在覆寫`CView::OnPreparePrinting`。 `m_strPageDesc`成員是公用類型的變數`CString`。

##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage

呼叫此函式來指定文件的最後一頁的數目。

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>參數

*nMaxPage*<br/>
文件的最後一頁的數目。

### <a name="remarks"></a>備註

這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果文件的長度為已知，在列印之前，呼叫此函式的覆寫從`CView::OnPreparePrinting`。 如果文件的長度取決於使用者在 [列印] 對話方塊中所指定的設定，會呼叫此函式的覆寫從`CView::OnBeginPrinting`。 如果不知道文件長度，會在列印之前，使用`m_bContinuePrinting`控制列印迴圈的成員。

### <a name="example"></a>範例

  範例，請參閱[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。

##  <a name="setminpage"></a>  CPrintInfo::SetMinPage

呼叫此函式來指定文件的第一頁的數目。

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>參數

*nMinPage*<br/>
文件的第一頁的數目。

### <a name="remarks"></a>備註

頁碼通常 1 開始。 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
