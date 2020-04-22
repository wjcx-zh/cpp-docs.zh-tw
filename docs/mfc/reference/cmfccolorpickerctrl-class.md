---
title: CMFCColorPickerCtrl 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: fe35ee5d6fc6484788a2636151c386689f4bdd96
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752531"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl 類別

類`CMFCColorPickerCtrl`為用於選擇顏色的控制項提供功能。

## <a name="syntax"></a>語法

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC顏色挑選器::CMFC顏色挑選器](#cmfccolorpickerctrl)|建構 `CMFCColorPickerCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC顏色挑選器::取得顏色](#getcolor)|檢索用戶選擇的顏色。|
|[CMFC顏色挑選器::GetHLS](#gethls)|檢索使用者選擇的顏色的色調、亮度和飽和度值。|
|[CMFC顏色挑選器::GetHue](#gethue)|檢索用戶選擇的顏色的色調元件。|
|[CMFC顏色挑選器::取得亮度](#getluminance)|檢索使用者選擇的顏色的亮度元件。|
|[CMFC顏色挑選器::取得飽和度](#getsaturation)|檢索用戶選擇的顏色的飽和度分量。|
|[CMFC顏色挑選器::選擇CellHexagon](#selectcellhexagon)|將當前顏色設置為指定 RGB 顏色分量或指定儲存格六邊形定義的顏色。|
|[CMFC 顏色挑選器::設定顏色](#setcolor)|將當前顏色設置為指定的 RGB 顏色值。|
|[CMFC顏色挑選器::SetHLS](#sethls)|將目前的顏色設定為指定的 HLS 顏色值。|
|[CMFC顏色挑選器::SetHue](#sethue)|更改目前選取顏色的色調分量。|
|[CMFC 顏色挑選器::設定亮度](#setluminance)|更改目前選取的顏色的亮度分量。|
|[CMFC顏色挑選器::設定亮度條寬](#setluminancebarwidth)|設置顏色選取器控制項線亮度條的寬度。|
|[CMFC 顏色選擇器Ctrl:設定原始顏色](#setoriginalcolor)|設置初始所選顏色。|
|[CMFC顏色挑選器::設定調色板](#setpalette)|設置當前調色板。|
|[CMFC顏色挑選器::設定飽和度](#setsaturation)|更改目前選取顏色的飽和度分量。|
|[CMFC 顏色挑選器::設定類型](#settype)|設置要顯示的顏色選取器控制項的類型。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC顏色挑選器::D生游標](#drawcursor)|顯示指向所選顏色的游標之前由框架呼叫。|

## <a name="remarks"></a>備註

標準顏色是從六邊形調色板中選擇的,自定義顏色是從亮度條中選擇的,其中使用紅色/綠色/藍色表示法或色調/色度/亮度表示法指定顏色。

下圖描述了多個`CMFCColorPickerCtrl`物件。

![CMFCColorPickerCtrl 對話方塊](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl 對話方塊")

支援`CMFCColorPickerCtrl`兩對樣式。 HEX 和 HEX_GREYSCALE 樣式適用於標準顏色選擇。 PICKER 和 LUMINANCE 樣式適用於自定義顏色選擇。

執行以下步驟將`CMFCColorPickerCtrl`控制器合併到對話框中:

1. 如果使用**ClassWizard,** 請在對話方塊樣本中插入新的按鈕控制項`CMFCColorPickerCtrl`(因為類別是從類繼承的`CButton`)。

1. 將與新按鈕控制項關聯的成員變數插入到對話方塊類中。 然後將變數型態從`CButton`變更為`CMFCColorPickerCtrl`。

1. 插入`WM_INITDIALOG`對話方塊類的消息處理程式。 在處理程式中,設置`CMFCColorPickerCtrl`控制項的類型、調色板和初始選擇顏色。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCColorPickerCtrl``CMFCColorPickerCtrl`類中的各種方法配置物件。 該示例演示如何設置選取器控制項的類型,以及如何設置其顏色、色調、亮度和飽和度。 該示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFC顏色挑選器::CMFC顏色挑選器

建構 `CMFCColorPickerCtrl` 物件。

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFC顏色挑選器::D生游標

顯示指向所選顏色的游標之前由框架呼叫。

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]指定所選顏色周圍的矩形區域。

### <a name="remarks"></a>備註

當您需要更改指向所選顏色的游標的形狀時,將重寫此方法。

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFC顏色挑選器::取得顏色

檢索用戶選擇的顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

所選顏色的 RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFC顏色挑選器::GetHLS

檢索使用者選擇的顏色的色調、亮度和飽和度值。

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>參數

*色調*<br/>
[出]指向接收色調資訊的雙型變數的指標。

*亮度*<br/>
[出]指向接收亮度資訊的雙型變數的指標。

*飽和*<br/>
[出]指向接收飽和度資訊的雙型變數的指標。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFC顏色挑選器::GetHue

檢索用戶選擇的顏色的色調元件。

```
double GetHue() const;
```

### <a name="return-value"></a>傳回值

所選顏色的色調分量。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFC顏色挑選器::取得亮度

檢索使用者選擇的顏色的亮度元件。

```
double GetLuminance() const;
```

### <a name="return-value"></a>傳回值

所選顏色的亮度分量。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFC顏色挑選器::取得飽和度

檢索用戶選擇的顏色的飽和度值。

```
double GetSaturation() const;
```

### <a name="return-value"></a>傳回值

所選顏色的飽和度分量。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFC顏色挑選器::選擇CellHexagon

將當前顏色設置為指定 RGB 顏色分量或指定儲存格六邊形定義的顏色。

```cpp
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>參數

*R*<br/>
[在]紅色元件。

*G*<br/>
[在]綠色元件。

*B*<br/>
[在]藍色元件。

*x*<br/>
[在]游標的 x 座標,它指向單元格六邊形。

*Y*<br/>
[在]游標的 y 座標,它指向單元格六邊形。

### <a name="return-value"></a>傳回值

此方法的第二個重載始終返回 FALSE。

### <a name="remarks"></a>備註

此方法的第一個重載將當前顏色設置為對應於顏色選擇控制項指定的紅色、綠色和藍色分量的顏色。

此方法的第二個重載將當前顏色設置為由指定的游標位置指向的單元格六邊形的顏色。

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFC 顏色挑選器::設定顏色

將當前顏色設置為指定的 RGB 顏色值。

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>參數

*Color*<br/>
[在]RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFC顏色挑選器::SetHLS

將目前的顏色設定為指定的 HLS 顏色值。

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>參數

*色調*<br/>
[在]色調值。

*亮度*<br/>
[在]亮度值。

*飽和*<br/>
[在]飽和度值。

*b 無效*<br/>
[在]TRUE 強制視窗立即更新到新顏色;否則,FALSE。 預設值是 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFC顏色挑選器::SetHue

更改當前選取顏色的色調。

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>參數

*Hue*<br/>
[在]色調值。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFC 顏色挑選器::設定亮度

更改目前選取的顏色的亮度。

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>參數

*明亮度*<br/>
[在]亮度值。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFC顏色挑選器::設定亮度條寬

設置顏色選取器控制項線亮度條的寬度。

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>參數

*w*<br/>
[在]以像素為單位的亮度條的寬度。

### <a name="remarks"></a>備註

使用此方法可以調整亮度條的大小,亮度條位於顏色選取器控制項的 **「自訂」** 選項卡上。 *w*參數指定亮度條的新寬度。 如果寬度值超過工作區寬度的四分之三,則忽略該值。

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFC 顏色選擇器Ctrl:設定原始顏色

設置初始所選顏色。

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>參數

*ref*<br/>
[在]RGB 顏色值。

### <a name="remarks"></a>備註

在顏色選取器控制程式初始化時呼叫此方法。

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFC顏色挑選器::設定調色板

設置當前調色板。

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[在]指向調色板的指標。

### <a name="remarks"></a>備註

調色板定義顏色選取器控制項中顯示的顏色陣列。

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFC顏色挑選器::設定飽和度

更改當前選取顏色的飽和度。

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>參數

*飽和度*<br/>
[在]飽和度值。

### <a name="remarks"></a>備註

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFC 顏色挑選器::設定類型

設置要顯示的顏色選取器控制項的類型。

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>參數

*色彩類型*<br/>
[在]顏色選取器控制項類型。

類型由`CMFCColorPickerCtrl::COLORTYPE`枚舉定義。 可能的類型包括亮度、拾取器、HEX 和HEX_GREYSCALE。 默認類型為"選取器"

### <a name="remarks"></a>備註

要指定顏色選取器控制項類型,請在創建 Windows 控制件之前呼叫此方法。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)
