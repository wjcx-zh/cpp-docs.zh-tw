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
ms.openlocfilehash: 38fe09b5fdde85dad485e126f6c094196fe68ff4
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176919"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl 類別

`CMFCColorPickerCtrl`類別會提供用來選取色彩的控制項的功能。

## <a name="syntax"></a>語法

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|建構 `CMFCColorPickerCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|擷取使用者選取的色彩。|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|擷取使用者選取之色彩的色調、 亮度和飽和度的值。|
|[CMFCColorPickerCtrl::GetHue](#gethue)|擷取使用者選取的色彩的色調元件。|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|擷取使用者選取的色彩的亮度元件。|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|擷取使用者選取的色彩的飽和度元件。|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|為指定的 RGB 色彩元件或指定的儲存格六邊形所定義的色彩設定目前的色彩。|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|指定的 RGB 色彩值來設定目前的色彩。|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|將目前的色彩設定為指定的 HLS 色彩值。|
|[CMFCColorPickerCtrl::SetHue](#sethue)|變更目前選取之色彩的色調元件。|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|變更目前選取之色彩的亮度元件。|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|色彩選擇器控制項中設定 [亮度] 列的寬度。|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|設定初始選取的色彩。|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|設定目前的色彩調色盤。|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|變更目前選取之色彩的飽和度元件。|
|[CMFCColorPickerCtrl::SetType](#settype)|設定要顯示的色彩選擇器控制項的型別。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|之前顯示的資料指標，指向選取的色彩，由架構呼叫。|

## <a name="remarks"></a>備註

六角色彩調色盤中，選取標準色彩和亮度列中選取自訂色彩，使用 紅/綠/藍標記法或明亮度色調/satuaration 標記法來指定色彩。

下圖說明數個`CMFCColorPickerCtrl`物件。

![CMFCColorPickerCtrl 對話方塊](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl 對話方塊")

`CMFCColorPickerCtrl`支援兩組成對的樣式。 十六進位與 HEX_GREYSCALE 樣式是適用於標準色彩選取範圍。 選擇器和明亮度樣式是適用於自訂色彩選取範圍。

執行下列步驟，以納入`CMFCColorPickerCtrl`控制項到您的對話方塊：

1. 如果您使用**ClassWizard**，您的對話方塊範本中插入新的按鈕控制項 (因為`CMFCColorPickerCtrl`類別繼承自`CButton`類別)。

1. 插入與新的按鈕控制項到您的對話方塊類別相關聯的成員變數。 然後變更 來自變數的型別`CButton`至`CMFCColorPickerCtrl`。

1. 插入`WM_INITDIALOG`對話方塊類別的訊息處理常式。 在處理常式中設定類型、 調色盤和初始選取的色彩`CMFCColorPickerCtrl`控制項。

## <a name="example"></a>範例

下列範例示範如何設定`CMFCColorPickerCtrl`使用中的各種方法的物件`CMFCColorPickerCtrl`類別。 此範例示範如何設定選擇器控制項的類型以及如何設定其色彩、 色調、 亮度及飽和度。 範例是一部分[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcolorpickerctrl.h

##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl

建構 `CMFCColorPickerCtrl` 物件。

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor

之前顯示的資料指標，指向選取的色彩，由架構呼叫。

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rect*<br/>
[in]指定的矩形區域四周選取的色彩。

### <a name="remarks"></a>備註

當您需要將資料指標，指向 所選取之色彩的圖案變更時，請覆寫這個方法。

##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor

擷取使用者選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

所選取之色彩的 RGB 值。

### <a name="remarks"></a>備註

##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS

擷取使用者選取之色彩的色調、 亮度和飽和度的值。

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>參數

*Hue*<br/>
[out]Double，接收 hue 資訊類型的變數的指標。

*亮度*<br/>
[out]Double，接收明亮度資訊類型的變數的指標。

*飽和度*<br/>
[out]Double，接收到的飽和度資訊類型的變數的指標。

### <a name="remarks"></a>備註

##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue

擷取使用者選取的色彩的色調元件。

```
double GetHue() const;
```

### <a name="return-value"></a>傳回值

選取的色彩色調元件。

### <a name="remarks"></a>備註

##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance

擷取使用者選取的色彩的亮度元件。

```
double GetLuminance() const;
```

### <a name="return-value"></a>傳回值

選取的色彩亮度元件。

### <a name="remarks"></a>備註

##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation

擷取使用者選取的色彩的濃度值。

```
double GetSaturation() const;
```

### <a name="return-value"></a>傳回值

選取的色彩飽和度元件。

### <a name="remarks"></a>備註

##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon

為指定的 RGB 色彩元件或指定的儲存格六邊形所定義的色彩設定目前的色彩。

```
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
[in]紅色元件。

*G*<br/>
[in]綠色元件。

*B*<br/>
[in]藍色元件。

*x*<br/>
[in]資料指標，指向儲存格六邊形 x 座標。

*y*<br/>
[in]資料指標，指向儲存格六邊形 y 座標。

### <a name="return-value"></a>傳回值

第二個多載，這個方法一律會傳回 FALSE。

### <a name="remarks"></a>備註

這個方法會設定目前色彩的色彩對應至色彩選取範圍控制項的第一個多載指定紅色、 綠色和藍色色彩元件。

這個方法的第二個多載會依指定的資料指標位置，將目前的色彩設定為指向資料格六邊形的色彩。

##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor

指定的 RGB 色彩值來設定目前的色彩。

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS

將目前的色彩設定為指定的 HLS 色彩值。

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>參數

*Hue*<br/>
[in]色調值。

*亮度*<br/>
[in]亮度值。

*飽和度*<br/>
[in]飽和度值。

*bInvalidate*<br/>
[in]若要強制立即更新至新的色彩; 視窗，則為 TRUE否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue

變更目前選取之色彩的色調。

```
void SetHue(double Hue);
```

### <a name="parameters"></a>參數

*Hue*<br/>
[in]色調值。

### <a name="remarks"></a>備註

##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance

變更目前所選色彩的亮度。

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>參數

*明亮度*<br/>
[in]亮度值。

### <a name="remarks"></a>備註

##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth

色彩選擇器控制項中設定 [亮度] 列的寬度。

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>參數

*w*<br/>
[in]亮度列的寬度，以像素表示。

### <a name="remarks"></a>備註

使用這個方法來調整大小的亮度列中，這位於**自訂** 索引標籤的色彩選擇器控制項。 *w*參數指定 [亮度] 列的新寬度。 如果它超過工作區寬度的四分之三，則會忽略寬度值。

##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor

設定初始選取的色彩。

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>參數

*ref*<br/>
[in]RGB 色彩值。

### <a name="remarks"></a>備註

初始化色彩選擇器控制項時，請呼叫這個方法。

##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette

設定目前的色彩調色盤。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[in]色彩調色盤的指標。

### <a name="remarks"></a>備註

色彩調色盤定義色彩的陣列，會顯示色彩選擇器控制項中。

##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation

變更目前所選色彩的飽和度。

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>參數

*飽和度*<br/>
[in]飽和度值。

### <a name="remarks"></a>備註

##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType

設定要顯示的色彩選擇器控制項的型別。

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>參數

*colorType*<br/>
[in]色彩選擇器控制項型別。

類型由定義`CMFCColorPickerCtrl::COLORTYPE`列舉型別。 可能的類型會是明亮度、 選擇器、 十六進位和 HEX_GREYSCALE。 選擇器預設類型。

### <a name="remarks"></a>備註

若要指定色彩選擇器控制項類型，請建立 Windows 控制項之前呼叫這個方法。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)
