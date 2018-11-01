---
title: CMFCRibbonColorButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca18f54cc38c81e7b78f0afe4d1bba99029404b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057903"
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
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|將色彩群組加入標準色彩區域中。|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|指定是否啟用 [自動]  按鈕。|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|啟用 [其他]  按鈕。|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|傳回目前選取的色彩。|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|傳回色軸顯示的色彩項目大小。|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|傳回目前所選項目在快顯調色盤上的色彩。|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|從標準色彩區域移除所有色彩群組。|
|[CMFCRibbonColorButton::SetColor](#setcolor)|從標準色彩區域選取色彩。|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|設定色軸顯示之所有色彩項目的大小。|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|指定文件色彩區域顯示的 RGB 值清單。|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>備註

當使用者按下它時，功能區色彩按鈕就會顯示色軸。 這個色軸預設包含色彩選取範圍的調色盤，稱為標準色彩區域。 色軸也可以選擇顯示 [自動]  按鈕，讓使用者選取預設的色彩，而 [其他]  按鈕則顯示包含其他色彩的快顯調色盤。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonColorButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonColorButton` 物件、設定大型影像、啟用 [自動]  按鈕、啟用 [其他]  按鈕、設定資料行數目、設定色軸顯示的所有色彩項目大小、將色彩群組加入標準色彩區域中，以及指定文件色彩區域顯示的 RGB 值清單。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxribboncolorbutton.h

##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup

將色彩群組加入標準色彩區域中。

```
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
[in]群組名稱。

*lstColors*<br/>
[in]色彩的清單。

*bContiguousColumns*<br/>
[in]控制色彩項目群組中的顯示方式。 如果為 TRUE，則色彩項目會繪製沒有垂直間距。 如果為 FALSE，色彩項目會繪製以垂直間距。

### <a name="remarks"></a>備註

使用此函式讓色彩的快顯會顯示數個群組的色彩。 您可以控制色彩群組中的顯示方式。

##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton

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
[in]指定當使用者按一下按鈕時要執行此命令的命令識別碼。

*lpszText*<br/>
[in]指定要顯示於按鈕的文字。

*nSmallImageIndex*<br/>
[in]出現在按鈕上的小型影像之以零起始的索引。

*色彩*<br/>
[in]（預設為黑色）] 按鈕的色彩。

*bSimpleButtonLook*<br/>
[in]如果為 TRUE，按鈕是繪製為一個簡單的矩形中。

*nLargeImageIndex*<br/>
[in]要顯示在按鈕上的大型影像的以零起始的索引。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton

指定是否啟用 [自動]  按鈕。

```
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
[in]標籤**自動** 按鈕。

*colorAutomatic*<br/>
[in]RGB 值，指定**自動**按鈕的預設色彩。

*bEnable*<br/>
[in]則為 TRUE**自動**按鈕已啟用;如果已停用，則為 FALSE。

*lpszToolTip*<br/>
[in]工具提示**自動** 按鈕。

*bOnTop*<br/>
[in]指定是否**自動**按鈕位於最上層之前色彩調色盤。

*bDrawBorder*<br/>
[in]如果應用程式功能區色彩按鈕上繪製框線的色彩列，則為 TRUE。 色軸會顯示目前選取的色彩。 如果應用程式不能繪製框線，則為 FALSE。

##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton

啟用 [其他]  按鈕。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
按鈕的標籤。

*lpszToolTip*<br/>
工具提示文字**其他** 按鈕。

### <a name="remarks"></a>備註

**其他**按鈕是顯示的色彩群組下方的按鈕。 當使用者按一下**其他** 按鈕，它會顯示色彩對話方塊。

##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor

擷取目前自動按鈕的色彩。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前的自動按鈕色彩的 RGB 色彩值。

### <a name="remarks"></a>備註

設定自動按鈕的色彩`colorAutomatic`參數傳遞至`CMFCRibbonColorButton::EnableAutomaticButton`方法。

##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor

傳回目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

按一下按鈕選取的色彩。

##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize

傳回色軸顯示的色彩項目大小。

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>傳回值

中的下拉式色彩調色盤的色彩按鈕的大小。

##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns

取得功能區色彩按鈕的組件庫顯示的資料列中的項目數目。

```
int GetColumns() const;
```

### <a name="return-value"></a>傳回值

在每個資料列中傳回圖示的數目。

### <a name="remarks"></a>備註

##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor

在快顯調色盤上傳回目前所選元素的色彩。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>傳回值

在快顯調色盤上的目前選取項目的色彩。

##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups

從標準色彩區域移除所有色彩群組。

```
void RemoveAllColorGroups();
```

##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor

從標準色彩區域選取色彩。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]若要設定色彩。

##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize

設定色軸顯示之所有色彩項目的大小。

```
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>參數

*sizeBox*<br/>
[in]色彩按鈕的色彩調色盤中的新大小。

##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName

設定指定的色彩的新名稱。

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]色彩的 RGB 值。

*strName*<br/>
[in]指定的色彩的的新名稱。

### <a name="remarks"></a>備註

因為它會呼叫`CMFCColorBar::SetColorName`，這個方法會變更在所有指定的色彩名稱`CMFCColorBar`應用程式中的物件。

##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns

設定使用者的色彩選取程序期間呈現給使用者的色彩表中顯示的資料行數目。

```
void SetColumns(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[in]若要在每個資料列中顯示的色彩圖示數目。

### <a name="remarks"></a>備註

##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors

指定文件色彩區域顯示的 RGB 值清單。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]若要使用的文件色彩來顯示文字。

*lstColors*<br/>
[in]參考的 RGB 值清單。

##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette

指定要顯示在 [色彩] 按鈕會顯示色彩表中的標準色彩。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[in]色彩調色盤指標。

### <a name="remarks"></a>備註

##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor

當使用者從顯示使用者按一下 [色彩] 按鈕時，色彩表中選取某種顏色時，由架構呼叫。

```
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]使用者所選取之色彩。

### <a name="remarks"></a>備註

`CMFCRibbonColorButton::UpdateColor`方法變更目前選取之按鈕的色彩，並傳送 WM_COMMAND 訊息 BN_CLICKED 標準通知會告知其父代。 使用[CMFCRibbonColorButton::GetColor](#getcolor)方法來擷取選取的色彩。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)
