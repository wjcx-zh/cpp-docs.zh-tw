---
title: CEditView 類別
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: e853a770dd1f98b1e7f06afd814962f3b3805ceb
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177871"
---
# <a name="ceditview-class"></a>CEditView 類別

檢視類別的類型，這個類型提供 Windows 編輯控制項功能，而且可用於實作簡單的文字編輯器功能。

## <a name="syntax"></a>語法

```
class CEditView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|建構類型 `CEditView` 的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CEditView::FindText](#findtext)|搜尋文字內的字串。|
|[CEditView::GetBufferLength](#getbufferlength)|取得字元緩衝區的長度。|
|[CEditView::GetEditCtrl](#geteditctrl)|提供存取權`CEdit`部分`CEditView`（Windows 編輯控制項） 的物件。|
|[CEditView::GetPrinterFont](#getprinterfont)|擷取目前的印表機字型。|
|[CEditView::GetSelectedText](#getselectedtext)|擷取目前文字選取範圍。|
|[CEditView::LockBuffer](#lockbuffer)|鎖定緩衝區。|
|[CEditView::PrintInsideRect](#printinsiderect)|呈現指定的矩形內的文字。|
|[CEditView::SerializeRaw](#serializeraw)|將序列化`CEditView`物件以磁碟為未經處理的文字。|
|[CEditView::SetPrinterFont](#setprinterfont)|將新的印表機字型設定。|
|[CEditView::SetTabStops](#settabstops)|設定定位停駐點，供螢幕顯示和列印。|
|[CEditView::UnlockBuffer](#unlockbuffer)|解除鎖定緩衝區。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|尋找下一個出現的文字字串。|
|[CEditView::OnReplaceAll](#onreplaceall)|新字串取代所有出現的指定字串。|
|[CEditView::OnReplaceSel](#onreplacesel)|取代目前的選取範圍。|
|[CEditView::OnTextNotFound](#ontextnotfound)|當尋找作業無法比對任何進一步的文字時呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|預設型別物件的樣式`CEditView`。|

## <a name="remarks"></a>備註

`CEditView`類別提供下列額外的函數：

- 列印。

- 尋找和取代。

因為類別`CEditView`是類別的衍生`CView`，類別的物件`CEditView`可以搭配文件和文件範本。

每個`CEditView`控制項的文字會保留在自己的全域記憶體物件。 您的應用程式可以有任意數目的`CEditView`物件。

建立類型的物件`CEditView`如果您想使用上面所列的新增功能的 [編輯] 視窗，或如果您想要簡單的文字編輯器功能。 A`CEditView`物件可以佔用整個視窗的工作區。 衍生您自己的類別，從`CEditView`新增或修改的基本功能，或宣告可以加入至文件範本的類別。

類別的預設實作`CEditView`處理下列命令：ID_EDIT_SELECT_ALL、 ID_EDIT_FIND、 ID_EDIT_REPLACE、 ID_EDIT_REPEAT 和 ID_FILE_PRINT。

預設字元限制`CEditView`是 (1024年\*1024年-1 = 1048575)。 這可以藉由呼叫基礎編輯控制項的 EM_LIMITTEXT 函式變更。 不過，限制會根據作業系統而不同，而且類型的編輯控制項 （單一或多行）。 如需有關這些限制的詳細資訊，請參閱 < [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext)。

若要變更這項限制在控制項中的，覆寫`OnCreate()`函式的程式`CEditView`類別，並插入下列程式碼行：

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

類型的物件`CEditView`(或衍生之型別的`CEditView`) 具有下列限制：

- `CEditView` 不會實作 true 所見即所得 (WYSIWYG) 編輯。 在螢幕上的可讀性與相符的列印的輸出之間沒有選擇`CEditView`且的螢幕可讀性。

- `CEditView` 可以在單一字型顯示文字。 支援任何特殊字元格式。 請參閱類別[CRichEditView](../../mfc/reference/cricheditview-class.md)更高的功能。

- 文字數量`CEditView`可包含限制。 這些限制是相同`CEdit`控制項。

如需詳細資訊`CEditView`，請參閱 <<c2> [ 衍生檢視類別中可用 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="ceditview"></a>  CEditView::CEditView

建構類型 `CEditView` 的物件。

```
CEditView();
```

### <a name="remarks"></a>備註

之後建構物件時，您必須呼叫[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)函式會使用編輯控制項。 如果您衍生的類別`CEditView`並將它新增至範本中使用`CWinApp::AddDocTemplate`，架構會呼叫這兩個這個建構函式和`Create`函式。

##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault

包含的預設樣式`CEditView`物件。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>備註

傳遞做為這個靜態成員*cheaderctrl:: Create*的參數`Create`函式來取得的預設樣式`CEditView`物件。

##  <a name="findtext"></a>  CEditView::FindText

呼叫`FindText`函式可搜尋`CEditView`物件的文字緩衝。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找的文字。

*bNext*<br/>
指定搜尋方向。 如果為 TRUE，搜尋方向是往緩衝區的結尾。 如果為 FALSE，搜尋方向是朝緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE，則搜尋會區分大小寫。 如果為 FALSE，則搜尋不區分大小寫。

### <a name="return-value"></a>傳回值

非零值，如果找到搜尋文字;否則為 0。

### <a name="remarks"></a>備註

此函式所指定的文字的緩衝區中搜尋文字*lpszFind*，從所指定的方向中目前選取範圍開始*bNext*，且所指定的區分大小寫*bCase*。 如果找到文字，則它會設定為找到的文字選取項目，並傳回非零值。 如果找不到文字，則函數會傳回 0。

您通常不需要呼叫`FindText`函式，除非您覆寫`OnFindNext`，其會呼叫`FindText`。

##  <a name="getbufferlength"></a>  CEditView::GetBufferLength

呼叫此成員函式，以取得目前在編輯控制項的緩衝區，不包括 null 結束字元的字元數。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>傳回值

緩衝區中字串的長度。

##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl

呼叫`GetEditCtrl`以取得使用 [編輯] 檢視的編輯控制項的參考。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>傳回值

對 `CEdit` 物件的參考。

### <a name="remarks"></a>備註

此控制項是型別的[CEdit](../../mfc/reference/cedit-class.md)，因此您可以操作直接使用的 Windows 編輯控制項`CEdit`成員函式。

> [!CAUTION]
>  使用`CEdit`物件可以變更狀態的基礎 Windows 編輯控制項。 例如，您不應該變更使用的定位點設定[CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函式，因為`CEditView`快取適用於在編輯控制項以及在列印中的這些設定。 請改用[CEditView::SetTabStops](#settabstops)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont

呼叫`GetPrinterFont`若要取得的指標[CFont](../../mfc/reference/cfont-class.md)物件，描述目前印表機字型。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>傳回值

指標`CFont`物件，指定目前的印表機字型;如果尚未設定印表機字型，則為 NULL。 該指標可能是暫時性的，因此不應該儲存供日後使用。

### <a name="remarks"></a>備註

如果印表機字型尚未設定，列印的行為預設`CEditView`類別是要使用的相同字型來顯示列印。

您可以使用此函式來判斷目前的印表機字型。 如果不想要的印表機字型，請使用[CEditView::SetPrinterFont](#setprinterfont)加以變更。

##  <a name="getselectedtext"></a>  CEditView::GetSelectedText

呼叫`GetSelectedText`複製到選取的文字`CString`物件，最多的選取範圍或選取範圍中之前的第一個的歸位字元的字元結尾。

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>參數

*strResult*<br/>
參考`CString`要接收所選的文字的物件。

##  <a name="lockbuffer"></a>  CEditView::LockBuffer

呼叫此成員函式，以取得緩衝區的指標。 不應該修改的緩衝區。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>傳回值

編輯控制項的緩衝區的指標。

##  <a name="onfindnext"></a>  CEditView::OnFindNext

搜尋文字中所指定的文字的緩衝區*lpszFind*，在所指定的方向*bNext*，與所指定的區分大小寫*bCase*。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找的文字。

*bNext*<br/>
指定搜尋方向。 如果為 TRUE，搜尋方向是往緩衝區的結尾。 如果為 FALSE，搜尋方向是朝緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE，則搜尋會區分大小寫。 如果為 FALSE，則搜尋不區分大小寫。

### <a name="remarks"></a>備註

搜尋會從目前的選取範圍的開頭，並透過呼叫來完成[FindText](#findtext)。 在預設實作中，`OnFindNext`呼叫[OnTextNotFound](#ontextnotfound)如果找不到的文字。

覆寫`OnFindNext`若要變更的方式`CEditView`-衍生的物件搜尋的文字。 `CEditView` 呼叫`OnFindNext`當使用者在標準的 [尋找] 對話方塊中選擇 [尋找下一個] 按鈕。

##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll

`CEditView` 呼叫`OnReplaceAll`當使用者在標準的 [取代] 對話方塊中選取 [取代全部] 按鈕。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找的文字。

*lpszReplace*<br/>
要取代搜尋文字的文字。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE，則搜尋會區分大小寫。 如果為 FALSE，則搜尋不區分大小寫。

### <a name="remarks"></a>備註

`OnReplaceAll` 搜尋文字中所指定的文字的緩衝區*lpszFind*，與所指定的區分大小寫*bCase*。 搜尋會從目前的選取範圍的開頭。 每次找到搜尋文字時，此函式所指定的文字取代文字的項目*lpszReplace*。 搜尋透過呼叫來達成[FindText](#findtext)。 在預設實作中， [OnTextNotFound](#ontextnotfound)找不到文字時呼叫。

如果目前的選取範圍不符*lpszFind*，選取項目已更新為第一個所指定的文字*lpszFind* ，且取代未在執行中。 這可讓使用者確認，這是他們想要執行選取項目類型不符合要被取代的文字時。

覆寫`OnReplaceAll`若要變更的方式`CEditView`-衍生的物件會取代文字。

##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel

`CEditView` 呼叫`OnReplaceSel`當使用者在標準的 [取代] 對話方塊中選取 [取代] 按鈕。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找的文字。

*bNext*<br/>
指定搜尋方向。 如果為 TRUE，搜尋方向是往緩衝區的結尾。 如果為 FALSE，搜尋方向是朝緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE，則搜尋會區分大小寫。 如果為 FALSE，則搜尋不區分大小寫。

*lpszReplace*<br/>
要取代找到的文字的文字。

### <a name="remarks"></a>備註

更換後選取項目，此函式，請搜尋緩衝區所指定的文字的下一個相符項目中的文字*lpszFind*，在所指定的方向*bNext*，使用區分大小寫所指定*bCase*。 搜尋透過呼叫來達成[FindText](#findtext)。 找不到文字，如果[OnTextNotFound](#ontextnotfound)呼叫。

覆寫`OnReplaceSel`若要變更的方式`CEditView`-衍生的物件會取代選取的文字。

##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound

此函式來變更預設的實作，它會呼叫 Windows 函式會覆寫`MessageBeep`。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找的文字。

##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect

呼叫`PrintInsideRect`列印文字中所指定的矩形*rectLayout*。

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
印表機裝置內容指標。

*rectLayout*<br/>
若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](/windows/desktop/api/windef/ns-windef-tagrect)指定呈現之文字的矩形。

*nIndexStart*<br/>
要轉譯的第一個字元的緩衝區內的索引。

*nIndexStop*<br/>
編製索引之後要呈現的最後一個字元的字元緩衝區中。

### <a name="return-value"></a>傳回值

要列印的下一個字元的索引 （也就是後呈現的最後一個字元的字元）。

### <a name="remarks"></a>備註

如果`CEditView`控制項沒有樣式 ES_AUTOHSCROLL、 文字換行轉譯矩形內。 如果控制項具有樣式 ES_AUTOHSCROLL，文字會裁剪矩形的右邊緣。

`rect.bottom`項目*rectLayout*有物件遭到變更，讓矩形的維度定義的部分原始文字所佔據的矩形。

##  <a name="serializeraw"></a>  CEditView::SerializeRaw

呼叫`SerializeRaw`能夠`CArchive`物件讀取或寫入的文字`CEditView`文字檔的物件。

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
若要參考`CArchive`物件會儲存已序列化的文字。

### <a name="remarks"></a>備註

`SerializeRaw` 不同於`CEditView`的內部實作`Serialize`，因為它會讀取並寫入的文字，而不需要上述物件描述的資料。

##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont

呼叫`SetPrinterFont`設為指定之字型的印表機字型*pFont*。

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
型別的物件的指標`CFont`。 如果是 NULL，用於列印的字型根據顯示的字型。

### <a name="remarks"></a>備註

如果您要一律使用特定字型，列印檢視，包括呼叫`SetPrinterFont`在您的類別`OnPreparePrinting`函式。 此虛擬函式稱為在列印之前，讓字型變更發生之前檢視的內容會列印。

##  <a name="settabstops"></a>  CEditView::SetTabStops

呼叫此函式來設定定位停駐點的顯示和列印使用。

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>參數

*nTabStops*<br/>
對話方塊單位的每個定位停駐點的寬度。

### <a name="remarks"></a>備註

支援單一定位停駐點寬度。 (`CEdit`物件支援多個定位點寬度。)寬度會以對話方塊單位等於 4 個字型在列印或顯示的時間使用的平均字元寬度 （以大寫和小寫字母字元只為基礎）。 您不應該使用`CEdit::SetTabStops`因為`CEditView`必須快取的定位停駐點值。

此函式可修改的它會呼叫的物件的索引標籤。 若要變更 [] 索引標籤會停止針對每個`CEditView`物件在您的應用程式，請呼叫每個物件的`SetTabStops`函式。

### <a name="example"></a>範例

此程式碼片段中每個第四個字元的控制項設定定位停駐點，藉由仔細測量控制項使用的字型。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer

呼叫此成員函式，來解除鎖定緩衝區。

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>備註

呼叫`UnlockBuffer`當您完成使用所傳回的指標之後, [LockBuffer](#lockbuffer)。

## <a name="see-also"></a>另請參閱

[MFC 範例 SUPERPAD](../../visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
