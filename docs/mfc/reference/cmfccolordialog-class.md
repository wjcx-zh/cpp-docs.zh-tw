---
title: CMFCColorDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505332"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 類別

`CMFCColorDialog`類別表示色彩選取對話方塊。

## <a name="syntax"></a>語法

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|建構 `CMFCColorDialog` 物件。|
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|傳回目前選取的色彩。|
|[CMFCColorDialog::GetPalette](#getpalette)|傳回色彩的調色板。|
|`CMFCColorDialog::PreTranslateMessage`|會先轉譯視窗訊息, 再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需語法和詳細資訊, 請參閱[CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CDialogEx::PreTranslateMessage`。)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|從系統調色板衍生調色板。|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|設定目前選取的色彩。|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|將色彩設定為與指定的 RGB 值最相等。|
|[CMFCColorDialog::SetPageOne](#setpageone)|選取第一個屬性頁的 RGB 值。|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|選取第二個屬性頁的 RGB 值。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|說明|
|----------|-----------------|
|`m_bIsMyPalette`|如果色彩選取對話方塊使用自己的調色板, 則為 TRUE, 如果對話方塊使用在此`CMFCColorDialog`函式中指定的調色板, 則為 FALSE。|
|`m_bPickerMode`|當使用者從 [選取範圍] 對話方塊中選取色彩時, 即為 TRUE;否則為 FALSE。|
|`m_btnColorSelect`|使用者已選取的色彩按鈕。|
|`m_CurrentColor`|目前選取的色彩。|
|`m_hcurPicker`|用來挑選色彩的游標。|
|`m_NewColor`|預期的選取色彩, 可以永久選取或還原為原始色彩。|
|`m_pColourSheetOne`|色彩選取屬性工作表之第一個屬性頁的指標。|
|`m_pColourSheetTwo`|色彩選取屬性工作表之第二個屬性頁的指標。|
|`m_pPalette`|目前的邏輯調色板。|
|`m_pPropSheet`|色彩選取對話方塊之屬性工作表的指標。|
|`m_wndColors`|色彩選擇器控制項物件。|
|`m_wndStaticPlaceHolder`|靜態控制項, 這是色彩選擇器屬性工作表的預留位置。|

## <a name="remarks"></a>備註

[色彩選取] 對話方塊會顯示為具有兩個頁面的屬性工作表。 在第一頁上, 您可以從系統元件中選取標準色彩;在第二個頁面上, 您可以選取自訂色彩。

您可以在堆疊`CMFCColorDialog`上建立物件, 然後呼叫`DoModal`, 並將初始色彩當做參數傳遞給此`CMFCColorDialog`函式。 [色彩選取] 對話方塊接著會建立數個[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)物件來處理每個調色板。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>範例

下列範例示範如何使用`CMFCColorDialog`類別中的各種方法來設定色彩對話方塊。 此範例示範如何設定對話方塊的目前和新色彩, 以及如何在 [色彩] 對話方塊的兩個屬性頁上, 設定所選色彩的紅色、綠色和藍色元件。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭:** afxcolordialog。h

##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

建構 `CMFCColorDialog` 物件。

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>參數

*clrInit*<br/>
在預設色彩選取範圍。 如果未指定任何值, 則預設值為 RGB (0, 0, 0) (黑色)。

*dwFlags*<br/>
[in] 保留。

*pParentWnd*<br/>
在對話方塊的父代或擁有者視窗的指標。

*hPal*<br/>
在色調色板的控制碼。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getcolor"></a>CMFCColorDialog:: GetColor

抓取使用者從 [色彩] 對話方塊中選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值, 其中包含 [色彩] 對話方塊中所選取之色彩的 RGB 資訊。

### <a name="remarks"></a>備註

呼叫`DoModal`方法之後, 請呼叫此函式。

##  <a name="getpalette"></a>CMFCColorDialog::GetPalette

抓取目前色彩對話方塊中可用的調色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

在此`CPalette` `CMFCColorDialog`函數中指定之物件的指標。

### <a name="remarks"></a>備註

色調色板會指定使用者可以選擇的色彩。

##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

從系統調色板衍生調色板。

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

設定對話方塊的目前色彩。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*rgb*<br/>
在RGB 色彩值

### <a name="remarks"></a>備註

##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

將目前的色彩設定為目前調色板中最類似的色彩。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*rgb*<br/>
在指定 RGB 色彩的[COLORREF](/windows/win32/gdi/colorref) 。

### <a name="remarks"></a>備註

##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne

在色彩對話方塊的第一個屬性頁上, 明確地指定所選色彩的紅色、綠色和藍色元件。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
在指定 RGB 值的紅色元件。

*G*<br/>
在指定 RGB 值的綠色元件。

*B*<br/>
在指定 RGB 值的藍色元件。

### <a name="remarks"></a>備註

##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

在色彩對話方塊的第二個屬性頁上, 明確指定所選色彩的紅色、綠色和藍色元件。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
在指定 RGB 值的紅色元件

*G*<br/>
在指定 RGB 值的綠色元件

*B*<br/>
在指定 RGB 值的藍色元件

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)
