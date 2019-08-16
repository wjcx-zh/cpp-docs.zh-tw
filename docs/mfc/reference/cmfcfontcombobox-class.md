---
title: CMFCFontComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505305"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 類別

`CMFCFontComboBox`類別會建立包含字型清單的下拉式方塊控制項。

## <a name="syntax"></a>語法

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|建構 `CMFCFontComboBox` 物件。|
|`CMFCFontComboBox::~CMFCFontComboBox`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|由架構呼叫, 以判斷新專案在目前字型下拉式方塊控制項之排序清單方塊中的相對位置。 (覆寫[CComboBox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|
|`CMFCFontComboBox::DrawItem`|由架構呼叫, 以在目前的字型下拉式方塊控制項中繪製指定的專案。 (覆寫[CComboBox::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem)。)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|抓取目前選取之字型的相關資訊。|
|`CMFCFontComboBox::MeasureItem`|由架構呼叫, 以通知視窗目前字型下拉式方塊控制項中清單方塊的維度。 (覆寫[CComboBox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|
|`CMFCFontComboBox::PreTranslateMessage`|會先轉譯視窗訊息, 再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCFontComboBox::SelectFont](#selectfont)|從 [字型] 下拉式方塊中選取符合指定準則的字型。|
|[CMFCFontComboBox::Setup](#setup)|初始化 [字型] 下拉式方塊中的專案清單。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|向架構表示在 [目前字型] 下拉式方塊中用來繪製專案標籤的字型。|

## <a name="remarks"></a>備註

若要在`CMFCFontComboBox`對話方塊中使用物件, 請`CMFCFontComboBox`將變數新增至對話方塊類別。 然後在對話方塊`OnInitDialog`類別的方法中, 呼叫[CMFCFontComboBox:: Setup](#setup)方法, 以初始化下拉式方塊控制項中的專案清單。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>需求

**標頭:** afxfontcombobox。h

##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

建構 `CMFCFontComboBox` 物件。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getselfont"></a>CMFCFontComboBox::GetSelFont

抓取目前選取之字型的相關資訊。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>傳回值

描述字型之[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)物件的指標。 如果未在下拉式方塊中選取字型, 則可以是 Null。

### <a name="remarks"></a>備註

##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

向架構表示在 [目前字型] 下拉式方塊中用來繪製專案標籤的字型。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>備註

將此成員設定為 TRUE, 以指示架構使用相同的字型來繪製每個專案標籤。 將此成員設定為 FALSE, 以指示架構使用其名稱與標籤相同的字型繪製每個專案標籤。 這個成員的預設值為 FALSE。

##  <a name="selectfont"></a>CMFCFontComboBox::SelectFont

從 [字型] 下拉式方塊中選取符合指定準則的字型。

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>參數

*pDesc*<br/>
在指向字型描述物件。

*lpszName*<br/>
在指定字型名稱。

*nCharSet*<br/>
在指定字元集。 預設值為 DEFAULT_CHARSET。 如需詳細資訊, 請`lfCharSet`參閱[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

### <a name="return-value"></a>傳回值

如果 [字型] 下拉式方塊中的專案符合指定的 [字型描述] 物件或 [字型名稱] 和 [字元集], 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用這個方法, 在對應至指定字型的 [字型] 下拉式方塊中選取並滾動到該專案。

### <a name="example"></a>範例

下列範例示範如何`SelectFont` `CMFCFontComboBox`在類別中使用方法。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>CMFCFontComboBox:: Setup

初始化 [字型] 下拉式方塊中的專案清單。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*nFontType*<br/>
在指定字型類型。 預設值是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的位元組合 (OR)。

*nCharSet*<br/>
在指定字型字元集。 預設值為 DEFAULT_CHARSET。

*nPitchAndFamily*<br/>
在指定字型音調和系列。 預設值為 DEFAULT_PITCH。

### <a name="return-value"></a>傳回值

如果已成功初始化字型下拉式方塊, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會藉由列舉符合指定參數的目前已安裝字型, 並在 [字型] 下拉式方塊中插入這些字型名稱, 來初始化 [字型] 下拉式方塊。

### <a name="example"></a>範例

下列範例示範如何`Setup` `CMFCFontComboBox`在類別中使用方法。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)
