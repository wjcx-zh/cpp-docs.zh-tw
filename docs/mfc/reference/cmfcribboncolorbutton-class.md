---
title: CMFCRibbonColorButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754851"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 類別

`CMFCRibbonColorButton` 類別實作可以加入功能區列中的色彩按鈕。 功能區色彩按鈕會顯示包含一個或多個色板的下拉式功能表。

## <a name="syntax"></a>語法

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC彩帶顏色按鈕::添加顏色組](#addcolorsgroup)|將色彩群組加入標準色彩區域中。|
|[CMFC功能彩帶按鈕::啟用自動按鈕](#enableautomaticbutton)|指定是否啟用 [自動] **** 按鈕。|
|[CMFC功能彩帶按鈕::啟用其他按鈕](#enableotherbutton)|啟用 [其他] **** 按鈕。|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFC 彩帶顏色按鈕:取得顏色](#getcolor)|傳回目前選取的色彩。|
|[CMFC功能彩帶按鈕:取得ColorBox大小](#getcolorboxsize)|傳回色軸顯示的色彩項目大小。|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFC彩帶顏色按鈕::取得突出顯示的顏色](#gethighlightedcolor)|傳回目前所選項目在快顯調色盤上的色彩。|
|[CMFC彩帶顏色按鈕::刪除所有顏色組](#removeallcolorgroups)|從標準色彩區域移除所有色彩群組。|
|[CMFC彩帶顏色按鈕::設定顏色](#setcolor)|從標準色彩區域選取色彩。|
|[CMFC功能彩帶顏色按鈕::設定彩色框大小](#setcolorboxsize)|設定色軸顯示之所有色彩項目的大小。|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFC功能彩帶顏色按鈕::設定文檔顏色](#setdocumentcolors)|指定文件色彩區域顯示的 RGB 值清單。|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>備註

當使用者按下它時，功能區色彩按鈕就會顯示色軸。 這個色軸預設包含色彩選取範圍的調色盤，稱為標準色彩區域。 色軸也可以選擇顯示 [自動] **** 按鈕，讓使用者選取預設的色彩，而 [其他] **** 按鈕則顯示包含其他色彩的快顯調色盤。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonColorButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonColorButton` 物件、設定大型影像、啟用 [自動] **** 按鈕、啟用 [其他] **** 按鈕、設定資料行數目、設定色軸顯示的所有色彩項目大小、將色彩群組加入標準色彩區域中，以及指定文件色彩區域顯示的 RGB 值清單。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFC彩帶顏色按鈕::添加顏色組

將色彩群組加入標準色彩區域中。

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
[在]組名稱。

*lstColors*<br/>
[在]顏色清單。

*b 連續列*<br/>
[在]控制顏色項在組中的顯示方式。 如果為 TRUE,則繪製顏色項目時沒有垂直間距。 如果 FALSE,則使用垂直間距繪製顏色項。

### <a name="remarks"></a>備註

使用此函數可以使顏色彈出視窗顯示多組顏色。 您可以控制顏色在組中的顯示方式。

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFC彩帶顏色按鈕::CMFC彩帶顏色按鈕

建構 `CMFCRibbonColorButton` 物件。

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]指定在使用者按下按鈕時要執行的命令 ID。

*lpszText*<br/>
[在]指定要顯示在按鈕上的文字。

*n 小圖像索引*<br/>
[在]要顯示在按鈕上的小圖像的零基索引。

*顏色*<br/>
[在]按鈕的顏色(預設為黑色)。

*b 簡單按鈕外觀*<br/>
[在]如果為 TRUE,則該按鈕將作為一個簡單的矩形繪製。

*nLargeImageIndex*<br/>
[在]要顯示在按鈕上的大圖像的零基索引。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC功能彩帶按鈕::啟用自動按鈕

指定是否啟用 [自動] **** 按鈕。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]**「自動」** 按鈕的標籤。

*顏色 自動*<br/>
[在]指定 **「自動**」按鈕預設顏色的 RGB 值。

*b 啟用*<br/>
[在]如果啟用了"自動"按鈕,則為 TRUE;如果啟用了 **"自動"** 按鈕,則為 TRUE。如果禁用,則 FALSE。

*lpszToolTip*<br/>
[在]**「自動」** 按鈕的工具提示。

*蓬托普*<br/>
[在]指定 **「自動」** 按鈕是否位於調色板之前的頂部。

*bDraw邊框*<br/>
[在]如果應用程式在色帶顏色按鈕的顏色欄周圍繪製邊框,則為 TRUE。 顏色列顯示目前選擇的顏色。 如果應用程式未繪製邊框,則 FALSE

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC功能彩帶按鈕::啟用其他按鈕

啟用 [其他] **** 按鈕。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
按鈕的標籤。

*lpszToolTip*<br/>
**"其他**"按鈕的工具提示文字。

### <a name="remarks"></a>備註

「**其他**」按鈕是顯示在顏色組下方的按鈕。 當用戶按下 **「其他**」按鈕時,將顯示顏色對話方塊。

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFC 彩帶顏色按鈕:取得自動顏色

檢索目前自動按鈕顏色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示當前自動按鈕顏色的 RGB 顏色值。

### <a name="remarks"></a>備註

自動按鈕顏色由傳遞給方法的`colorAutomatic``CMFCRibbonColorButton::EnableAutomaticButton`參數設置。

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFC 彩帶顏色按鈕:取得顏色

傳回目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

按下按鈕選擇的顏色。

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFC功能彩帶按鈕:取得ColorBox大小

傳回色軸顯示的色彩項目大小。

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>傳回值

下拉調色板中顏色按鈕的大小。

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFC功能彩帶按鈕::獲取列

取得功能區顏色按鈕的庫顯示的行中的項目數。

```
int GetColumns() const;
```

### <a name="return-value"></a>傳回值

返回每行中的圖示數。

### <a name="remarks"></a>備註

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFC彩帶顏色按鈕::取得突出顯示的顏色

返回彈出式調色板上當前選定元素的顏色。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>傳回值

彈出式調色板上當前選定元素的顏色。

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFC彩帶顏色按鈕::刪除所有顏色組

從標準色彩區域移除所有色彩群組。

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFC彩帶顏色按鈕::設定顏色

從標準色彩區域選取色彩。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]要設置的顏色。

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFC功能彩帶顏色按鈕::設定彩色框大小

設定色軸顯示之所有色彩項目的大小。

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>參數

*大小盒*<br/>
[在]調色板中顏色按鈕的新大小。

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFC彩帶顏色按鈕::設定顏色名稱

為指定顏色設置新名稱。

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]顏色的 RGB 值。

*strName*<br/>
[在]指定顏色的新名稱。

### <a name="remarks"></a>備註

因為它調用`CMFCColorBar::SetColorName`,此方法更改應用程式中`CMFCColorBar`所有 物件中指定顏色的名稱。

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFC 功能色按鈕::設定欄

設置在使用者顏色選擇過程中向使用者顯示的顏色表中顯示的列數。

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[在]每行中顯示的顏色圖示數。

### <a name="remarks"></a>備註

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFC功能彩帶顏色按鈕::設定文檔顏色

指定文件色彩區域顯示的 RGB 值清單。

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]要與文件顏色一起顯示的文本。

*lstColors*<br/>
[在]對 RGB 值清單的引用。

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFC功能彩帶按鈕::設定調色板

指定在顏色按鈕顯示的顏色表中顯示的標準顏色。

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[在]指向調色板的指標。

### <a name="remarks"></a>備註

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFC彩帶顏色按鈕::更新顏色

當使用者從使用者按下顏色按鈕時顯示的顏色表中選擇顏色時,由框架調用。

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]使用者選擇的顏色。

### <a name="remarks"></a>備註

該方法`CMFCRibbonColorButton::UpdateColor`更改當前所選按鈕的顏色,並通過發送帶有BN_CLICKED標準通知的WM_COMMAND消息通知其父按鈕。 使用[CMFC 功能色按鈕:獲取顏色](#getcolor)方法檢索所選顏色。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)
