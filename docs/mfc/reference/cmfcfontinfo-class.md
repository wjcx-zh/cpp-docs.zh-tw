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
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505267"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 類別

`CMFCFontInfo`類別會描述字型的名稱和其他屬性。

## <a name="syntax"></a>語法

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|`CMFCFontInfo`|建構 `CMFCFontInfo` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|抓取字型和其字元集 (腳本) 的串連名稱。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|值, 指定與字型相關聯的字元集 (腳本)。|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|值, 指定字型的音調和系列。|
|[CMFCFontInfo::m_nType](#m_ntype)|指定字型類型的值。|
|[CMFCFontInfo::m_strName](#m_strname)|字型的名稱;例如, **Arial**。|
|[CMFCFontInfo::m_strScript](#m_strscript)|與字型相關聯之字元集 (腳本) 的名稱。|

## <a name="remarks"></a>備註

您可以將`CMFCFontInfo`物件附加至[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)類別的專案。 呼叫[CMFCToolBarFontComboBox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法, 以取得`CMFCFontInfo`物件的指標。

## <a name="example"></a>範例

下列範例示範如何使用`CMFCFontInfo`類別的各種成員。 這個範例會示範如何`CMFCFontInfo` `CMFCRibbonFontComboBox`從取得物件, 以及如何存取它的本機變數。 這個範例是[MSOffice 2007 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭:** afxtoolbarfontcombobox。h

##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

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
在字型的名稱。 如需詳細資訊, 請`lfFaceName`參閱[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*lpszScript*<br/>
在字型的腳本名稱 (字元集)。

*nCharSet*<br/>
在值, 指定字型的字元集 (腳本)。 如需詳細資訊, 請`lfCharSet`參閱[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*nPitchAndFamily*<br/>
在值, 指定字型的音調和系列。 如需詳細資訊, 請`lfPitchAndFamily`參閱[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*nType*<br/>
在指定字型類型的值。 這個參數可以是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的位元組合 (OR)。

*src*<br/>
在現有`CMFCFontInfo`的物件, 其成員會用來建立`CMFCFontInfo`此物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

本檔會使用詞彙*組*和*腳本*交換。 *腳本*(也稱為寫入系統) 是一組字元和規則的集合, 可用於以一或多個語言撰寫這些字元。 字元集合包含該腳本中使用的字母和標點符號。 例如, 在美國說出來的英文時, 會使用拉丁腳本, 而其字母包含從 A 到 Z 的字元。[LOGFONT 結構](/windows/win32/api/wingdi/ns-wingdi-logfontw)的成員會指定`lfCharSet`字元集。 例如, 值 ANSI_CHARSET 會指定 ANSI 字元集, 其中包含拉丁腳本的字母。

##  <a name="getfullname"></a>CMFCFontInfo:: 問題

抓取字型和其字元集 (腳本) 的串連名稱。

```
CString GetFullName() const;
```

### <a name="return-value"></a>傳回值

包含字型名稱和腳本的字串。

### <a name="remarks"></a>備註

使用此方法可取得字型的完整名稱。 例如, 如果字型名稱是**Arial** , 而字型腳本是**斯拉夫**, 則此方法會傳回「arial (斯拉夫)」。

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

值, 指定與字型相關聯的字元集 (腳本)。

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)函數的*nCharSet*參數。

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

值, 指定字型的間距 (點大小) 和系列 (例如, serif、sans-serif 和等寬)。

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)函數的*nPitchAndFamily*參數。

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

指定字型類型的值。

```
const int m_nType;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)函數的*nType*參數。

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

字型的名稱: 例如, **Arial**。

```
const CString m_strName;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)函數的*lpszName*參數。

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

與字型相關聯之字元集 (腳本) 的名稱。

```
const CString m_strScript;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)函數的*lpszScript*參數。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox 類別](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
