---
title: CMFCPropertyGridColorProperty 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 393a871a881aa4bddd786b1d4333e02d5e0dbef1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751836"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty 類別

`CMFCPropertyGridColorProperty` 類別支援開啟色彩選取對話方塊的屬性清單控制項項目。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|建構 `CMFCPropertyGridColorProperty` 物件。|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|啟用顏色選擇對話框上的*自動*按鈕。 ( 標準自動按鈕標記為**自動**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|啟用顏色選擇對話框上*的另一個*按鈕。 ( 標準其他按鈕標記為**更多顏色**。|
|`CMFCPropertyGridColorProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[CMFC 屬性網格屬性::格式屬性](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|取得屬性的目前色彩。|
|`CMFCPropertyGridColorProperty::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyGridColorProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[CMFC 屬性網格屬性::按一下按鈕](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|由架構呼叫以顯示屬性值。 (覆蓋[CMFC 屬性網格屬性::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|使用者即將修改屬性值時由架構呼叫。 (覆寫[CMFC 屬性網格屬性::開啟編輯](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|當可編輯屬性的值變更時由架構呼叫。 (覆寫[CMFC 屬性網格屬性::更新值](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|設定屬性的新色彩。|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|指定目前色彩屬性格線中的資料行數目。|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|設定可編輯屬性的原始值。|

## <a name="remarks"></a>備註

`CMFCPropertyGridColorProperty` 類別支援的色彩屬性可以加入至屬性清單控制項。 有關詳細資訊,請參閱[CMFC 財產網格Ctrl 類](../../mfc/reference/cmfcpropertygridctrl-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCPropertyGridColorProperty` 類別的物件，以及使用 `CMFCPropertyGridColorProperty` 類別的各種方法來設定此物件。 程式碼說明如何啟用自動和其他按鈕，以及如何設定色彩和資料行數目。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>需求

**標題:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFC 屬性網格顏色屬性:CMFC財產網格顏色屬性

建構 `CMFCPropertyGridColorProperty` 物件。

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>參數

*strName*<br/>
[在]屬性的名稱。

*顏色*<br/>
[在]屬性的顏色值。

*pPalette*<br/>
[在]指向顏色調色板的指標。 預設值是 NULL。

*lpszDescr*<br/>
[在]屬性描述。 預設值是 NULL。

*dwData*<br/>
[在]特定於應用程式的數據,例如整數或指向與屬性關聯的其他數據的指標。 預設值為 0。

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC 屬性網格顏色屬性::啟用自動按鈕

啟用顏色選擇對話框上的*自動*按鈕。 ( 標準自動按鈕標記為**自動**.)

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]自動按鈕的標籤文本。

*顏色 自動*<br/>
[在]自動(預設)顏色的 RGB 顏色值。

*b 啟用*<br/>
[在]TRUE 啟用自動按鈕;否則,FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFC 屬性網格顏色屬性::啟用其他按鈕

啟用顏色選擇對話框上*的另一個*按鈕。 ( 標準其他按鈕標記為**更多顏色**。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]另一個按鈕的標籤文本。

*巴爾特·博拉爾德格*<br/>
[在]TRUE 以`CMFCColorDialog`顯示 對話方塊;FALSE 以顯示標準顏色選擇對話框。 預設值為 TRUE。

*b 啟用*<br/>
[在]TRUE 以顯示其他按鈕;否則,FALSE。  預設值為 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFC 屬性網格顏色屬性:取得顏色

取得屬性的目前色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFC 屬性網格顏色屬性::設定顏色

設定屬性的新色彩。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFC 屬性網格顏色屬性::設定欄數

指定目前色彩屬性格線中的資料行數目。

```cpp
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>參數

*n 欄位*<br/>
[在]顏色屬性網格中的首選列數。

### <a name="remarks"></a>備註

此方法設置`m_nColumnsNumber`受保護數據成員的值。

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFC 屬性網格顏色屬性::設定原始值

設定可編輯屬性的原始值。

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*varValue*<br/>
[在]值。

### <a name="remarks"></a>備註

使用[CMFC 屬性網格屬性:重置原始值](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue)方法重置已編輯屬性的原始值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
