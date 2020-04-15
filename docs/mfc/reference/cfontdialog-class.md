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
ms.openlocfilehash: 6ece239496def9fd65a95a622ac3c475fe5becea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373828"
---
# <a name="cfontdialog-class"></a>CFontDialog 類別

允許您將字型選擇對話方塊合併到應用程式中。

## <a name="syntax"></a>語法

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C方對話::C方對話](#cfontdialog)|建構 `CFontDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFontDialog::Do模態](#domodal)|顯示對話框,並允許用戶進行選擇。|
|[CFontDialog:取得字元格式](#getcharformat)|檢索選取的字型格式。|
|[CFontDialog:取得顏色](#getcolor)|返回所選字體的顏色。|
|[CFontDialog:取得目前的字型](#getcurrentfont)|將當前所選字體的特徵分配給`LOGFONT`結構。|
|[CFontDialog:取得Face名稱](#getfacename)|返回所選字體的面名。|
|[CFontDialog:取得大小](#getsize)|返回所選字體的點大小。|
|[CFontDialog:取得樣式名稱](#getstylename)|返回所選字體的樣式名稱。|
|[CFontDialog:獲得重量](#getweight)|返回所選字體的粗細。|
|[CFontDialog::是](#isbold)|確定字體是否為粗體。|
|[CFontDialog::伊塔利奇](#isitalic)|確定字體是否為斜體。|
|[CFontDialog::是斯特裡克](#isstrikeout)|確定字型是否以刪除方式顯示。|
|[CFontDialog::正則](#isunderline)|確定字體是否帶有下劃線。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFontDialog:m_cf](#m_cf)|定義物件的結構`CFontDialog`。|

## <a name="remarks"></a>備註

對`CFontDialog`像是一個對話框,其中包含系統中當前安裝的字體清單。 用戶可以從清單中選擇特定字體,然後將此選擇報告回應用程式。

要建構`CFontDialog`物件,請使用提供的構造函數或派生新的子類,並使用您自己的自定義構造函數。

建構`CFontDialog`物件後`m_cf`, 可以使用結構在對話框中初始化控制件的值或狀態。 [m_cf](#m_cf)結構為[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)類型。 有關此結構的詳細資訊,請參閱 Windows SDK。

初始化對話框物件的控制項後,調用`DoModal`成員函數以顯示對話方塊並允許使用者選擇字型。 `DoModal`返回使用者是否選擇了"確定 (IDOK)"還是"取消"(IDCANCEL)按鈕。

如果`DoModal`返回 IDOK,則可以使用 『`CFontDialog`的成員 函數之一來檢索用戶輸入的資訊。

您可以使用 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能來確定在對話方塊的初始化過程中是否發生了錯誤,並瞭解有關該錯誤的詳細資訊。 有關此功能的詳細資訊,請參閱 Windows SDK。

`CFontDialog`依賴於 COMMDLG。隨 Windows 版本 3.1 及更高版本一起附帶的 DLL 檔。

要自定義對話框,請從`CFontDialog`派生類,並提供自定義對話框範本,並添加消息映射來處理來自擴展控制項的通知消息。 任何未處理的消息都應傳遞到基類。

不需要自定義挂鉤功能。

有關`CFontDialog`使用的詳細資訊,請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>C方對話::C方對話

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

*plf初始*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)資料結構的指標,允許您設定字體的某些特徵。

*字元格式*<br/>
指向[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)資料結構的指標,允許您在豐富的編輯控制項中設置字體的某些特徵。

*dwFlags*<br/>
指定一或數個 choose-font 旗標。 可以使用位元 OR 運算子來合併一或數個預先設定的值。 如果您修改 `m_cf.Flag` 結構成員，請務必在您的變更中使用位元 OR 運算子，讓預設行為保持不變。 有關每個標誌的詳細資訊,請參閱 Windows SDK 中[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)結構的說明。

*pdcPrinter*<br/>
printer-device 內容的指標。 若有提供，此參數會指向要選取字型之印表機的 printer-device 內容。

*pparentwnd*<br/>
字型對話方塊的父系或擁有者視窗的指標。

### <a name="remarks"></a>備註

請注意，建構函式會自動填入 `CHOOSEFONT` 結構的成員中。 您應該只在想要使用不同於預設值的字型對話方塊時，才變更這些設定。

> [!NOTE]
> 唯有在沒有 Rich Edit 控制項支援的情況下，此函式的第一版才會存在。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::Do模態

呼叫此功能以顯示 Windows 常用字型對話框,並允許使用者選擇字型。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL,請呼叫 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以確定是否發生了錯誤。

IDOK 和 IDCANCEL 是指示使用者選擇"確定"還是"取消"按鈕的常量。

### <a name="remarks"></a>備註

如果要通過設置[m_cf](#m_cf)結構的成員來初始化各種字體對話方塊控制項,則應`DoModal`在調用 之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

### <a name="example"></a>範例

  請參考[CFontDialog 範例:CFontDialog](#cfontdialog)與[CFontDialog:getColor](#getcolor)。

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog:取得字元格式

檢索選取的字型格式。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>參數

*cf*<br/>
包含選取的字型格式資訊的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)結構。

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog:取得顏色

調用此功能以檢索所選字體顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

選取字型的色彩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog:取得目前的字型

呼叫此功能將當前所選字體的特徵分配給[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>參數

*lplf*<br/>
指向結構的`LOGFONT`指標。

### <a name="remarks"></a>備註

提供`CFontDialog`其他成員函數以訪問當前字體的單個特徵。

如果在調用[DoModal](#domodal)期間呼叫此函數,它將返回當前選擇(用戶在對話框中看到或更改的內容)。 如果在調用後調用此函數`DoModal`(僅當返回`DoModal`IDOK 時),它返回用戶實際選擇的內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog:取得Face名稱

調用此功能以檢索所選字體的面名。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>傳回值

對話框中選擇的字體的`CFontDialog`面名。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog:取得大小

調用此函數以檢索所選字體的大小。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

字體的大小,以十分之一點表示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog:取得樣式名稱

調用此函數以檢索所選字體的樣式名稱。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>傳回值

字體的樣式名稱。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog:獲得重量

調用此功能以檢索所選字體的權重。

```
int GetWeight() const;
```

### <a name="return-value"></a>傳回值

所選字體的粗細。

### <a name="remarks"></a>備註

有關字體權重的詳細資訊,請參閱[CFont:::create。](../../mfc/reference/cfont-class.md#createfont)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog::是

調用此函數以確定所選字體是否為粗體。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>傳回值

如果所選字體啟用了粗體特徵,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::伊塔利奇

調用此函數以確定所選字體是否為斜體。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>傳回值

如果所選字體啟用了斜體特徵,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog::是斯特裡克

呼叫此函數以確定所選字體是否顯示帶刪除。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>傳回值

如果所選字體啟用了「罷工」特徵,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog::正則

調用此函數以確定所選字體是否帶下劃線。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>傳回值

如果所選字體啟用了下劃線特徵,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog:m_cf

其成員存儲對話框物件特徵的結構。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>備註

建構`CFontDialog`物件後,可以`m_cf`使用 在`DoModal`調用 成員函數之前修改對話框的各個方面。 有關此結構的詳細資訊,請參閱 Windows SDK 中的[CHOOSEFONT。](/windows/win32/api/commdlg/ns-commdlg-choosefontw)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
