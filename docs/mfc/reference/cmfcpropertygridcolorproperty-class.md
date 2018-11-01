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
ms.openlocfilehash: c284906a85ec93c5c5419acb783f6f46ebcf03e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575730"
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
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|可讓*自動*色彩選取對話方塊上的按鈕。 (標準自動按鈕會標示**自動**。)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|可讓*其他*色彩選取對話方塊上的按鈕。 (標準其他按鈕會標示**更多色彩**。)|
|`CMFCPropertyGridColorProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|取得屬性的目前色彩。|
|`CMFCPropertyGridColorProperty::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|`CMFCPropertyGridColorProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|由架構呼叫以顯示屬性值。 (覆寫[cmfcpropertygridproperty:: Ondrawvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue)。)|
|`CMFCPropertyGridColorProperty::OnEdit`|使用者即將修改屬性值時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onedit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit)。)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|當可編輯屬性的值變更時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onupdatevalue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue)。)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|設定屬性的新色彩。|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|指定目前色彩屬性格線中的資料行數目。|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|設定可編輯屬性的原始值。|

## <a name="remarks"></a>備註

`CMFCPropertyGridColorProperty` 類別支援的色彩屬性可以加入至屬性清單控制項。 如需詳細資訊，請參閱 < [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCPropertyGridColorProperty` 類別的物件，以及使用 `CMFCPropertyGridColorProperty` 類別的各種方法來設定此物件。 程式碼說明如何啟用自動和其他按鈕，以及如何設定色彩和資料行數目。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertygridctrl.h

##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

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
[in]屬性的名稱。

*色彩*<br/>
[in]屬性的色彩值。

*pPalette*<br/>
[in]指標的色彩調色盤。 預設值是 NULL。

*lpszDescr*<br/>
[in]屬性描述。 預設值是 NULL。

*dwData*<br/>
[in]應用程式特定資料，例如整數或其他與屬性相關聯的資料指標。 預設值為 0。

##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton

可讓*自動*色彩選取對話方塊上的按鈕。 (標準自動按鈕會標示**自動**。)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in][自動] 按鈕的標籤文字。

*colorAutomatic*<br/>
[in]自動 （預設） 色彩的 RGB 色彩值。

*bEnable*<br/>
[in]若要啟用自動的按鈕，則為 TRUE否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton

可讓*其他*色彩選取對話方塊上的按鈕。 (標準其他按鈕會標示**更多色彩**。)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in][其他] 按鈕的標籤文字。

*bAltColorDlg*<br/>
[in]True 會顯示`CMFCColorDialog`此對話方塊。如果為 false，則顯示標準色彩選取對話方塊。 預設值為 TRUE。

*bEnable*<br/>
[in]若要顯示 [其他] 按鈕;，則為 TRUE否則為 FALSE。  預設值為 TRUE。

### <a name="remarks"></a>備註

##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor

取得屬性的目前色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor

設定屬性的新色彩。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber

指定目前色彩屬性格線中的資料行數目。

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>參數

*nColumnsNumber*<br/>
[in]色彩屬性格線中的資料行的慣用的數目。

### <a name="remarks"></a>備註

這個方法會設定的值`m_nColumnsNumber`受保護的資料成員。

##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue

設定可編輯屬性的原始值。

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*varValue*<br/>
[in]一個值。

### <a name="remarks"></a>備註

使用[cmfcpropertygridproperty:: Resetoriginalvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue)方法來重設已編輯的屬性的原始值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
