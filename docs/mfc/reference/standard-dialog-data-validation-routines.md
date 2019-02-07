---
title: 標準對話方塊資料驗證常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: dce982f76e25da424c02d621c1b760ec29e88918
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850160"
---
# <a name="standard-dialog-data-validation-routines"></a>標準對話方塊資料驗證常式

本主題列出常見的 MFC 對話方塊控制項所使用的標準對話方塊資料驗證 (DDV) 常式。

> [!NOTE]
>  標準對話方塊資料交換常式會定義在標頭檔 afxdd_.h。 不過，應用程式應該包含 afxwin.h。

### <a name="ddv-functions"></a>DDV 函式

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|確認指定的控制項值中的字元數目不超過指定的最大值。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|確認指定的控制項值未超過給定**位元組**範圍。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|確認指定的控制項值未超過指定的時間範圍內。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|確認指定的控制項值未超過給定**double**範圍。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|確認指定的控制項值未超過給定**DWORD**範圍。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|確認指定的控制項值未超過給定**浮點數**範圍。|
|[DDV_MinMaxInt](#ddv_minmaxint)|確認指定的控制項值未超過給定**int**範圍。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|確認指定的控制項值未超過給定**長**範圍。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|確認指定的控制項值未超過給定**LONGLONG**範圍。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|確認指定的控制項值未超過指定的日期範圍。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|確認指定的控制項值未超過給定**簡短**範圍。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|確認指定的滑桿控制項值落在指定的範圍內。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|確認指定的控制項值未超過給定**UINT**範圍。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|確認指定的控制項值介於兩個指定的值。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|確認指定的控制項值未超過給定**ULONGLONG**範圍。|

##  <a name="ddv_maxchars"></a>  DDV_MaxChars

呼叫`DDV_MaxChars`若要確認與關聯的控制項中的字元數量*值*不會超過*nChars*。

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*nChars*<br/>
允許的字元數目上限。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

呼叫`DDV_MinMaxByte`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 （位元組類型） 允許。

*maxVal*<br/>
最大值 （位元組類型） 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

呼叫`DDV_MinMaxDateTime`若要確認日期和時間選擇器中的日期/時間值，控制 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 相關聯*refValue*之間*refMinRange*並*refMaxRange*。

```
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
指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。

*refValue*<br/>
參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)或是[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊、 表單檢視或控制項檢視物件的成員變數相關聯的物件。 此物件包含要驗證的資料。

*refMinRange*<br/>
最小日期/時間允許的值。

*refMaxRange*<br/>
允許的最大的日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

呼叫`DDV_MinMaxDouble`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**double**) 允許。

*maxVal*<br/>
最大值 (型別的**double**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

呼叫`DDV_MinMaxDWord`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
允許最小值 （屬於 DWORD 型別）。

*maxVal*<br/>
允許最大值 （屬於 DWORD 型別）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  DDV_MinMaxFloat

呼叫`DDV_MinMaxFloat`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**浮點數**) 允許。

*maxVal*<br/>
最大值 (型別的**浮點數**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

呼叫`DDV_MinMaxInt`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**int**) 允許。

*maxVal*<br/>
最大值 (型別的**int**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

呼叫`DDV_MinMaxLong`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**長**) 允許。

*maxVal*<br/>
最大值 (型別的**長**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

呼叫`DDV_MinMaxLongLong`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小允許 （屬於類型 LONGLONG） 值。

*maxVal*<br/>
最大允許 （屬於類型 LONGLONG） 值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

呼叫`DDV_MinMaxMonth`若要確認在月份行事曆的日期/時間值，控制 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 相關聯*refValue*之間*refMinRange*和*refMaxRange*。

```
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
指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。

*refValue*<br/>
型別的物件的參考`CTime`或`COleDateTime`對話方塊中的成員變數與相關聯，表單檢視，或控制項檢視物件。 此物件包含要驗證的資料。 MFC 傳遞此參考時`DDV_MinMaxMonth`呼叫。

*refMinRange*<br/>
最小日期/時間允許的值。

*refMaxRange*<br/>
允許的最大的日期/時間值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

呼叫`DDV_MinMaxShort`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**簡短**) 允許。

*maxVal*<br/>
最大值 (型別的**簡短**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

呼叫`DDV_MinMaxSlider`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。

*value*<br/>
若要驗證值的參考。 此參數保留或設定滑桿控制項的目前捲動方塊位置。

*minVal*<br/>
允許的最小值。

*maxVal*<br/>
允許的最大值。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 滑桿控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

呼叫`DDV_MinMaxUInt`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
允許最小值 （屬於類型單位）。

*maxVal*<br/>
允許最大值 （屬於類型單位）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

呼叫`DDV_MinMaxULongLong`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
允許最小值 （屬於類型 ULONGLONG）。

*maxVal*<br/>
允許最大值 （屬於類型 ULONGLONG）。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_.h

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

呼叫`DDV_MinMaxUnsigned`驗證控制項中的值是與相關*值*之間*minVal*並*maxVal*。

### <a name="syntax"></a>語法

```
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
對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數的參考。

*minVal*<br/>
最小值 (型別的**不帶正負號**) 允許。

*maxVal*<br/>
最大值 (型別的**不帶正負號**) 允許。

### <a name="remarks"></a>備註

如需 DDV 的詳細資訊，請參閱[ 對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

**標頭：** afxdd_.h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料交換常式](standard-dialog-data-exchange-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)

