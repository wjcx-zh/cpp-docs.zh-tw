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
ms.openlocfilehash: 9133c30dd1ac069145862d4bf61ba0bc0d504838
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837355"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控制項的對話方塊資料交換函式

本主題列出在對話方塊、表單檢視或控制項視圖物件的屬性，以及對話方塊、表單檢視或 control view 物件的資料成員之間，用來交換資料的 DDX_OC 函數。

### <a name="ddx_oc-functions"></a>DDX_OC 函式

|名稱|描述|
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理 OLE 控制項的屬性和**bool**資料成員之間的**BOOL**資料傳送。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理 OLE 控制項的唯讀屬性和**bool**資料成員之間的**BOOL**資料傳送。|
|[DDX_OCColor](#ddx_occolor)|管理 OLE 控制項的屬性和**OLE_COLOR**資料成員之間的**OLE_COLOR**資料傳輸。|
|[DDX_OCColorRO](#ddx_occolorro)|管理 OLE 控制項的唯讀屬性和**OLE_COLOR**資料成員之間的**OLE_COLOR**資料傳輸。|
|[DDX_OCFloat](#ddx_ocfloat)|管理 **`float`** **`double`** OLE 控制項的屬性和 **`float`** (或) 資料成員之間的 (或) 資料的傳輸 **`double`** 。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理 **`float`** **`double`** OLE 控制項的唯讀屬性和 **`float`** (或) 資料成員之間的 (或) 資料的傳輸 **`double`** 。|
|[DDX_OCInt](#ddx_ocint)|管理 **`int`** **`long`** OLE 控制項的屬性和 **`int`** (或) 資料成員之間的 (或) 資料的傳輸 **`long`** 。|
|[DDX_OCIntRO](#ddx_ocintro)|管理 **`int`** **`long`** OLE 控制項的唯讀屬性和 **`int`** (或) 資料成員之間的 (或) 資料的傳輸 **`long`** 。|
|[DDX_OCShort](#ddx_ocshort)|管理 **`short`** OLE 控制項屬性和資料成員之間的資料傳輸 **`short`** 。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理 **`short`** OLE 控制項的唯讀屬性和資料成員之間的資料傳輸 **`short`** 。|
|[DDX_OCText](#ddx_octext)|管理 OLE 控制項的屬性和**cstring**資料成員之間的**CString**資料傳輸。|
|[DDX_OCTextRO](#ddx_octextro)|管理 OLE 控制項的唯讀屬性和**cstring**資料成員之間的**CString**資料傳輸。|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a> DDX_OCBool

此函式會在 `DDX_OCBool` 對話方塊、表單檢視或控制項視圖物件的屬性，以及對話方塊、表單檢視或 control view 物件的**bool**資料成員之間，管理**BOOL**資料的傳送。

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

### <a name="requirements"></a>規格需求

  **標頭：** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a> DDX_OCBoolRO

此函 `DDX_OCBoolRO` 式會在對話方塊、表單檢視、控制項視圖物件和對話方塊、表單檢視或 control view 物件的**bool**資料成員中，管理 OLE 控制項的唯讀屬性之間的**BOOL**資料傳送。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a> DDX_OCColor

此函式會在 `DDX_OCColor` 對話方塊、表單檢視或控制項視圖物件的 OLE 控制項屬性，以及對話方塊、表單檢視或 control view 物件的 OLE_COLOR 資料成員之間，管理 OLE_COLOR 資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a> DDX_OCColorRO

此函式會在 `DDX_OCColorRO` 對話方塊、表單檢視或控制項視圖物件的 OLE 控制項唯讀屬性，以及對話方塊、表單檢視或 control view 物件的 OLE_COLOR 資料成員之間，管理 OLE_COLOR 資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a> DDX_OCFloat

函 `DDX_OCFloat` 式會在 **`float`** **`double`** 對話方塊、表單檢視或控制視圖物件中的 OLE 控制項屬性，以及 **`float`** **`double`** 對話方塊、表單檢視或 control view 物件的 (或) 資料成員之間，管理 (或) 資料的傳送。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a> DDX_OCFloatRO

函 `DDX_OCFloatRO` 式會在 **`float`** **`double`** 對話方塊、表單檢視或 control VIEW 物件的 OLE 控制項的唯讀屬性，以及 **`float`** **`double`** 對話方塊、表單檢視或 control view 物件的 (或) 資料成員中管理 (或) 資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a> DDX_OCInt

函 `DDX_OCInt` 式會在 **`int`** **`long`** 對話方塊、表單檢視或控制視圖物件中的 OLE 控制項屬性，以及 **`int`** **`long`** 對話方塊、表單檢視或 control view 物件的 (或) 資料成員之間，管理 (或) 資料的傳送。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a> DDX_OCIntRO

函 `DDX_OCIntRO` 式會在 **`int`** **`long`** 對話方塊、表單檢視或 control VIEW 物件的 OLE 控制項的唯讀屬性，以及 **`int`** **`long`** 對話方塊、表單檢視或 control view 物件的 (或) 資料成員中管理 (或) 資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a> DDX_OCShort

此函式會在 `DDX_OCShort` 對話方塊、表單檢視或控制項視圖物件中的 OLE 控制項屬性和對話方塊、表單檢視或 control view 物件的簡短資料成員之間，管理短資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a> DDX_OCShortRO

此函式會在 `DDX_OCShortRO` 對話方塊、表單檢視或控制項視圖物件的 OLE 控制項唯讀屬性，以及對話方塊、表單檢視或 control view 物件的簡短資料成員之間，管理短資料的傳輸。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_octext"></a><a name="ddx_octext"></a> DDX_OCText

**DDX_OCText**函式會在對話方塊、表單檢視或控制項視圖物件的屬性，以及對話方塊、表單檢視或 control view 物件的**CString**資料成員之間，管理**CString**資料的傳送。

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a> DDX_OCTextRO

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

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
