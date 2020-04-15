---
title: CMFCPropertyGridFontProperty 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361842"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 類別

類`CMFCPropertyGridFileProperty`支援打開字體選擇對話方塊的屬性清單控制項。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC財產網格方瑟財產:CMFC財產網格方瑟財產](#cmfcpropertygridfontproperty)|建構 `CMFCPropertyGridFontProperty` 物件。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[CMFC 屬性網格屬性::格式屬性](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFC財產網格方屬性:取得顏色](#getcolor)|檢索使用者從字體對話框中選擇的字體顏色。|
|[CMFC財產網格方瑟財產:獲取日誌字體](#getlogfont)|檢索使用者從字體對話框中選擇的字體。|
|`CMFCPropertyGridFontProperty::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyGridFontProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[CMFC 屬性網格屬性::按一下按鈕](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>需求

**標題:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFC財產網格方瑟財產:CMFC財產網格方瑟財產

建構 `CMFCPropertyGridFontProperty` 物件。

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*strName*<br/>
[在]屬性的名稱。

*如果*<br/>
[在]指定字體屬性的邏輯字體結構。

*dwFontDialogFlags*<br/>
[在]應用於按一下屬性值下拉按鈕時顯示的字型對話框的樣式。 默認值是CF_EFFECTS和CF_SCREENFONTS的位組合 (OR)。 有關詳細資訊,請參閱[CHOOSEFONT 結構](/windows/win32/api/commdlg/ns-commdlg-choosefontw)*的標誌參數。*

*lpszDescr*<br/>
[在]字體屬性的說明。 預設值是 NULL。

*dwData*<br/>
[在]特定於應用程式的數據,例如整數或指向與屬性關聯的其他數據的指標。 預設值為 0。

*顏色*<br/>
[在]字體的顏色。 預設值為預設色彩。

### <a name="remarks"></a>備註

物件`CMFCPropertyGridFontProperty`表示屬性網格字體控制件中的字體屬性。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCPropertyGridFontProperty`類的物件。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFC財產網格方屬性:取得顏色

檢索使用者從字體對話框中選擇的字體顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

表示所選字體顏色的 RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFC財產網格方瑟財產:獲取日誌字體

檢索使用者從字體對話框中選擇的字體。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>傳回值

指向描述所選字體的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
