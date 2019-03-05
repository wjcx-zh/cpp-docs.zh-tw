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
ms.openlocfilehash: df96d44cefeb15d89653538c3006d109a97a21a7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298252"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控制項的對話方塊資料交換函式

本主題列出用來交換資料的屬性對話方塊、 表單檢視或控制項檢視物件中 OLE 控制項和對話方塊、 表單檢視或控制項檢視物件的資料成員之間的 DDX_OC 函式。

### <a name="ddxoc-functions"></a>DDX_OC 函式

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理傳送**BOOL** OLE 控制項的屬性之間的資料並**BOOL**資料成員。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理傳送**BOOL** OLE 控制項的唯讀屬性之間的資料並**BOOL**資料成員。|
|[DDX_OCColor](#ddx_occolor)|管理傳送**OLE_COLOR** OLE 控制項的屬性之間的資料並**OLE_COLOR**資料成員。|
|[DDX_OCColorRO](#ddx_occolorro)|管理傳送**OLE_COLOR** OLE 控制項的唯讀屬性之間的資料並**OLE_COLOR**資料成員。|
|[DDX_OCFloat](#ddx_ocfloat)|管理傳送**浮點數**(或**double**) 的 OLE 控制項屬性之間的資料和**float** (或**double**) 資料成員。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理傳送**浮點數**(或**double**) 的 OLE 控制項的唯讀屬性之間的資料和**float** (或**double**) 資料成員。|
|[DDX_OCInt](#ddx_ocint)|管理傳送**int** (或**長**) 的 OLE 控制項屬性之間的資料並**int** (或**長**) 資料成員。|
|[DDX_OCIntRO](#ddx_ocintro)|管理傳送**int** (或**長**) 的 OLE 控制項的唯讀屬性之間的資料並**int** (或**長**) 資料成員。|
|[DDX_OCShort](#ddx_ocshort)|管理傳送**簡短**OLE 控制項的屬性之間的資料並**簡短**資料成員。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理傳送**簡短**OLE 控制項的唯讀屬性之間的資料並**簡短**資料成員。|
|[DDX_OCText](#ddx_octext)|管理傳送**CString** OLE 控制項的屬性之間的資料並**CString**資料成員。|
|[DDX_OCTextRO](#ddx_octextro)|管理傳送**CString** OLE 控制項的唯讀屬性之間的資料並**CString**資料成員。|

##  <a name="ddx_ocbool"></a>  DDX_OCBool

`DDX_OCBool`函式可管理的傳輸**BOOL**  對話方塊中中, OLE 控制項的屬性之間的資料表單檢視或控制項檢視物件並**BOOL**資料成員的對話方塊中，表單 檢視中，或控制項檢視物件。

```
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

##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO

`DDX_OCBoolRO`函式可管理的傳輸**BOOL**  對話方塊中中, OLE 控制項的唯讀屬性之間的資料表單檢視或控制項檢視物件並**BOOL**對話方塊中，資料成員表單檢視或控制項檢視物件。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_occolor"></a>  DDX_OCColor

`DDX_OCColor`函式可管理 OLE_COLOR 之間傳送資料的 OLE 控制項在對話方塊中，表單 檢視中，屬性或控制項檢視物件和 OLE_COLOR 資料成員的對話方塊中，表單檢視，或控制項檢視物件。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_occolorro"></a>  DDX_OCColorRO

`DDX_OCColorRO`函式可管理 OLE_COLOR 之間傳送資料的 OLE 控制項在對話方塊中，表單 檢視中，唯讀屬性或控制項檢視物件和 OLE_COLOR 資料成員的對話方塊中，表單檢視，或控制項檢視物件。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocfloat"></a>  DDX_OCFloat

`DDX_OCFloat`函式可管理的傳輸**浮點數**(或**double**) 的 OLE 控制項在對話方塊中，屬性之間的資料表單檢視或控制項檢視物件和**float**(或**double**) 對話方塊、 表單檢視或控制項檢視物件的資料成員。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO

`DDX_OCFloatRO`函式可管理的傳輸**浮點數**(或**double**) 的 OLE 控制項在對話方塊中，唯讀屬性之間的資料表單檢視或控制項檢視物件和**浮點數**(或**double**) 對話方塊、 表單檢視或控制項檢視物件的資料成員。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocint"></a>  DDX_OCInt

`DDX_OCInt`函式可管理的傳輸**int** (或**long**) 的 OLE 控制項在對話方塊中，屬性之間的資料表單檢視或控制項檢視物件和**int**(或**長**) 對話方塊、 表單檢視或控制項檢視物件的資料成員。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocintro"></a>  DDX_OCIntRO

`DDX_OCIntRO`函式可管理的傳輸**int** (或**long**) 的 OLE 控制項在對話方塊中，唯讀屬性之間的資料表單檢視或控制項檢視物件和**int**(或**長**) 對話方塊、 表單檢視或控制項檢視物件的資料成員。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocshort"></a>  DDX_OCShort

`DDX_OCShort`函式可管理的對話方塊中，表單檢視中 OLE 控制項屬性之間傳輸短的資料或控制項檢視物件且短暫的資料成員的對話方塊中，表單檢視，或控制項檢視物件。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO

`DDX_OCShortRO`函式可管理簡短之間傳送資料的 OLE 控制項在對話方塊中，表單 檢視中，唯讀屬性或控制項檢視物件且短暫的資料成員的對話方塊中，表單檢視，或控制項檢視物件。

```
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

  **標頭**afxdisp.h

##  <a name="ddx_octext"></a>  DDX_OCText

**DDX_OCText**函式可管理的傳輸**CString**  對話方塊中中, OLE 控制項的屬性之間的資料表單檢視或控制項檢視物件及**CString**資料對話方塊、 表單檢視或控制項檢視物件的成員。

```
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指標**CDataExchange**物件。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*dispid*<br/>
控制項屬性的分派識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="ddx_octextro"></a>  DDX_OCTextRO

`DDX_OCTextRO` 函式可管理對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的唯讀屬性，與對話方塊、表單檢視或控制項檢視物件的 `CString` 資料成員之間的 `CString` 資料傳輸。

```
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

  **標頭**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
