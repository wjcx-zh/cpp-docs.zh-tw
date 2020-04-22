---
title: CMFC 功能放大縮小字型功能 放大縮小字型功能
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
ms.openlocfilehash: dbf28787e0c0f7d89586fbf98632bd9172c12eed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754163"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

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
|`CMFCRibbonFontComboBox::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|在下拉式方塊中選取指定的字型。|

## <a name="remarks"></a>備註

建立`CMFCRibbonFontComboBox`物件後,請呼叫[CMFC 功能面板將其新增到功能區面板::新增](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

使用字體填充功能區上的組合框。

```cpp
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*n 字型型別*<br/>
[在]指定要添加的字型的字型類型。

*nCharSet*<br/>
[在]指定要新增的字型的字元集。

*n 皮奇和家庭*<br/>
[在]指定要添加的字型的間距和族。

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFC 功能豐豐盒::CMFC 功能豐豐博盒

構造並初始化[CMFC 功能豐博盒](../../mfc/reference/cmfcribbonfontcombobox-class.md)物件。

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
[在]當使用者從組合框中選擇項時執行的命令的命令 ID。

*n 字型型別*<br/>
[在]指定要在組合框中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

*nCharSet*<br/>
[在]將組合框中的字型篩選為屬於指定字元集的字型。

*n 皮奇和家庭*<br/>
[在]指定組合框中顯示的字型的間距和族。

*n 寬度*<br/>
[在]指定組合框的寬度(以像素為單位)。

### <a name="remarks"></a>備註

有關可能的*nFontType*參數值的詳細資訊,請參閱 Windows SDK 文檔中的[EnumFontFamProc。](/previous-versions/dd162621\(v=vs.85\))

有關可分配給*nCharSet*的有效字元集的詳細資訊,以及可分配給*nPitch 和Family*的有效值,請參閱 Windows SDK 文件中的[LOGFONT。](/windows/win32/api/wingdi/ns-wingdi-logfontw)

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>參數

[在]*iIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

使用以前指定的字型類型、字元集、間距和族的字體填充功能區上的組合框。

```cpp
void RebuildFonts();
```

### <a name="remarks"></a>備註

您可以指定字型類型、字元集、間距以及字體的音調以及要包含在此類[建構函數](#cmfcribbonfontcombobox)的功能區字型組合框中,或者通過調用[CMFCRibbonFontCombox::BuildFonts。](#buildfonts)

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

在下拉式方塊中選取指定的字型。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>參數

"lpszName" 指定要選擇的字型名稱。

*nCharSet*<br/>
指定選取的字型集。

*b精確*<br/>
TRUE 指定字元集在選擇字體時必須匹配;FALSE 指定在選擇字型時可以忽略字元集。

### <a name="return-value"></a>傳回值

如果找到並選擇了指定的字體,則非零;否則,零。

### <a name="remarks"></a>備註

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

傳回指定的字元集。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>傳回值

字元集(請參閱 Windows SDK 文檔中的 LOGFONT)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

傳回要在下拉式方塊中顯示的字型類型。 有效的選項為 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE，或任何位元組合。

```
int GetFontType() const;
```

### <a name="return-value"></a>傳回值

字型類型(請參閱 Windows SDK 文檔中的 EnumFontFamProc)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

傳回在下拉式方塊中顯示之字型的字距和系列。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>傳回值

間距和系列(請參閱 Windows SDK 文檔中的 LOGFONT)。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox 類別](../../mfc/reference/cmfcribboncombobox-class.md)
