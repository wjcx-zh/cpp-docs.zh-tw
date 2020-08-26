---
title: 標準對話方塊資料驗證常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 19d1858d67802a7c464a9be783e4c1fb96fe3fae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844479"
---
# <a name="standard-dialog-data-validation-routines"></a>標準對話方塊資料驗證常式

本主題列出標準的對話資料驗證 (DDV 用於一般 MFC 對話方塊控制項的) 常式。

> [!NOTE]
> 標準對話方塊資料交換常式會定義在標頭檔 afxdd_ .h 中。 不過，應用程式應該包含 afxwin.h。

### <a name="ddv-functions"></a>DDV 函式

|名稱|描述|
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|確認指定控制項值中的字元數未超過指定的最大值。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|確認指定的控制項值未超過指定的 **位元組** 範圍。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|確認指定的控制項值未超過指定的時間範圍。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|確認指定的控制項值未超過指定的 **`double`** 範圍。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|確認指定的控制項值未超過指定的 **DWORD** 範圍。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|確認指定的控制項值未超過指定的 **`float`** 範圍。|
|[DDV_MinMaxInt](#ddv_minmaxint)|確認指定的控制項值未超過指定的 **`int`** 範圍。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|確認指定的控制項值未超過指定的 **`long`** 範圍。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|確認指定的控制項值未超過指定的 **LONGLONG** 範圍。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|確認指定的控制項值未超過指定的日期範圍。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|確認指定的控制項值未超過指定的 **`short`** 範圍。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|確認指定的滑杆控制項值落在指定的範圍內。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|確認指定的控制項值未超過指定的 **UINT** 範圍。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|確認指定的控制項值落在兩個指定的值之間。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|確認指定的控制項值未超過指定的 **ULONGLONG** 範圍。|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a> DDV_MaxChars

呼叫 `DDV_MaxChars` 以確認與 *值* 相關聯之控制項中的字元數量沒有超過 *nChars*。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*nChars*<br/>
允許的字元數上限。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a> DDV_MinMaxByte

呼叫 `DDV_MinMaxByte` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許的 BYTE) 類型的最小值 (。

*maxVal*<br/>
允許的 BYTE) 類型的最大值 (。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a> DDV_MinMaxDateTime

呼叫 `DDV_MinMaxDateTime` 以確認日期和時間選擇器控制項中的時間/日期值 ( 與*RefValue*相關聯的[CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 落在*refMinRange*和*refMaxRange*之間。

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
與對話方塊、表單檢視或 control view 物件的成員變數相關聯的 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 物件的參考。 此物件包含要驗證的資料。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a> DDV_MinMaxDouble

呼叫 `DDV_MinMaxDouble` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許) 類型的最小值 (**`double`** 。

*maxVal*<br/>
允許) 類型的最大值 (**`double`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a> DDV_MinMaxDWord

呼叫 `DDV_MinMaxDWord` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許的類型為 DWORD) 最小值 (。

*maxVal*<br/>
允許 DWORD) 類型的最大值 (。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a> DDV_MinMaxFloat

呼叫 `DDV_MinMaxFloat` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許) 類型的最小值 (**`float`** 。

*maxVal*<br/>
允許) 類型的最大值 (**`float`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a> DDV_MinMaxInt

呼叫 `DDV_MinMaxInt` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許) 類型的最小值 (**`int`** 。

*maxVal*<br/>
允許) 類型的最大值 (**`int`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a> DDV_MinMaxLong

呼叫 `DDV_MinMaxLong` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許) 類型的最小值 (**`long`** 。

*maxVal*<br/>
允許) 類型的最大值 (**`long`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a> DDV_MinMaxLongLong

呼叫 `DDV_MinMaxLongLong` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許的 LONGLONG 類型的最小值 () 。

*maxVal*<br/>
允許的 LONGLONG 類型的最大值 () 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a> DDV_MinMaxMonth

呼叫 `DDV_MinMaxMonth` 以確認月曆控制項中 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 與 *refValue* 相關聯的時間/日期值落在 *refMinRange* 和 *refMaxRange*之間。

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
類型之物件的參考 `CTime` `COleDateTime` ，或與對話方塊、表單檢視或 control view 物件的成員變數相關聯的參考。 此物件包含要驗證的資料。 當呼叫時，MFC 會傳遞此參考 `DDV_MinMaxMonth` 。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a> DDV_MinMaxShort

呼叫 `DDV_MinMaxShort` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許) 類型的最小值 (**`short`** 。

*maxVal*<br/>
允許) 類型的最大值 (**`short`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a> DDV_MinMaxSlider

呼叫 `DDV_MinMaxSlider` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
要驗證之值的參考。 此參數會保存或設定滑杆控制項的目前 thumb 位置。

*minVal*<br/>
允許的最小值。

*maxVal*<br/>
允許的最大值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需滑杆控制項的詳細資訊，請參閱 [使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a> DDV_MinMaxUInt

呼叫 `DDV_MinMaxUInt` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許類型 UINT) 的最小值 (。

*maxVal*<br/>
允許類型 UINT) 的最大值 (。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a> DDV_MinMaxULongLong

呼叫 `DDV_MinMaxULongLong` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許的 ULONGLONG 類型的最小值 () 。

*maxVal*<br/>
允許的 ULONGLONG 類型的最大值 () 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

呼叫 `DDV_MinMaxUnsigned` 以確認與 *值* 相關聯之控制項中的值落在 *minVal* 和 *maxVal*之間。

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
對話方塊之成員變數的參考、表單檢視，或是用來驗證資料的 control view 物件。

*minVal*<br/>
允許 ) 類型的最小值 (**`unsigned`** 。

*maxVal*<br/>
允許 ) 類型的最大值 (**`unsigned`** 。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxdd_。h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料交換常式](standard-dialog-data-exchange-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
