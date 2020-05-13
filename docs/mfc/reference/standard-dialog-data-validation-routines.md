---
title: 標準對話方塊資料驗證常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372908"
---
# <a name="standard-dialog-data-validation-routines"></a>標準對話方塊資料驗證常式

本主題列出了用於常見 MFC 對話方塊控制的標準對話框資料驗證 (DDV) 例程。

> [!NOTE]
> 標準對話框資料交換例程在標頭檔 afxdd_.h 中定義。 但是,應用程式應包括 afxwin.h。

### <a name="ddv-functions"></a>DDV 功能

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|驗證給定控制項值中的字元數不超過給定最大值。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|驗證給定的控制值不超過給定**的 BYTE**範圍。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|驗證給定控制值不超過給定時間範圍。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|驗證給定控制值不超過給定**的雙**範圍。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|驗證給定控件值不超過給定**的 DWORD**範圍。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|驗證給定控制值不超過給定**浮點**範圍。|
|[DDV_MinMaxInt](#ddv_minmaxint)|驗證給定控件值不超過給定**的 int**範圍。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|驗證給定的控制值不超過給定**的長距離**。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|驗證給定的控制值不超過給定**的 LONGLONG**範圍。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|驗證給定控件值不超過給定日期範圍。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|驗證給定控制值不超過給定**的短**距離。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|驗證給定滑塊控件值位於給定範圍內。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|驗證給定控制值不超過給定**的 UINT**範圍。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|驗證給定控制項值介於兩個指定值之間。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|驗證給定的控制值不超過給定**的 ULONGLONG**範圍。|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

呼叫`DDV_MaxChars`以驗證與*值*關聯的控制項中的字元量是否不超過*nChars*。

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*n查理斯*<br/>
允許的最大字元數。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

調用`DDV_MinMaxByte`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許最小值(位元組類型)。

*最大瓦爾*<br/>
允許的最大值(位元組類型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

呼叫`DDV_MinMaxDateTime`以驗證日期和時間選取器控制項[(CDateTimeCtrl)](../../mfc/reference/cdatetimectrl-class.md)中與*refInValue*關聯的時間和日期值是否位於*refMinRange*和*refMaxRange*之間。

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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您無需刪除此物件。

*參考值*<br/>
對與對話框、表單檢視或控制項檢視物件的成員變數關聯的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的引用。 此物件包含要驗證的數據。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

調用`DDV_MinMaxDouble`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(類型**為雙**精度值)。

*最大瓦爾*<br/>
允許的最大值(類型**為雙**精度值)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

調用`DDV_MinMaxDWord`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許最小值(DWORD 類型)。

*最大瓦爾*<br/>
允許的最大值(DWORD 類型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

調用`DDV_MinMaxFloat`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(類型**浮點**)。

*最大瓦爾*<br/>
允許的最大值 **(浮動類型**)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

調用`DDV_MinMaxInt`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(**類型 int**)。

*最大瓦爾*<br/>
允許的最大值(**類型 int**)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

調用`DDV_MinMaxLong`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(**類型長**)。

*最大瓦爾*<br/>
允許的最大值(**類型長**)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

調用`DDV_MinMaxLongLong`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許最小值(龍龍類型)。

*最大瓦爾*<br/>
允許的最大值(龍龍類型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

調用`DDV_MinMaxMonth`以驗證與*refValue*關聯的月份行事曆控制件[(CMonthCalCtrl)](../../mfc/reference/cmonthcalctrl-class.md)中的時間/日期值是否位於*refMinRange*和*refMaxRange*之間。

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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*參考值*<br/>
對類型`CTime`的物件或與`COleDateTime`對話框、窗體視圖或控制項檢視物件的成員變數關聯的物件的引用。 此物件包含要驗證的數據。 MFC 在調用`DDV_MinMaxMonth`時 傳遞此引用。

*refMinRange*<br/>
允許的最小日期/時間值。

*refMaxRange*<br/>
允許的最大日期/時間值。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

調用`DDV_MinMaxShort`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(**短**型)。

*最大瓦爾*<br/>
允許的最大值(**短**型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

調用`DDV_MinMaxSlider`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*值*<br/>
對要驗證的值的引用。 此參數保留或設置滑塊控制項的當前拇指位置。

*明瓦爾*<br/>
允許的最小值。

*最大瓦爾*<br/>
允許的最大值。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。 有關滑動項資訊,請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

調用`DDV_MinMaxUInt`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許最小值(UINT 類型)。

*最大瓦爾*<br/>
允許的最大值(UINT 類型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

調用`DDV_MinMaxULongLong`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許最小值(ULONGLONG 類型)。

*最大瓦爾*<br/>
允許的最大值(ULONGLONG 類型)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

調用`DDV_MinMaxUnsigned`以驗證與*值*關聯的控制項中的值是否介於*最小值和 maxVal*之間。 *maxVal*

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

*值*<br/>
對用於驗證數據的對話框、表單檢視或控制檢視物件的成員變數的引用。

*明瓦爾*<br/>
允許的最小值(**未簽署**類型)。

*最大瓦爾*<br/>
允許的最大值(**類型未符號**)。

### <a name="remarks"></a>備註

關於 DDV 的詳細資訊,請參考[對話資料交換與認證](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

**標題:** afxdd_.h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料交換常式](standard-dialog-data-exchange-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
