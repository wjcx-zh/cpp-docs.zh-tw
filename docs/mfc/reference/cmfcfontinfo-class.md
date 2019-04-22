---
title: CMFCFontInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 930aceb4514195f0e844c35d326b52d9cd8d31fa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781324"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 類別

`CMFCFontInfo`類別所描述的名稱和字型的其他屬性。

## <a name="syntax"></a>語法

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCFontInfo`|建構 `CMFCFontInfo` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|擷取的字型和它的字元串連的名稱集 （指令碼）。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|值，指定與字型相關聯的字集 （指令碼）。|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|值，指定的字幅和家族的字型。|
|[CMFCFontInfo::m_nType](#m_ntype)|值，指定字型的類型。|
|[CMFCFontInfo::m_strName](#m_strname)|字型; 的名稱例如， **Arial**。|
|[CMFCFontInfo::m_strScript](#m_strscript)|字元集 （指令碼） 與字型相關聯的名稱。|

## <a name="remarks"></a>備註

您可以將附加`CMFCFontInfo`物件的項目[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)類別。 呼叫[CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法來擷取變數的指標，`CMFCFontInfo`物件。

## <a name="example"></a>範例

下列範例示範如何使用各類成員`CMFCFontInfo`類別。 此範例示範如何取得`CMFCFontInfo`物件從`CMFCRibbonFontComboBox`，以及如何存取其本機變數。 此範例中是屬於[MSOffice 2007 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxtoolbarfontcombobox.h

##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo

建構 `CMFCFontInfo` 物件。

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
[in]字型的名稱。 如需詳細資訊，請參閱 <<c0> `lfFaceName` 隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。

*lpszScript*<br/>
[in]指令碼 （字元集） 的字型名稱。

*nCharSet*<br/>
[in]值，指定字型的字元集 （指令碼）。 如需詳細資訊，請參閱 <<c0> `lfCharSet` 隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。

*nPitchAndFamily*<br/>
[in]值，指定的字幅和家族的字型。 如需詳細資訊，請參閱 <<c0> `lfPitchAndFamily` 隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。

*nType*<br/>
[in]指定的字型類型的值。 這個參數可以是 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 合 (OR)。

*src*<br/>
[in]將現有`CMFCFontInfo`物件，其成員用來建構這個`CMFCFontInfo`物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

這份文件使用詞彙*字元集*並*指令碼*交替。 A*指令碼*，這就是所謂的書寫系統，是字元和規則的一或多個語言中撰寫這些字元的集合。 字元的集合可包含字母與使用該指令碼中的標點符號。 比方說，拉丁文字用於英文，唸在美國，以及其字母包括從 A 到 Z 的字元。`lfCharSet`隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構指定的字元集。 比方說，新細明的值指定 ANSI 字元集，其中包括拉丁指令碼的字母。

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

擷取的字型和它的字元串連的名稱集 （指令碼）。

```
CString GetFullName() const;
```

### <a name="return-value"></a>傳回值

字串，包含字型名稱和指令碼。

### <a name="remarks"></a>備註

您可以使用這個方法來取得字型的完整名稱。 比方說，如果字型名稱為**Arial**字型指令碼，而且**斯拉夫**，這個方法會傳回"新細明體 （斯拉夫） 」。

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

值，指定與字型相關聯的字集 （指令碼）。

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < *nCharSet*的參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

值，指定的字幅 （點大小） 和字型系列 （比方說，serif，新細明體和等寬）。

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < *nPitchAndFamily*的參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

值，指定字型的類型。

```
const int m_nType;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < *n*的參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

字型的名稱： 例如， **Arial**。

```
const CString m_strName;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < *lpszName*的參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

字元集 （指令碼） 與字型相關聯的名稱。

```
const CString m_strScript;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < *lpszScript*的參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox 類別](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
