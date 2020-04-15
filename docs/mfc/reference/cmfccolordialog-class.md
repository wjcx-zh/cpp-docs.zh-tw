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
ms.openlocfilehash: 987e4f1e5e89c3c56b58adaad76cfd23d5e26c52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367711"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 類別

類`CMFCColorDialog`表示顏色選擇對話方塊。

## <a name="syntax"></a>語法

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC顏色對話::CMFC顏色對話](#cmfccolordialog)|建構 `CMFCColorDialog` 物件。|
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 顏色對話:取得顏色](#getcolor)|返回當前選取顏色。|
|[CMFCColor對話:取得調色板](#getpalette)|返回調色板。|
|`CMFCColorDialog::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 有關語法和更多資訊,請參閱[CWnd::P重新翻譯消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CDialogEx::PreTranslateMessage`。)|
|[CMFCColor對話::重建調色板](#rebuildpalette)|從系統調色板派生調色板。|
|[CMFC顏色對話::設定當前顏色](#setcurrentcolor)|設置當前所選顏色。|
|[CMFCColor對話::設定新顏色](#setnewcolor)|設定最等效於指定 RGB 值的顏色。|
|[CMFCColor對話::SetpageOne](#setpageone)|為第一個屬性頁選擇 RGB 值。|
|[CMFCColor對話::設定頁面二](#setpagetwo)|為第二個屬性頁選擇 RGB 值。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|`m_bIsMyPalette`|如果顏色選擇對話框使用其自己的調色板,則為 TRUE;如果對話框`CMFCColorDialog`使用 構造函數中指定的調色板,則為 FALSE。|
|`m_bPickerMode`|當使用者從選擇對話框中選擇顏色時為 TRUE;在選擇對話方塊中選擇顏色時為 TRUE;否則,FALSE。|
|`m_btnColorSelect`|用戶選擇的顏色按鈕。|
|`m_CurrentColor`|當前選擇的顏色。|
|`m_hcurPicker`|用於選取顏色的游標。|
|`m_NewColor`|預期選擇的顏色,可以永久選擇或還原到原始顏色。|
|`m_pColourSheetOne`|指向顏色選擇屬性表的第一個屬性頁的指標。|
|`m_pColourSheetTwo`|指向顏色選擇屬性表的第二個屬性頁的指標。|
|`m_pPalette`|當前邏輯調色板。|
|`m_pPropSheet`|指向顏色選擇對話框的屬性表的指標。|
|`m_wndColors`|顏色選取器控制件物件。|
|`m_wndStaticPlaceHolder`|作為顏色選取器屬性表的占位符的靜態控制項。|

## <a name="remarks"></a>備註

顏色選擇對話框顯示為具有兩頁的屬性表。 在第一頁上,您可以從系統調色板中選擇標準顏色;然後,從系統調色板中選擇標準顏色。在第二頁上,您可以選擇自定義顏色。

您可以在堆疊上`CMFCColorDialog`建構物件,然後調`DoModal`用 ,將初始顏色作為參數`CMFCColorDialog`傳遞給 構造函數。 然後,顏色選擇對話框創建多個[CMFCColorPickerCtrl 類](../../mfc/reference/cmfccolorpickerctrl-class.md)物件來處理每個調色板。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCColorDialog`類中的各種方法配置顏色對話方塊。 該示例演示如何設置對話框的當前顏色和新顏色,以及如何在顏色對話框的兩個屬性頁上設置所選顏色的紅色、綠色和藍色分量。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFC顏色對話::CMFC顏色對話

建構 `CMFCColorDialog` 物件。

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>參數

*克利尼特*<br/>
[在]默認顏色選擇。 如果未指定值,則預設值為 RGB(0,0,0)(黑色)。

*dwFlags*<br/>
[in] 保留。

*pparentwnd*<br/>
[在]指向對話框的父視窗或所有者視窗的指標。

*hPal*<br/>
[在]調色板的句柄。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFC 顏色對話:取得顏色

檢索使用者從顏色對話框中選擇的顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

包含顏色對話框中選擇顏色的 RGB 資訊的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

調用`DoModal`方法後調用此函數。

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColor對話:取得調色板

檢索當前顏色對話方塊中可用的調色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

指向`CMFCColorDialog`建構函數`CPalette`中 指定的物件的指標。

### <a name="remarks"></a>備註

調色板指定用戶可以選擇的顏色。

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColor對話::重建調色板

從系統調色板派生調色板。

```
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFC顏色對話::設定當前顏色

設置對話框的當前顏色。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*Rgb*<br/>
[在]RGB 顏色值

### <a name="remarks"></a>備註

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColor對話::設定新顏色

將當前顏色設置為當前調色板中最相似的顏色。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>參數

*Rgb*<br/>
[在]指定 RGB 顏色的[COLORREF。](/windows/win32/gdi/colorref)

### <a name="remarks"></a>備註

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColor對話::SetpageOne

在顏色對話框的第一個屬性頁上顯式指定所選顏色的紅色、綠色和藍色分量。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
[在]指定 RGB 值的紅色元件。

*G*<br/>
[在]指定 RGB 值的綠色元件。

*B*<br/>
[在]指定 RGB 值的藍色元件。

### <a name="remarks"></a>備註

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColor對話::設定頁面二

在顏色對話框的第二個屬性頁上顯式指定所選顏色的紅色、綠色和藍色分量。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*<br/>
[在]指定 RGB 值的紅色元件

*G*<br/>
[在]指定 RGB 值的綠色元件

*B*<br/>
[在]指定 RGB 值的藍色元件

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)
