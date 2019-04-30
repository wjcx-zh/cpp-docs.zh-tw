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
ms.openlocfilehash: 1b9f57e46d5ac74dd52f7ddb7ebd90f8888891e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403733"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 類別

`CMFCColorDialog`類別代表色彩選取對話方塊。

## <a name="syntax"></a>語法

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|建構 `CMFCColorDialog` 物件。|
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|傳回目前選取的色彩。|
|[CMFCColorDialog::GetPalette](#getpalette)|傳回的色彩調色盤。|
|`CMFCColorDialog::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需語法和詳細資訊，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CDialogEx::PreTranslateMessage`。)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|自系統調色盤中的調色盤。|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|設定目前選取的色彩。|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|設定最相當於指定的 RGB 值的色彩。|
|[CMFCColorDialog::SetPageOne](#setpageone)|選取第一個屬性頁的 RGB 值。|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|選取第二個屬性頁的 RGB 值。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|`m_bIsMyPalette`|如果色彩選取對話方塊會使用它自己的調色盤，則為 TRUE 或 FALSE 的對話方塊會使用調色盤中指定`CMFCColorDialog`建構函式。|
|`m_bPickerMode`|當使用者從 [選取項目] 對話方塊中，選取色彩，則為 TRUE。否則為 FALSE。|
|`m_btnColorSelect`|使用者選取 [色彩] 按鈕。|
|`m_CurrentColor`|目前選取的色彩。|
|`m_hcurPicker`|資料指標用來選擇色彩。|
|`m_NewColor`|潛在選取的色彩，可以永久選取或已還原成原始的色彩。|
|`m_pColourSheetOne`|色彩選取範圍的屬性工作表的第一個屬性頁面指標。|
|`m_pColourSheetTwo`|色彩選取範圍的屬性工作表的第二個屬性頁面指標。|
|`m_pPalette`|目前的邏輯色板。|
|`m_pPropSheet`|色彩選取對話方塊的屬性工作表指標。|
|`m_wndColors`|色彩選擇器控制項物件。|
|`m_wndStaticPlaceHolder`|靜態控制項，這是一個預留位置，色彩選擇器的屬性工作表。|

## <a name="remarks"></a>備註

色彩選取對話方塊會顯示為兩個頁面的屬性工作表。 您可以在第一個頁面上，選取標準色彩來從系統調色盤;在第二個頁面上，您可以選取自訂色彩。

您可以建構`CMFCColorDialog`物件在堆疊上，然後呼叫`DoModal`，做為參數傳遞的初始色彩`CMFCColorDialog`建構函式。 色彩選取對話方塊接著會建立數個[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)物件來處理每個色彩調色盤。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>範例

下列範例示範如何使用中的各種方法來設定色彩對話方塊`CMFCColorDialog`類別。 此範例示範如何設定目前的和新的色彩的對話方塊中，以及如何在兩個屬性頁的 [色彩] 對話方塊上設定所選取之色彩的紅色、 綠色和藍色元件。 此範例中是屬於[新的控制項範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxcolordialog.h

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

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
[in]預設色彩選取範圍。 如果未不指定任何值，預設會為 RGB(0,0,0) （黑色）。

*dwFlags*<br/>
[in] 保留。

*pParentWnd*<br/>
[in]對話方塊的父代或擁有者視窗的指標。

*hPal*<br/>
[in]色彩調色盤控制代碼。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

擷取使用者從 [色彩] 對話方塊中選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)包含 [色彩] 對話方塊中選取的色彩的 RGB 資訊的值。

### <a name="remarks"></a>備註

呼叫此函式之後您呼叫,`DoModal`方法。

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

擷取在目前的色彩 對話方塊中可用的色彩調色盤。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

指標`CPalette`中所指定的物件`CMFCColorDialog`建構函式。

### <a name="remarks"></a>備註

色彩調色盤中，指定使用者可以選擇的色彩。

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

自系統調色盤中的調色盤。

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor

設定目前的色彩 對話方塊。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*rgb*<br/>
[in]RGB 色彩值

### <a name="remarks"></a>備註

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

目前最相似的調色盤的色彩會設定目前的色彩。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*rgb*<br/>
[in]A [COLORREF](/windows/desktop/gdi/colorref)表示的 RGB 色彩。

### <a name="remarks"></a>備註

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

在 [色彩] 對話方塊的第一個屬性頁面上，明確指定所選取之色彩的紅色、 綠色和藍色元件。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
[in]指定的 RGB 值的紅色元件。

*G*<br/>
[in]指定的 RGB 值的綠色元件。

*B*<br/>
[in]指定的 RGB 值的藍色元件。

### <a name="remarks"></a>備註

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

在 [色彩] 對話方塊的第二個的 [屬性] 頁面上，明確指定所選取之色彩的紅色、 綠色和藍色元件。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
[in]指定 RGB 值的紅色元件

*G*<br/>
[in]指定 RGB 值的綠色元件

*B*<br/>
[in]指定 RGB 值的藍色元件

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)
