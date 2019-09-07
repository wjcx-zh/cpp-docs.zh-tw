---
title: CFontDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: c0d0c37d055d9b337f7b709b4ee3d299daae7658
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741548"
---
# <a name="cfontdialog-class"></a>CFontDialog 類別

可讓您在應用程式中併入字型選取範圍對話方塊。

## <a name="syntax"></a>語法

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|建構 `CFontDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|
|[CFontDialog::GetCharFormat](#getcharformat)|抓取選取之字型的字元格式。|
|[CFontDialog::GetColor](#getcolor)|傳回選取之字型的色彩。|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|將目前選取之字型的特性指派至`LOGFONT`結構。|
|[CFontDialog::GetFaceName](#getfacename)|傳回所選字型的臉部名稱。|
|[CFontDialog::GetSize](#getsize)|傳回選取之字型的點大小。|
|[CFontDialog::GetStyleName](#getstylename)|傳回選取之字型的樣式名稱。|
|[CFontDialog::GetWeight](#getweight)|傳回選取之字型的權數。|
|[CFontDialog::IsBold](#isbold)|判斷字型是否為粗體。|
|[CFontDialog::IsItalic](#isitalic)|判斷字型是否為斜體。|
|[CFontDialog::IsStrikeOut](#isstrikeout)|決定字型是否以刪除線顯示。|
|[CFontDialog::IsUnderline](#isunderline)|決定字型是否加上底線。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|用來自訂`CFontDialog`物件的結構。|

## <a name="remarks"></a>備註

「 `CFontDialog`物件」是一個對話方塊，其中包含目前安裝在系統中的字型清單。 使用者可以從清單中選取特定的字型，然後將此選項回報給應用程式。

若要建立`CFontDialog`物件，請使用所提供的函式，或衍生新的子類別，並使用您自己的自訂函式。

一旦建立`CFontDialog`物件之後，您就可以`m_cf`使用結構來初始化對話方塊中控制項的值或狀態。 [M_cf](#m_cf)結構的類型為[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)。 如需此結構的詳細資訊，請參閱 Windows SDK。

初始化對話方塊物件的控制項之後，呼叫`DoModal`成員函式以顯示對話方塊，並允許使用者選取字型。 `DoModal`傳回使用者是否選取 [確定] （IDOK）或 [取消] （IDCANCEL）按鈕。

如果`DoModal`傳回 IDOK，您可以使用`CFontDialog`的其中一個成員函式來取出使用者輸入的資訊。

您可以使用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷對話方塊初始化期間是否發生錯誤，並深入瞭解錯誤。 如需此函數的詳細資訊，請參閱 Windows SDK。

`CFontDialog`依賴 COMMDLG。Windows 3.1 和更新版本隨附的 DLL 檔案。

若要自訂對話方塊、從`CFontDialog`衍生類別，請提供自訂對話方塊範本，並加入訊息對應以處理來自擴充控制項的通知訊息。 任何未處理的訊息都應該傳遞至基類。

不需要自訂攔截函數。

如需使用`CFontDialog`的詳細資訊，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

##  <a name="cfontdialog"></a>CFontDialog::CFontDialog

建構 `CFontDialog` 物件。

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*plfInitial*<br/>
[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)資料結構的指標，可讓您設定部分字型的特性。

*charFormat*<br/>
[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)資料結構的指標，可讓您在 rich edit 控制項中設定部分字型的特性。

*dwFlags*<br/>
指定一或數個 choose-font 旗標。 可以使用位元 OR 運算子來合併一或數個預先設定的值。 如果您修改 `m_cf.Flag` 結構成員，請務必在您的變更中使用位元 OR 運算子，讓預設行為保持不變。 如需每個旗標的詳細資訊，請參閱 Windows SDK 中的[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)結構描述。

*pdcPrinter*<br/>
printer-device 內容的指標。 若有提供，此參數會指向要選取字型之印表機的 printer-device 內容。

*pParentWnd*<br/>
字型對話方塊的父系或擁有者視窗的指標。

### <a name="remarks"></a>備註

請注意，建構函式會自動填入 `CHOOSEFONT` 結構的成員中。 您應該只在想要使用不同於預設值的字型對話方塊時，才變更這些設定。

> [!NOTE]
>  唯有在沒有 Rich Edit 控制項支援的情況下，此函式的第一版才會存在。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>CFontDialog：:D oModal

呼叫此函式以顯示 [Windows 通用字型] 對話方塊，並允許使用者選擇字型。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，請呼叫 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函數來判斷是否發生錯誤。

IDOK 和 IDCANCEL 是常數，指出使用者是否選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_cf](#m_cf)結構的成員來初始化各種字型對話方塊控制項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

### <a name="example"></a>範例

  請參閱[CFontDialog：： CFontDialog](#cfontdialog)和[CFontDialog：： GetColor](#getcolor)的範例。

##  <a name="getcharformat"></a>CFontDialog::GetCharFormat

抓取選取之字型的字元格式。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>參數

*cf*<br/>
[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)結構，其中包含所選字型之字元格式的相關資訊。

##  <a name="getcolor"></a>CFontDialog：： GetColor

呼叫此函式可取得選取的字型色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

選取字型的色彩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

呼叫此函式可將目前選取之字型的特性指派給[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>參數

*lplf*<br/>
`LOGFONT`結構的指標。

### <a name="remarks"></a>備註

提供`CFontDialog`其他成員函式來存取目前字型的個別特性。

如果在呼叫[DoModal](#domodal)期間呼叫此函式，它會傳回目前的選取範圍（使用者在對話方塊中看到或變更的內容）。 如果在呼叫`DoModal`之後呼叫此函式（僅在傳回`DoModal` IDOK 時），則會傳回使用者實際選取的內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>CFontDialog::GetFaceName

呼叫此函式可抓取所選字型的臉部名稱。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>傳回值

在`CFontDialog`對話方塊中選取之字型的臉部名稱。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>CFontDialog：： GetSize

呼叫此函式可取得所選字型的大小。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

字型的大小，以十分之一為點。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>CFontDialog::GetStyleName

呼叫此函式可抓取所選字型的樣式名稱。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>傳回值

字型的樣式名稱。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>CFontDialog::GetWeight

呼叫此函式可取得所選字型的權數。

```
int GetWeight() const;
```

### <a name="return-value"></a>傳回值

選取之字型的權數。

### <a name="remarks"></a>備註

如需字型權數的詳細資訊，請參閱[CFont：： CreateFont](../../mfc/reference/cfont-class.md#createfont)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>CFontDialog::IsBold

呼叫此函式可判斷選取的字型是否為粗體。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>傳回值

如果選取的字型已啟用粗體特性，則為非零。否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>CFontDialog::IsItalic

呼叫此函式可判斷選取的字型是否為斜體。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>傳回值

如果選取的字型已啟用斜體特性，則為非零。否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>CFontDialog::IsStrikeOut

呼叫此函式可判斷選取的字型是否以刪除線顯示。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>傳回值

如果選取的字型已啟用刪除線特性，則為非零值;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>CFontDialog::IsUnderline

呼叫此函式可判斷選取的字型是否已加上底線。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>傳回值

如果選取的字型已啟用底線特性，則為非零值;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

結構，其成員會儲存對話方塊物件的特性。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>備註

在建立`CFontDialog`物件之後，您可以使用`m_cf`來修改`DoModal`對話方塊的各個層面，然後再呼叫成員函式。 如需此結構的詳細資訊，請參閱 Windows SDK 中的[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
