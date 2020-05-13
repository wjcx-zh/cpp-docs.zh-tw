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
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367487"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 類別

類別`CMFCFontInfo`描述字型的名稱和其他屬性。

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
|[CMFC方資訊:取得全名](#getfullname)|檢索字體及其字元集(腳本)的串聯名稱。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC方資訊::m_nCharSet](#m_ncharset)|指定與字型關聯的字元集(文稿)的值。|
|[CMFC方資訊:m_nPitchAndFamily](#m_npitchandfamily)|指定字體的間距和族的值。|
|[CMFC方資訊:m_nType](#m_ntype)|指定字型類型的值。|
|[CMFC方資訊:m_strName](#m_strname)|字體的名稱;例如 **,Arial**。|
|[CMFC方資訊::m_strScript](#m_strscript)|與字體關聯的字元集(文稿)的名稱。|

## <a name="remarks"></a>備註

您可以將`CMFCFontInfo`物件附加到[CMFCToolBarFontCombox 類](../../mfc/reference/cmfctoolbarfontcombobox-class.md)的項。 調用[CMFCToolBarFontCombox:getFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法以檢`CMFCFontInfo`索指向 物件的指標。

## <a name="example"></a>範例

下面的範例示範如何使用`CMFCFontInfo`類的各個成員。 該示例演示如何從`CMFCFontInfo``CMFCRibbonFontComboBox`獲取 物件以及如何訪問其局部變數。 此示例是[MSOffice 2007演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afxtoolbarfontcombox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFC方資訊:CMFC方資訊

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

*lpsz名稱*<br/>
[在]字型的名稱。 有關詳細資訊,請參閱`lfFaceName`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*lpszScript*<br/>
[在]字型的文稿(字元集)的名稱。

*nCharSet*<br/>
[在]指定字型的字元集(文稿)的值。 有關詳細資訊,請參閱`lfCharSet`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*n 皮奇和家庭*<br/>
[在]指定字體的間距和族的值。 有關詳細資訊,請參閱`lfPitchAndFamily`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

*nType*<br/>
[在]指定字型類型的值。 此參數可以是DEVICE_FONTTYPE、RASTER_FONTTYPE和TRUETYPE_FONTTYPE的位組合 (OR)。

*src*<br/>
[在]其成員用於`CMFCFontInfo`建構此`CMFCFontInfo`物件的現有物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

此文件可相互換使用字*元集*與*文稿*。 *文本*(也稱為書寫系統)是用一種或多種語言書寫這些字元的字元和規則的集合。 字元的集合包括該腳本中使用的字母表和標點符號。 例如,拉丁語腳本用於英語,因為它在美國使用,其字母表包括從A到Z的字元。`lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員指定字元集。 例如,值ANSI_CHARSET指定 ANSI 字元集,其中包括拉丁文本的字母表。

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFC方資訊:取得全名

檢索字體及其字元集(腳本)的串聯名稱。

```
CString GetFullName() const;
```

### <a name="return-value"></a>傳回值

包含字型名稱和文稿的字串。

### <a name="remarks"></a>備註

使用此方法獲取字體的全名。 例如,如果字體名稱為**Arial,** 並且字體腳本為**西里爾,** 則此方法返回"Arial(西里爾)"。

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFC方資訊::m_nCharSet

指定與字型關聯的字元集(文稿)的值。

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 CMFCFontInfo 的*nCharSet*參數[::CMFCFontInfo](#cmfcfontinfo)構造函數。

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFC方資訊:m_nPitchAndFamily

指定字體的間距(點大小)和族(例如,襯線、無襯線和單一空間)的值。

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 CMFCFontInfo 的*nPitch 和系列*參數[::CMFCFontInfo](#cmfcfontinfo)構造函數。

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFC方資訊:m_nType

指定字型類型的值。

```
const int m_nType;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 CMFCFontInfo 的*nType*參數[::CMFCFontInfo](#cmfcfontinfo)構造函數。

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFC方資訊:m_strName

字型名稱:例如 **,Arial**。

```
const CString m_strName;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 CMFCFontInfo 的*lpszName*參數[::CMFCFontInfo](#cmfcfontinfo)構造函數。

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFC方資訊::m_strScript

與字體關聯的字元集(文稿)的名稱。

```
const CString m_strScript;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 CMFCFontInfo 的*lpszScript*參數[::CMFCFontInfo](#cmfcfontinfo)構造函數。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox 類別](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
