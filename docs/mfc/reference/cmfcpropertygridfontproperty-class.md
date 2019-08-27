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
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505116"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 類別

`CMFCPropertyGridFileProperty`類別支援可開啟字型選取對話方塊的屬性清單控制項專案。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|建構 `CMFCPropertyGridFontProperty` 物件。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|抓取使用者從 [字型] 對話方塊中選取的字型色彩。|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|抓取使用者從 [字型] 對話方塊中選取的字型。|
|`CMFCPropertyGridFontProperty::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyGridFontProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>需求

**標頭:** afxpropertygridctrl。h

##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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
在屬性的名稱。

*lf*<br/>
在指定字型屬性的邏輯字型結構。

*dwFontDialogFlags*<br/>
[in]會套用至字型對話方塊會顯示當您按一下屬性值的下拉式按鈕的樣式。 預設值為 CF_EFFECTS 和 CF_SCREENFONTS 的位元組合 (OR)。 如需詳細資訊, 請參閱[CHOOSEFONT 結構](/windows/win32/api/commdlg/ns-commdlg-choosefontw)的*Flags*參數。

*lpszDescr*<br/>
在字型屬性的描述。 預設值為 Null。

*dwData*<br/>
在應用程式特定的資料, 例如整數或與屬性相關聯之其他資料的指標。 預設值為 0。

*color*<br/>
在字型的色彩。 預設值為預設色彩。

### <a name="remarks"></a>備註

`CMFCPropertyGridFontProperty`物件代表屬性方格字型控制項中的字型屬性。

### <a name="example"></a>範例

下列範例示範如何建立`CMFCPropertyGridFontProperty`類別的物件。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>CMFCPropertyGridFontProperty:: GetColor

抓取使用者從 [字型] 對話方塊中選取的字型色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 色彩值, 表示選取的字型色彩。

### <a name="remarks"></a>備註

##  <a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

抓取使用者從 [字型] 對話方塊中選取的字型。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>傳回值

[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的指標, 描述選取的字型。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
