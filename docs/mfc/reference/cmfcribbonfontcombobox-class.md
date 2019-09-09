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
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504960"
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

|名稱|說明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|在功能區字型下拉式方塊中填入指定字型類型的字型、字元集，及字距和系列。|
|`CMFCRibbonFontComboBox::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|傳回指定的字元集。|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|傳回在下拉式方塊中顯示之字型的字距和系列。|
|`CMFCRibbonFontComboBox::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|在下拉式方塊中選取指定的字型。|

## <a name="remarks"></a>備註

建立`CMFCRibbonFontComboBox`物件之後，請呼叫[CMFCRibbonPanel：： add](../../mfc/reference/cmfcribbonpanel-class.md#add)將它加入至功能區面板。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxRibbonComboBox。h

##  <a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

在功能區的下拉式方塊中填入字型。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*nFontType*<br/>
在指定要加入之字型的字型類型。

*nCharSet*<br/>
在指定要加入之字型的字元集。

*nPitchAndFamily*<br/>
在指定要加入之字型的音調和系列。

##  <a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

建立[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)物件的結構並加以初始化。

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
在當使用者從下拉式方塊中選取專案時，所執行命令的命令 ID。

*nFontType*<br/>
在指定要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

*nCharSet*<br/>
在將下拉式方塊中的字型篩選成屬於指定字元集的字型。

*nPitchAndFamily*<br/>
在指定顯示在下拉式方塊中的字型音調和系列。

*nWidth*<br/>
在指定下拉式方塊的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

如需可能*nFontType*參數值的詳細資訊，請參閱 Windows SDK 檔中的[EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) 。

如需可指派給*nCharSet*之有效字元集的詳細資訊，以及可指派給*nPitchAndFamily*的有效值，請參閱 Windows SDK 檔中的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 。

##  <a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

如需詳細資訊，請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>參數

在*iIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

在功能區的下拉式方塊中填入先前指定的字型類型、字元集和音調和系列的字型。

```
void RebuildFonts();
```

### <a name="remarks"></a>備註

您[可以在這個類別的函](#cmfcribbonfontcombobox)式中，指定要包含在功能區字型下拉式方塊中的字型類型、字元集和音調和系列，或是呼叫[CMFCRibbonFontComboBox：： BuildFonts](#buildfonts)。

##  <a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

在下拉式方塊中選取指定的字型。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>參數

' lpszName * 指定要選取之字型的名稱。

*nCharSet*<br/>
指定所選取字型的字元集。

*bExact*<br/>
TRUE 表示選取字型時，字元集必須相符;[FALSE] 指定在選取字型時可以忽略字元集。

### <a name="return-value"></a>傳回值

如果找到指定的字型並加以選取，則為非零值;否則為零。

### <a name="remarks"></a>備註

##  <a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

傳回指定的字元集。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>傳回值

字元集（請參閱 Windows SDK 檔中的 LOGFONT）。

### <a name="remarks"></a>備註

##  <a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

```
int GetFontType() const;
```

### <a name="return-value"></a>傳回值

字型類型（請參閱 Windows SDK 檔中的 EnumFontFamProc）。

### <a name="remarks"></a>備註

##  <a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

傳回在下拉式方塊中顯示之字型的字距和系列。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>傳回值

音調和系列（請參閱 Windows SDK 檔中的 LOGFONT）。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox 類別](../../mfc/reference/cmfcribboncombobox-class.md)
