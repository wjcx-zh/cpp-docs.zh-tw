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
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506719"
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
|[CEditView::GetEditCtrl](#geteditctrl)|提供`CEditView`物件 (Windows `CEdit`編輯控制項) 部分的存取權。|
|[CEditView::GetPrinterFont](#getprinterfont)|抓取目前的印表機字型。|
|[CEditView::GetSelectedText](#getselectedtext)|抓取目前的文字選取範圍。|
|[CEditView::LockBuffer](#lockbuffer)|鎖定緩衝區。|
|[CEditView::PrintInsideRect](#printinsiderect)|呈現指定矩形內的文字。|
|[CEditView::SerializeRaw](#serializeraw)|`CEditView`將物件序列化至磁片做為原始文字。|
|[CEditView::SetPrinterFont](#setprinterfont)|設定新的印表機字型。|
|[CEditView::SetTabStops](#settabstops)|設定螢幕顯示和列印的定位停駐點。|
|[CEditView::UnlockBuffer](#unlockbuffer)|解除鎖定緩衝區。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|尋找下一個出現的文字字串。|
|[CEditView::OnReplaceAll](#onreplaceall)|以新字串取代所有出現的指定字串。|
|[CEditView::OnReplaceSel](#onreplacesel)|取代目前的選取範圍。|
|[CEditView::OnTextNotFound](#ontextnotfound)|當尋找作業無法比對任何進一步的文字時呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|類型`CEditView`物件的預設樣式。|

## <a name="remarks"></a>備註

`CEditView`類別提供下列額外的功能:

- 印刷.

- 尋找和取代。

因為類別`CEditView`是類別`CView`的衍生, 所以類別`CEditView`的物件可以與檔和檔範本搭配使用。

每`CEditView`個控制項的文字都會保留在它自己的全域記憶體物件中。 您的應用程式可以有任意`CEditView`數目的物件。

如果您想要`CEditView`具有以上所列新增功能的 [編輯] 視窗, 或想要使用簡單的文字編輯器功能, 請建立類型的物件。 `CEditView`物件可以佔用整個視窗的工作區。 從`CEditView`衍生您自己的類別, 以加入或修改基本功能, 或宣告可以加入至檔範本的類別。

類別`CEditView`的預設實作為處理下列命令:ID_EDIT_SELECT_ALL、ID_EDIT_FIND、ID_EDIT_REPLACE、ID_EDIT_REPEAT 和 ID_FILE_PRINT。

的預設字元限制`CEditView`為 (1024 \* 1024-1 = 1048575)。 這可以藉由呼叫基礎編輯控制項的 EM_LIMITTEXT 函式來變更。 不過, 限制會根據作業系統和編輯控制項的類型 (單一或多行) 而有所不同。 如需這些限制的詳細資訊, 請參閱[EM_LIMITTEXT](/windows/win32/Controls/em-limittext)。

若要在控制項中變更此限制, 請`OnCreate()`覆寫類別`CEditView`的函式, 並插入下列程式程式碼:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

類型`CEditView`的物件 (或衍生自`CEditView`的類型) 具有下列限制:

- `CEditView`不會實作為您所看到的結果 (WYSIWYG) 編輯。 在螢幕上的可讀性與相符的列印輸出之間有選擇時, `CEditView`選擇是否要讓螢幕更容易閱讀。

- `CEditView`只能在單一字型中顯示文字。 不支援特殊字元格式。 如需更多的功能, 請參閱類別[CRichEditView](../../mfc/reference/cricheditview-class.md) 。

- `CEditView`可以包含的文字數量有限。 `CEdit`控制項的限制與相同。

如需的詳細`CEditView`資訊, 請參閱[MFC 中提供的衍生視圖類別](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>需求

**標頭:** afxext.h。h

##  <a name="ceditview"></a>CEditView:: CEditView

建構類型 `CEditView` 的物件。

```
CEditView();
```

### <a name="remarks"></a>備註

在建立物件之後, 您必須呼叫[CWnd:: Create](../../mfc/reference/cwnd-class.md#create)函式, 才能使用編輯控制項。 如果您從`CEditView`衍生類別, 並使用`CWinApp::AddDocTemplate`將它加入至範本, 則架構會呼叫這個函式和`Create`函式。

##  <a name="dwstyledefault"></a>CEditView::d wStyleDefault

包含`CEditView`物件的預設樣式。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>備註

傳遞這個靜態成員做為函式的 dwStyle `Create`參數, 以取得`CEditView`物件的預設樣式。

##  <a name="findtext"></a>CEditView:: FindText

呼叫函數來`CEditView`搜尋物件的文字緩衝區。 `FindText`

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的文字。

*bNext*<br/>
指定搜尋的方向。 如果為 TRUE, 則表示搜尋方向朝向緩衝區結尾。 如果為 FALSE, 則表示搜尋方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 若為 TRUE, 則搜尋會區分大小寫。 如果為 FALSE, 則表示搜尋不區分大小寫。

### <a name="return-value"></a>傳回值

如果找到搜尋文字, 則為非零值;否則為0。

### <a name="remarks"></a>備註

此函式會在緩衝區中的文字中搜尋*lpszFind*所指定的文字, 從目前的選取範圍開始, 以*bNext*所指定的方向, 以及由*bCase*所指定的區分大小寫。 如果找到文字, 則會將選取範圍設定為找到的文字, 並傳回非零值。 如果找不到文字, 則函數會傳回0。

您通常不需要呼叫`FindText`函式, 除非您覆寫`OnFindNext`, 而這會呼叫。 `FindText`

##  <a name="getbufferlength"></a>CEditView:: GetBufferLength

呼叫這個成員函式可取得目前在編輯控制項緩衝區中的字元數, 不包括 null 結束字元。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>傳回值

緩衝區中的字串長度。

##  <a name="geteditctrl"></a>CEditView:: GetEditCtrl

呼叫`GetEditCtrl`以取得編輯檢視所使用之編輯控制項的參考。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>傳回值

對 `CEdit` 物件的參考。

### <a name="remarks"></a>備註

這個控制項的類型是[CEdit](../../mfc/reference/cedit-class.md), 因此您可以使用`CEdit`成員函式直接操作 Windows 編輯控制項。

> [!CAUTION]
>  `CEdit`使用物件可以變更基礎 Windows 編輯控制項的狀態。 例如, 您不應該使用[CEdit:: SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函式來變更索引標籤設定`CEditView` , 因為會快取這些設定, 以便在編輯控制項和列印中使用。 請改用[CEditView:: SetTabStops](#settabstops)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>CEditView:: GetPrinterFont

呼叫`GetPrinterFont`以取得描述目前印表機字型的[CFont](../../mfc/reference/cfont-class.md)物件指標。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>傳回值

`CFont`物件的指標, 指定目前的印表機字型;如果印表機字型尚未設定, 則為 Null。 該指標可能是暫時性的，因此不應該儲存供日後使用。

### <a name="remarks"></a>備註

如果尚未設定印表機字型, `CEditView`類別的預設列印行為會使用用於顯示的相同字型進行列印。

使用此函數來判斷目前的印表機字型。 如果它不是所需的印表機字型, 請使用[CEditView:: SetPrinterFont](#setprinterfont)加以變更。

##  <a name="getselectedtext"></a>CEditView:: GetSelectedText

呼叫`GetSelectedText`以將選取的文字複製`CString`到物件中, 直到選取範圍的結尾或第一個換行字元前面的字元為止。

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>參數

*strResult*<br/>
`CString`物件的參考, 用來接收選取的文字。

##  <a name="lockbuffer"></a>CEditView:: LockBuffer

呼叫這個成員函式以取得緩衝區的指標。 緩衝區不應該修改。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>傳回值

編輯控制項緩衝區的指標。

##  <a name="onfindnext"></a>CEditView:: OnFindNext

以*bNext*指定的方向, 以*bCase*指定的區分大小寫, 搜尋緩衝區中的文字中*lpszFind*所指定的文字。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的文字。

*bNext*<br/>
指定搜尋的方向。 如果為 TRUE, 則表示搜尋方向朝向緩衝區結尾。 如果為 FALSE, 則表示搜尋方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 若為 TRUE, 則搜尋會區分大小寫。 如果為 FALSE, 則表示搜尋不區分大小寫。

### <a name="remarks"></a>備註

搜尋會從目前選取範圍的開頭開始, 並透過呼叫[FindText](#findtext)來完成。 在預設的執行中`OnFindNext` , 如果找不到文字, 則會呼叫[OnTextNotFound](#ontextnotfound) 。

覆`OnFindNext`寫以變更衍生物件`CEditView`搜尋文字的方式。 `CEditView`當`OnFindNext`使用者在 [標準尋找] 對話方塊中選擇 [尋找下一個] 按鈕時呼叫。

##  <a name="onreplaceall"></a>CEditView:: OnReplaceAll

`CEditView`當`OnReplaceAll`使用者選取 [標準取代] 對話方塊中的 [全部取代] 按鈕時呼叫。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的文字。

*lpszReplace*<br/>
要取代搜尋文字的文字。

*bCase*<br/>
指定搜尋是否區分大小寫。 若為 TRUE, 則搜尋會區分大小寫。 如果為 FALSE, 則表示搜尋不區分大小寫。

### <a name="remarks"></a>備註

`OnReplaceAll`搜尋緩衝區中的文字, 以取得由*bCase*指定的區分大小寫*lpszFind*所指定的文字。 搜尋會從目前選取範圍的開頭開始。 每次找到搜尋文字時, 此函式會使用*lpszReplace*所指定的文字來取代該文字的出現次數。 搜尋是透過呼叫[FindText](#findtext)來完成。 在預設的執行中, 如果找不到文字, 則會呼叫[OnTextNotFound](#ontextnotfound) 。

如果目前的選取範圍與*lpszFind*不符, 則會將選取專案更新為*lpszFind*所指定之文字的第一次出現, 而且不會執行 replace。 這可讓使用者在選取專案不符合要取代的文字時, 確認這是他們想要執行的動作。

覆`OnReplaceAll`寫以變更衍生物件`CEditView`取代文字的方式。

##  <a name="onreplacesel"></a>CEditView:: OnReplaceSel

`CEditView`當`OnReplaceSel`使用者選取 [標準取代] 對話方塊中的 [取代] 按鈕時呼叫。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的文字。

*bNext*<br/>
指定搜尋的方向。 如果為 TRUE, 則表示搜尋方向朝向緩衝區結尾。 如果為 FALSE, 則表示搜尋方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 若為 TRUE, 則搜尋會區分大小寫。 如果為 FALSE, 則表示搜尋不區分大小寫。

*lpszReplace*<br/>
要用來取代找到的文字的文字。

### <a name="remarks"></a>備註

取代選取範圍之後, 此函式會搜尋緩衝區中的文字, 以根據*bNext*指定的方向, 以*bCase*所指定的區分大小寫, 在*lpszFind*指定的下一個文字出現。 搜尋是透過呼叫[FindText](#findtext)來完成。 如果找不到文字, 則會呼叫[OnTextNotFound](#ontextnotfound) 。

覆`OnReplaceSel`寫以變更衍生物件`CEditView`取代選取文字的方式。

##  <a name="ontextnotfound"></a>CEditView:: OnTextNotFound

覆寫此函式以變更預設的實作為呼叫 Windows `MessageBeep`函式。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的文字。

##  <a name="printinsiderect"></a>CEditView::P rintInsideRect

呼叫`PrintInsideRect`以在*rectLayout*所指定的矩形中列印文字。

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
印表機裝置內容的指標。

*rectLayout*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](/windows/win32/api/windef/ns-windef-rect)的參考, 指定要在其中呈現文字的矩形。

*nIndexStart*<br/>
要轉譯之第一個字元的緩衝區內的索引。

*nIndexStop*<br/>
要轉譯之最後一個字元之後的字元緩衝區內的索引。

### <a name="return-value"></a>傳回值

要列印的下一個字元的索引 (也就是最後一個呈現的字元之後的字元)。

### <a name="remarks"></a>備註

`CEditView`如果控制項沒有樣式 ES_AUTOHSCROLL, 文字就會包裝在轉譯矩形內。 如果控制項的樣式為 ES_AUTOHSCROLL, 則會在矩形的右邊緣裁剪文字。

*RectLayout 物件*的元素會變更,因此矩形的維度會定義文字所佔用之原始矩形的`rect.bottom`部分。

##  <a name="serializeraw"></a>CEditView:: SerializeRaw

呼叫`SerializeRaw` , `CEditView`讓物件讀取或寫入物件中的文字至文字檔。 `CArchive`

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
參考儲存序列化`CArchive`文字的物件。

### <a name="remarks"></a>備註

`SerializeRaw`與的內部`Serialize`執行不同之處在于, 它只會讀取和寫入文字, 而不會有先前的物件描述資料。 `CEditView`

##  <a name="setprinterfont"></a>CEditView:: SetPrinterFont

呼叫`SetPrinterFont` , 將印表機字型設定為*pFont*所指定的字型。

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
類型`CFont`物件的指標。 如果是 Null, 用於列印的字型會以顯示字型為基礎。

### <a name="remarks"></a>備註

如果您想要讓您的視圖一律使用特定字型進行列印, 請`SetPrinterFont`在類別的`OnPreparePrinting`函式中包含對的呼叫。 此虛擬函式會在進行列印之前呼叫, 因此字型變更會在列印視圖的內容之前進行。

##  <a name="settabstops"></a>CEditView:: SetTabStops

呼叫此函式可設定用於顯示和列印的定位停駐點。

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>參數

*nTabStops*<br/>
每個索引標籤的寬度, 以對話方塊為單位。

### <a name="remarks"></a>備註

僅支援單一索引標籤-停用寬度。 ( `CEdit`物件支援多個索引標籤寬度)。寬度是在對話單位中, 其等於列印或顯示時所使用字型的平均字元寬度的四分之一 (僅以大寫和小寫字母字元為基礎)。 您不應該使用`CEdit::SetTabStops` , `CEditView`因為必須快取 tab 鍵-stop 值。

此函式只會修改所呼叫物件的索引標籤。 若要變更應用程式中每`CEditView`個物件的定位停駐點, 請呼叫每`SetTabStops`個物件的函式。

### <a name="example"></a>範例

此程式碼片段會藉由仔細測量控制項所使用的字型, 將控制項中的索引標籤設定為每四個字元。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

呼叫這個成員函式來解除鎖定緩衝區。

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>備註

當`UnlockBuffer`您完成使用[LockBuffer](#lockbuffer)所傳回的指標之後, 請呼叫。

## <a name="see-also"></a>另請參閱

[MFC 範例 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
