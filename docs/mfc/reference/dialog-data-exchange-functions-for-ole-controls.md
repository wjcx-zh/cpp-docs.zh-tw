---
title: OLE 控制項的對話方塊資料交換函式
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: b5a7263ae5cac81508ab2450a530132879ed45b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222819"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控制項的對話方塊資料交換函式

本主題列出在對話方塊、表單檢視或控制項視圖物件中的 OLE 控制項屬性與對話方塊、表單檢視或控制項視圖物件的資料成員之間交換資料時，所用的 DDX_OC 函數。

### <a name="ddx_oc-functions"></a>DDX_OC 函式

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理 OLE 控制項的屬性與**bool**資料成員之間的**BOOL**資料傳輸。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理 OLE 控制項的唯讀屬性與**bool**資料成員之間的**BOOL**資料傳輸。|
|[DDX_OCColor](#ddx_occolor)|管理 OLE 控制項的屬性與**OLE_COLOR**資料成員之間**OLE_COLOR**資料的傳輸。|
|[DDX_OCColorRO](#ddx_occolorro)|管理 OLE 控制項的唯讀屬性與**OLE_COLOR**資料成員之間**OLE_COLOR**資料的傳輸。|
|[DDX_OCFloat](#ddx_ocfloat)|管理 **`float`** **`double`** OLE 控制項的屬性和 **`float`** （或 **`double`** ）資料成員之間的資料傳輸（或）。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理 **`float`** **`double`** OLE 控制項的唯讀屬性和 **`float`** （或 **`double`** ）資料成員之間的資料傳輸（或）。|
|[DDX_OCInt](#ddx_ocint)|管理 **`int`** **`long`** OLE 控制項的屬性和 **`int`** （或 **`long`** ）資料成員之間的資料傳輸（或）。|
|[DDX_OCIntRO](#ddx_ocintro)|管理 **`int`** **`long`** OLE 控制項的唯讀屬性和 **`int`** （或 **`long`** ）資料成員之間的資料傳輸（或）。|
|[DDX_OCShort](#ddx_ocshort)|管理 **`short`** OLE 控制項的屬性與資料成員之間的資料傳輸 **`short`** 。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理 **`short`** OLE 控制項的唯讀屬性與資料成員之間的資料傳輸 **`short`** 。|
|[DDX_OCText](#ddx_octext)|管理 OLE 控制項的屬性與**cstring**資料成員之間的**CString**資料傳輸。|
|[DDX_OCTextRO](#ddx_octextro)|管理 OLE 控制項的唯讀屬性與**cstring**資料成員之間的**CString**資料傳輸。|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

函 `DDX_OCBool` 式會管理在對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的屬性與對話方塊、表單檢視或控制項視圖物件的**bool**資料成員之間的**BOOL**資料傳送。

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭：** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

函 `DDX_OCBoolRO` 式會在對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的唯讀屬性與對話方塊、表單檢視或控制項視圖物件的**BOOL**資料成員之間，管理**BOOL**資料的傳送。

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

函 `DDX_OCColor` 式會管理對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的屬性，以及對話方塊、表單檢視或控制項視圖物件的 OLE_COLOR 資料成員之間，OLE_COLOR 資料的傳輸。

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

函 `DDX_OCColorRO` 式會在對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的唯讀屬性與對話方塊、表單檢視或控制項視圖物件的 OLE_COLOR 資料成員之間，管理 OLE_COLOR 資料的傳輸。

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

函 `DDX_OCFloat` 式會在 **`float`** **`double`** 對話方塊、表單檢視或控制項視圖物件中的 OLE 控制項屬性與 **`float`** **`double`** 對話方塊、表單檢視或控制項視圖物件的（或）資料成員之間，管理（或）資料的傳送。

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

函 `DDX_OCFloatRO` 式會管理 **`float`** （或） [ **`double`** 對話方塊]、[表單檢視] 或 [控制項視圖物件] 中 OLE 控制項的唯讀屬性，以及 **`float`** **`double`** 對話方塊、表單檢視或控制項視圖物件的（或）資料成員之間的資料傳輸。

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

函 `DDX_OCInt` 式會在 **`int`** **`long`** 對話方塊、表單檢視或控制項視圖物件中的 OLE 控制項屬性與 **`int`** **`long`** 對話方塊、表單檢視或控制項視圖物件的（或）資料成員之間，管理（或）資料的傳送。

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

函 `DDX_OCIntRO` 式會管理 **`int`** （或） [ **`long`** 對話方塊]、[表單檢視] 或 [控制項視圖物件] 中 OLE 控制項的唯讀屬性，以及 **`int`** **`long`** 對話方塊、表單檢視或控制項視圖物件的（或）資料成員之間的資料傳輸。

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

函 `DDX_OCShort` 式會管理對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的屬性與對話方塊、表單檢視或控制項視圖物件的簡短資料成員之間的短資料傳輸。

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

函 `DDX_OCShortRO` 式會管理對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的唯讀屬性與對話方塊、表單檢視或控制項視圖物件的簡短資料成員之間的短資料傳輸。

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

**DDX_OCText**函式會管理對話方塊、表單檢視或控制項視圖物件中 OLE 控制項的屬性，以及對話方塊、表單檢視或控制項視圖物件的**CString**資料成員之間的**CString**資料傳送。

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
**CDataExchange**物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

`DDX_OCTextRO` 函式可管理對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的唯讀屬性，與對話方塊、表單檢視或控制項檢視物件的 `CString` 資料成員之間的 `CString` 資料傳輸。

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
