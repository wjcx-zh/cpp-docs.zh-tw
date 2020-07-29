---
title: 標準對話方塊資料驗證常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 2511e2ec6dbd4e27c0e12e35bdc1cd671bf72eaa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213979"
---
# <a name="standard-dialog-data-validation-routines"></a>標準對話方塊資料驗證常式

本主題列出常用 MFC 對話方塊控制項所使用的標準對話資料驗證（DDV）常式。

> [!NOTE]
> 標準對話方塊資料交換常式會定義在標頭檔 afxdd_ .h 中。 不過，應用程式應該包含 afxwin.h。

### <a name="ddv-functions"></a>DDV 函式

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|驗證指定控制項值中的字元數未超過指定的上限。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|驗證指定的控制項值未超過指定的**位元組**範圍。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|驗證指定的控制項值未超過指定的時間範圍。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|驗證指定的控制項值未超過指定的 **`double`** 範圍。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|驗證指定的控制項值未超過指定的**DWORD**範圍。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|驗證指定的控制項值未超過指定的 **`float`** 範圍。|
|[DDV_MinMaxInt](#ddv_minmaxint)|驗證指定的控制項值未超過指定的 **`int`** 範圍。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|驗證指定的控制項值未超過指定的 **`long`** 範圍。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|驗證指定的控制項值未超過指定的**LONGLONG**範圍。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|驗證指定的控制項值未超過指定的日期範圍。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|驗證指定的控制項值未超過指定的 **`short`** 範圍。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|驗證指定的滑杆控制項值是否落在指定的範圍內。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|驗證指定的控制項值未超過指定的**UINT**範圍。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|驗證給定的控制項值介於兩個指定的值之間。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|驗證指定的控制項值未超過指定的**ULONGLONG**範圍。|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

呼叫 `DDV_MaxChars` 以確認與*值*相關聯之控制項中的字元數量不會超過*nChars*。

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*nChars*<br/>
允許的最大字元數。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

呼叫 `DDV_MinMaxByte` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 BYTE）。

*maxVal*<br/>
允許的最大值（類型為 BYTE）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

呼叫 `DDV_MinMaxDateTime` 以確認與*refValue*相關聯之日期和時間選擇器控制項（ [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)）中的時間/日期值落在*refMinRange*和*refMaxRange*之間。

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。

*refValue*<br/>
與對話方塊、表單檢視或控制項視圖物件的成員變數相關聯之[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考。 此物件包含要驗證的資料。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

呼叫 `DDV_MinMaxDouble` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`double`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`double`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

呼叫 `DDV_MinMaxDWord` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 DWORD）。

*maxVal*<br/>
允許的最大值（類型為 DWORD）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

呼叫 `DDV_MinMaxFloat` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`float`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`float`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

呼叫 `DDV_MinMaxInt` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`int`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`int`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

呼叫 `DDV_MinMaxLong` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`long`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`long`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

呼叫 `DDV_MinMaxLongLong` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 LONGLONG）。

*maxVal*<br/>
允許的最大值（類型為 LONGLONG）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

呼叫 `DDV_MinMaxMonth` 以確認與*refValue*相關聯的月曆控制項（ [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)）中的時間/日期值落在*refMinRange*和*refMaxRange*之間。

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*refValue*<br/>
類型物件的參考 `CTime` `COleDateTime` ，或與對話方塊、表單檢視或控制項視圖物件的成員變數相關聯的。 此物件包含要驗證的資料。 當呼叫時，MFC 會傳遞此參考 `DDV_MinMaxMonth` 。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

呼叫 `DDV_MinMaxShort` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`short`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`short`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

呼叫 `DDV_MinMaxSlider` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證之值的參考。 這個參數會保留或設定滑杆控制項的目前捲軸位置。

*minVal*<br/>
允許的最小值。

*maxVal*<br/>
允許的最大值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需滑杆控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

呼叫 `DDV_MinMaxUInt` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（UINT 類型）。

*maxVal*<br/>
允許的最大值（UINT 類型）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

呼叫 `DDV_MinMaxULongLong` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 ULONGLONG）。

*maxVal*<br/>
允許的最大值（類型為 ULONGLONG）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

呼叫 `DDV_MinMaxUnsigned` 以確認與*值*相關聯之控制項中的值落在*minVal*和*maxVal*之間。

### <a name="syntax"></a>語法

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
要驗證資料之對話方塊、表單檢視或控制項視圖物件的成員變數參考。

*minVal*<br/>
允許的最小值（類型為 **`unsigned`** ）。

*maxVal*<br/>
允許的最大值（類型為 **`unsigned`** ）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

**標頭：** afxdd_。h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料交換常式](standard-dialog-data-exchange-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
