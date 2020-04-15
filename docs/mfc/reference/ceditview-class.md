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
ms.openlocfilehash: 8fbb2dc569e675ecff4ce04758a4eced40505bf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373974"
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
|[編輯檢視:編輯檢視](#ceditview)|建構類型 `CEditView` 的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[編輯檢視:尋找文字](#findtext)|搜尋文字中的字串。|
|[編輯檢視:抓取緩衝區長度](#getbufferlength)|獲取字元緩衝區的長度。|
|[編輯檢視:抓取編輯](#geteditctrl)|提供對`CEdit``CEditView`物件部分(Windows 編輯控件)的訪問。|
|[編輯檢視::抓取印表機字型](#getprinterfont)|檢索目前印表機字體。|
|[編輯檢視:抓取選取的文字](#getselectedtext)|檢索當前文本選擇。|
|[CEditView:鎖緩衝器](#lockbuffer)|鎖定緩衝區。|
|[CEditView::P林特內斯特](#printinsiderect)|在給定矩形內渲染文本。|
|[CEditView:序列化](#serializeraw)|將`CEditView`物件序列化為原始文本。|
|[編輯檢視::設定印表機字型](#setprinterfont)|設置新的印表機字體。|
|[編輯檢視::設定標籤](#settabstops)|設置螢幕顯示和列印的製表位。|
|[CEditView:解鎖緩衝區](#unlockbuffer)|解鎖緩衝區。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[編輯檢視::在尋找下一個](#onfindnext)|尋找文字字串的下一個符合項。|
|[編輯檢視::全部更換](#onreplaceall)|將給定字串的所有匹配項替換為新字串。|
|[編輯檢視:開啟取代氏](#onreplacesel)|替換當前選擇。|
|[編輯檢視::未找到文字](#ontextnotfound)|當查找操作無法與任何進一步文本匹配時調用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CEditView::dwStyle預設](#dwstyledefault)|類型`CEditView`物件的預設樣式。|

## <a name="remarks"></a>備註

該`CEditView`類別提供以下附加功能:

- 列印。

- 查找和替換。

由於類`CEditView`是`CView`類 的派生`CEditView`,類的物件可以與文檔和文檔範本一起使用。

每個`CEditView`控制項的文本都保存在其自己的全域記憶體物件中。 應用程式可以具有任意數量的`CEditView`物件。

如果需要具有上面列出的`CEditView`添加功能的編輯視窗,或者想要簡單的文本編輯器功能,請創建類型物件。 物件`CEditView`可以佔用視窗的整個工作區。 派生`CEditView`您自己的類,用於添加或修改基本功能,或聲明可添加到文檔範本的類。

類`CEditView`的默認實現處理以下命令:ID_EDIT_SELECT_ALL、ID_EDIT_FIND、ID_EDIT_REPLACE、ID_EDIT_REPEAT 和ID_FILE_PRINT。

的`CEditView`預設字元限制為 (1024 \* 1024 - 1 = 1048575)。 這可以通過調用基礎編輯控件的EM_LIMITTEXT函數來更改。 但是,根據操作系統和編輯控制項的類型(單行或多行)的不同,限制是不同的。 有關這些限制的詳細資訊,請參閱[EM_LIMITTEXT](/windows/win32/Controls/em-limittext)。

若要在控制項中更改此限制,請重寫`OnCreate()``CEditView`類別的函式並插入以下代碼行:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

類型`CEditView`(或派生`CEditView`自的類型)的物件具有以下限制:

- `CEditView`不能實現真實的,你所看到的是你得到的 (WYSIWYG) 編輯。 如果在螢幕上可以選擇可讀性與匹配的列印輸出,`CEditView`則選擇螢幕可讀性。

- `CEditView`只能以一種字體顯示文本。 不支援特殊字元格式。 有關更強大的功能,請參閱類[CRichEditView。](../../mfc/reference/cricheditview-class.md)

- `CEditView`可以包含的文本量是有限的。 限制與`CEdit`控件相同。

有關 的詳細`CEditView`資訊 ,請參閱[MFC 中可用的派生檢視類](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>編輯檢視:編輯檢視

建構類型 `CEditView` 的物件。

```
CEditView();
```

### <a name="remarks"></a>備註

建構物件後,必須先調用[CWnd::創建](../../mfc/reference/cwnd-class.md#create)函數,然後才能使用編輯控制件。 如果派生`CEditView`類並使用 將其添加到`CWinApp::AddDocTemplate`範本 ,則框架將調用此建構`Create`函數和 函數。

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyle預設

包含`CEditView`物件的預設樣式。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>備註

將此靜態成員作為`Create`函數的*dwStyle*`CEditView`參數傳遞, 以獲取物件的預設樣式。

## <a name="ceditviewfindtext"></a><a name="findtext"></a>編輯檢視:尋找文字

調用函數`FindText`以`CEditView`搜索 物件的文本緩衝區。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找到的文本。

*b 下一個*<br/>
指定搜索的方向。 如果為 TRUE,則搜索方向朝向緩衝區的末尾。 如果 FALSE,則搜索方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE,則搜索區分大小寫。 如果 FALSE,則搜索不區分大小寫。

### <a name="return-value"></a>傳回值

如果找到搜索文本,則非零;否則 0。

### <a name="remarks"></a>備註

此函數在緩衝區中搜索*lpszFind*指定的文本,從當前選擇開始,按照*bNext*指定的方向,以及*bCase*指定的區分大小寫。 如果找到文本,它將所選內容設置到找到的文本並返回非零值。 如果未找到文本,則函數返回 0。

通常不需要呼叫 函數`FindText`, 除非您`OnFindNext`重寫`FindText`呼叫 。

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>編輯檢視:抓取緩衝區長度

呼叫此成員函數以獲取編輯控制項緩衝區中當前字元數,不包括空終止符。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>傳回值

緩衝區中字串的長度。

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>編輯檢視:抓取編輯

呼叫`GetEditCtrl`以取得對編輯檢視使用的編輯控制項的引用。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>傳回值

`CEdit` 物件的參考。

### <a name="remarks"></a>備註

此控制項類型為[CEdit](../../mfc/reference/cedit-class.md),因此您可以直接`CEdit`使用成員函數操作 Windows 編輯控制件。

> [!CAUTION]
> 使用物件`CEdit`可以更改基礎 Windows 編輯控制件的狀態。 例如,不應使用[CEdit:SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函數更改選項卡設置`CEditView`,因為快取這些設置以便在編輯控制項和列印中使用。 而是使用[CEditView::設定 TabStop](#settabstops)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>編輯檢視::抓取印表機字型

呼叫`GetPrinterFont`以取得指向描述目前印表機字型的[CFont](../../mfc/reference/cfont-class.md)物件的指標。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>傳回值

指向指定當前印表`CFont`機 字體的對象的指標;如果未設定印表機字型,則為 NULL。 該指標可能是暫時性的，因此不應該儲存供日後使用。

### <a name="remarks"></a>備註

如果未設定印表機字型`CEditView`, 則類的預設列印行為是使用用於顯示的相同字體進行列印。

使用此函數確定當前印表機字型。 如果它不是所需的印表機字體,請使用[CEditView:setPrinterFont](#setprinterfont)來更改它。

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>編輯檢視:抓取選取的文字

呼叫`GetSelectedText`以將選取的文字複製`CString`到物件中,最多到所選內容的末尾或所選內容中第一個回車字元前面的字元。

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>參數

*strResult*<br/>
對要接收所選`CString`文本的物件的引用。

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView:鎖緩衝器

調用此成員函數以獲取指向緩衝區的指標。 不應修改緩衝區。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>傳回值

指向編輯控制件緩衝區的指標。

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>編輯檢視::在尋找下一個

在緩衝區中搜索*lpszFind*指定的文本,按照*bNext*指定的方向搜索文本,由*bCase*指定區分大小寫。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找到的文本。

*b 下一個*<br/>
指定搜索的方向。 如果為 TRUE,則搜索方向朝向緩衝區的末尾。 如果 FALSE,則搜索方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE,則搜索區分大小寫。 如果 FALSE,則搜索不區分大小寫。

### <a name="remarks"></a>備註

搜索從當前選擇的開頭開始,並通過調用[FindText](#findtext)來完成。 在預設的中,`OnFindNext`如果未找到文字,則呼叫[OnTextNot。](#ontextnotfound)

重寫`OnFindNext`以`CEditView`更改 派生物件搜索文本的方式。 `CEditView`當使用者`OnFindNext`在標準「尋找」對話框中選擇「尋找下一步」按鈕時調用。

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>編輯檢視::全部更換

`CEditView`當使用者`OnReplaceAll`在標準"替換"對話框中選擇"全部替換"按鈕時調用。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找到的文本。

*lpsz取代*<br/>
要取代搜尋文字的文字。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE,則搜索區分大小寫。 如果 FALSE,則搜索不區分大小寫。

### <a name="remarks"></a>備註

`OnReplaceAll`在緩衝區中搜索*lpszFind*指定的文本的文本,由*bCase*指定區分大小寫。 搜索從當前選擇的開頭開始。 每次找到搜尋文本時,此函數都會將文本的匹配項替換為*lpszReplace*指定的文本。 搜索是通過調用[FindText](#findtext)來完成的。 在預設實現中,如果未找到文本,則調用[OnTextNotFound。](#ontextnotfound)

如果當前選擇與*lpszFind*不匹配,則所選內容將更新為*lpszFind*指定的文本的第一次出現,並且不執行替換。 這允許使用者確認這是他們想要做的,當選擇與要替換的文本不匹配時。

重寫`OnReplaceAll`以`CEditView`更改 派生對象替換文本的方式。

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>編輯檢視:開啟取代氏

`CEditView`當使用者`OnReplaceSel`在標準"替換"對話框中選擇"替換"按鈕時調用。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找到的文本。

*b 下一個*<br/>
指定搜索的方向。 如果為 TRUE,則搜索方向朝向緩衝區的末尾。 如果 FALSE,則搜索方向朝向緩衝區的開頭。

*bCase*<br/>
指定搜尋是否區分大小寫。 如果為 TRUE,則搜索區分大小寫。 如果 FALSE,則搜索不區分大小寫。

*lpsz取代*<br/>
要取代找到的文字的文字。

### <a name="remarks"></a>備註

替換所選內容後,此函數在緩衝區中搜索文本,以*bNext*指定的方向,按照*bNext*指定的方式,以 bCase 指定的區分大小寫為下一次出現*lpszFind*指定的文本。 搜索是通過調用[FindText](#findtext)來完成的。 如果未找到文本,則調用[OnTextNotFound。](#ontextnotfound)

重寫`OnReplaceSel`以`CEditView`更改 派生物件替換選取的文字的方式。

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>編輯檢視::未找到文字

重寫此函數以更改預設實現,該實現呼叫 Windows`MessageBeep`函數 。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要找到的文本。

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::P林特內斯特

呼叫`PrintInsideRect`以在*rectLayout*指定的矩形中列印文本。

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機設備上下文的指標。

*重新佈局*<br/>
引用[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](/windows/win32/api/windef/ns-windef-rect),指定要在其中呈現文本的矩形。

*nIndex 開始*<br/>
要呈現的第一個字元的緩衝區內的索引。

*nIndexStop*<br/>
在要呈現的最後一個字元之後的字元緩衝區中的索引。

### <a name="return-value"></a>傳回值

要列印的下一個字元的索引(即最後一個字元呈現後的字元)。

### <a name="remarks"></a>備註

如果`CEditView`控制項沒有樣式ES_AUTOHSCROLL,則文本將包在呈現矩形中。 如果控件的樣式ES_AUTOHSCROLL,則文本將剪切在矩形的右邊緣。

`rect.bottom` *rectLayout*物件的元素將發生更改,以便矩形的尺寸定義文本佔用的原始矩形的一部分。

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView:序列化

呼叫`SerializeRaw`以`CArchive`讓 物件讀取或寫入`CEditView`物件中的文字到文字檔。

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
引用儲存序列`CArchive`化文本的物件。

### <a name="remarks"></a>備註

`SerializeRaw`不同於`CEditView`'的內部實現`Serialize`, 因為它唯讀取和寫入文本,沒有前面的物件描述資料。

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>編輯檢視::設定印表機字型

呼叫`SetPrinterFont`以將印表機字型設定為*pFont*指定的字型。

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
指向類型`CFont`物件的指標。 如果為 NULL,則用於列印的字型基於顯示字型。

### <a name="remarks"></a>備註

如果希望檢視始終使用特定字體進行列印,請在類`SetPrinterFont``OnPreparePrinting`的函數中包含調用。 此虛擬函數在列印之前調用,因此在列印檢視內容之前進行字體更改。

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>編輯檢視::設定標籤

呼叫此函數以設置用於顯示和列印的制表位。

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>參數

*NTabStops*<br/>
每個製表符的寬度,以對話框單位表示。

### <a name="remarks"></a>備註

僅支援一個制表位寬度。 (`CEdit`物件支援多個選項卡寬度。寬度以對話方塊單位表示,等於列印或顯示時所用字體的平均字元寬度的四分之一(僅基於大寫字母字元和小寫字母字元)。 不應使用`CEdit::SetTabStops`,`CEditView`因為 必須緩存制表停止值。

此函數僅修改為其調用的對象的選項卡。 要更改應用程式中每個`CEditView`物件的製表位,請調用每個物件`SetTabStops`的 函數。

### <a name="example"></a>範例

此代碼片段通過仔細測量控制項使用的字型,將控制件中的製表元停止設置為每 4 個字元。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView:解鎖緩衝區

調用此成員函數以解鎖緩衝區。

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>備註

使用`UnlockBuffer`[LockBuffer](#lockbuffer)返回的指標完成後調用。

## <a name="see-also"></a>另請參閱

[MFC 樣品 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
