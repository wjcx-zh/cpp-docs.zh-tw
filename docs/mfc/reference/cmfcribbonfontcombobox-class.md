---
title: CMFCRibbonFontComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 5feb97b274b6547ebc6868e27ead20824ce4e8ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635668"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 類別

實作包含字型清單的下拉式方塊。 您可以在功能區面板上放置下拉式方塊。

## <a name="syntax"></a>語法

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|解構函式。|

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|建構並初始化 `CMFCRibbonFontComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|在功能區字型下拉式方塊中填入指定字型類型的字型、字元集，及字距和系列。|
|`CMFCRibbonFontComboBox::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|傳回指定的字元集。|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|傳回在下拉式方塊中顯示之字型的字距和系列。|
|`CMFCRibbonFontComboBox::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|在下拉式方塊中選取指定的字型。|

## <a name="remarks"></a>備註

在建立後`CMFCRibbonFontComboBox`物件，將它新增至功能區面板中，藉由呼叫[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxRibbonComboBox.h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

在功能區字型下拉式方塊中填入。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*nFontType*<br/>
[in]指定要加入字型的字型類型。

*nCharSet*<br/>
[in]指定要加入字型的字元集。

*nPitchAndFamily*<br/>
[in]指定的字幅和加入的字型系列。

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

建構並初始化[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)物件。

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>參數

*nID*<br/>
[in]當使用者從下拉式方塊選取項目時執行命令的命令識別碼。

*nFontType*<br/>
[in]指定字型下拉式方塊中顯示類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

*nCharSet*<br/>
[in]篩選出隸屬於指定的字元集的下拉式方塊中的字型...

*nPitchAndFamily*<br/>
[in]指定的字幅和下拉式方塊中顯示的字型家族。

*nWidth*<br/>
[in]指定寬度，單位為像素下拉式方塊。

### <a name="remarks"></a>備註

如需有關可能*nFontType*參數值，請參閱[EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) Windows SDK 文件。

如需有效的字元集，可以指派給*nCharSet*，以及有效的值指派給*nPitchAndFamily*，請參閱[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)中Windows SDK 文件。

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>參數

[in]*iIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

先前指定的字型類型、 字元集，及字距和系列在功能區字型下拉式方塊中填入。

```
void RebuildFonts();
```

### <a name="remarks"></a>備註

您可以指定字型類型、 字元集，及字距和系列的字型，包含在功能區字型下拉式方塊中編輯方塊中[建構函式](#cmfcribbonfontcombobox)對於此類別，或藉由呼叫[CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

在下拉式方塊中選取指定的字型。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>參數

' lpszName * 指定要選取的字型名稱。

*nCharSet*<br/>
指定選取的字型的字元集。

*bExact*<br/>
若要指定當您選取的字型; 時，必須符合的字元集，則為 TRUE指定當您選取的字型時，可以忽略的字元集，則為 FALSE。

### <a name="return-value"></a>傳回值

如果找到並選取，則指定的字型，則為非零否則為零。

### <a name="remarks"></a>備註

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

傳回指定的字元集。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>傳回值

字元集 （請參閱 Windows SDK 文件中的 LOGFONT） 的內容。

### <a name="remarks"></a>備註

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

```
int GetFontType() const;
```

### <a name="return-value"></a>傳回值

（請參閱 Windows SDK 文件中的 EnumFontFamProc） 的字型類型。

### <a name="remarks"></a>備註

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

傳回在下拉式方塊中顯示之字型的字距和系列。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>傳回值

字距和系列 （Windows SDK 文件，請參閱 LOGFONT）。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox 類別](../../mfc/reference/cmfcribboncombobox-class.md)
