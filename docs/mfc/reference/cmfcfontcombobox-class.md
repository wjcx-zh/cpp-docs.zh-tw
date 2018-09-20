---
title: CMFCFontComboBox 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: feb34a64fee8f3d3674f1513ea2a964f574aab54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402494"
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

|名稱|描述|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|由架構呼叫以判斷新的項目在目前的字型下拉式方塊控制項的已排序的清單方塊中的相對位置。 (覆寫[CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|
|`CMFCFontComboBox::DrawItem`|由架構呼叫以在目前的字型下拉式方塊控制項中繪製指定的項目。 (覆寫[CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem)。)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|擷取目前選取的字型相關資訊。|
|`CMFCFontComboBox::MeasureItem`|由架構呼叫以通知 Windows 的清單方塊，目前的字型下拉式方塊控制項中的維度。 (覆寫[CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|
|`CMFCFontComboBox::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCFontComboBox::SelectFont](#selectfont)|選取符合指定的準則從字型下拉式方塊的字型。|
|[CMFCFontComboBox::Setup](#setup)|初始化字型下拉式方塊中的項目清單。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|指出 framework 用來繪製目前的字型下拉式方塊中的項目標籤的字型。|

## <a name="remarks"></a>備註

若要使用`CMFCFontComboBox`物件在對話方塊中，並將`CMFCFontComboBox`變數加入對話方塊類別。 然後在`OnInitDialog`方法的對話方塊類別，呼叫[CMFCFontComboBox::Setup](#setup)方法來初始化下拉式方塊控制項中的項目清單。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxfontcombobox.h

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

建構 `CMFCFontComboBox` 物件。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

擷取目前選取的字型相關資訊。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>傳回值

指標[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)描述字型的物件。 如果沒有字型選取下拉式方塊中，它可以是 NULL。

### <a name="remarks"></a>備註

##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont

指出 framework 用來繪製目前的字型下拉式方塊中的項目標籤的字型。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>備註

將這個成員設定為 TRUE 可引導架構應使用的相同字型來繪製每個項目標籤。 此成員設為 false，則導向的架構，來繪製每個項目包含標籤名稱等同於標籤的字型。 這個成員的預設值為 FALSE。

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

選取符合指定的準則從字型下拉式方塊的字型。

```
BOOL SelectFont(CMFCFontInfo* pDesc);


BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>參數

*pDesc*<br/>
[in]指向字型描述物件。

*lpszName*<br/>
[in]指定的字型名稱。

*nCharSet*<br/>
[in]指定的字元集。 預設值是 DEFAULT_CHARSET。 如需詳細資訊，請參閱 <<c0> `lfCharSet` 隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。

### <a name="return-value"></a>傳回值

如果字型下拉式方塊中的項目符合指定的字型描述物件或字型名稱和字元集，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

使用這個方法來選取及捲動到對應至指定的字型字型下拉式方塊中的項目。

### <a name="example"></a>範例

下列範例示範如何使用`SelectFont`方法中的`CMFCFontComboBox`類別。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

初始化字型下拉式方塊中的項目清單。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*nFontType*<br/>
[in]指定的字型類型。 預設值為 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 合 (OR)。

*nCharSet*<br/>
[in]指定字型的字元集。 預設值是 DEFAULT_CHARSET。

*nPitchAndFamily*<br/>
[in]指定字型的字距和系列。 預設值是 DEFAULT_PITCH。

### <a name="return-value"></a>傳回值

如果已成功; 初始化字型下拉式方塊，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會初始化字型下拉式方塊，藉由列舉符合指定的參數的目前已安裝的字型，並插入字型下拉式方塊中的這些字型名稱。

### <a name="example"></a>範例

下列範例示範如何使用`Setup`方法中的`CMFCFontComboBox`類別。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)
