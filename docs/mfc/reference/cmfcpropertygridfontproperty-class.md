---
title: CMFCPropertyGridFontProperty 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d6c1f9f9b2084273345463bccfe4eb2bc78d150
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384386"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 類別

`CMFCPropertyGridFileProperty`類別支援開啟字型選取對話方塊的屬性清單控制項項目。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|建構 `CMFCPropertyGridFontProperty` 物件。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|格式化屬性值的文字表示法。 (覆寫[cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|擷取使用者從 [字型] 對話方塊中選取的字型色彩。|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|擷取使用者從 [字型] 對話方塊中選取的字型。|
|`CMFCPropertyGridFontProperty::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|`CMFCPropertyGridFontProperty::OnClickButton`|使用者按一下屬性中內含的按鈕時由架構呼叫。 (覆寫[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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
[in]屬性的名稱。

*lf*<br/>
[in]一種邏輯字型結構指定的字型屬性。

*dwFontDialogFlags*<br/>
[in]會套用至字型] 對話方塊會顯示當您按一下屬性值的下拉式按鈕的樣式。 預設值是 CF_EFFECTS 和 CF_SCREENFONTS 合 (OR)。 如需詳細資訊，請參閱 <<c0>  *旗標*的參數[CHOOSEFONT 結構](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta)。

*lpszDescr*<br/>
[in][字型] 屬性的描述。 預設值是 NULL。

*dwData*<br/>
[in]應用程式特定資料，例如整數或其他與屬性相關聯的資料指標。 預設值為 0。

*色彩*<br/>
[in]字型的色彩。 預設值為預設色彩。

### <a name="remarks"></a>備註

A`CMFCPropertyGridFontProperty`物件都代表在屬性方格字型控制項的字型屬性。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCPropertyGridFontProperty`類別。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

擷取使用者從 [字型] 對話方塊中選取的字型色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

表示選取的字型色彩的 RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

擷取使用者從 [字型] 對話方塊中選取的字型。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>傳回值

指標[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)該結構描述選取的字型。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)
