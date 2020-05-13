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
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365771"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控制項的對話方塊資料交換函式

本主題列出了用於在對話框、窗體檢視或控制項檢視物件中的 OLE 控制件的屬性與對話框、窗體檢視或控制元件檢視物件的資料成員之間交換數據的DDX_OC函數。

### <a name="ddx_oc-functions"></a>DDX_OC功能

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理**BOOL**資料在 OLE 控制項的屬性和**BOOL**資料成員之間的傳輸。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理**BOOL**資料在 OLE 控制件的唯讀屬性和**BOOL**資料成員之間的傳輸。|
|[DDX_OCColor](#ddx_occolor)|管理**OLE_COLOR**資料在 OLE 控制的屬性和**OLE_COLOR**資料成員之間的傳輸。|
|[DDX_OCColorRO](#ddx_occolorro)|管理**OLE_COLOR**的 OLE 控制件的唯讀屬性和**OLE_COLOR**資料成員之間的傳輸。|
|[DDX_OCFloat](#ddx_ocfloat)|管理 OLE 控制項屬性和**浮點**(或**雙**精度)數據成員之間的**浮點**(或**雙精度**)數據傳輸。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理 OLE 控制項的唯讀屬性和**浮點**(或**雙****精度**)數據成員之間的**浮點**(或雙精度)數據傳輸。|
|[DDX_OCInt](#ddx_ocint)|管理在 OLE 控制的屬性**long**和**int(** 或長)數據成員之間傳輸**int(** 或**長**) 資料。|
|[DDX_OCIntRO](#ddx_ocintro)|管理在 OLE 控制檔**long**的唯讀屬性和**int(** 或長)資料成員之間傳輸**int(** 或**長**) 資料。|
|[DDX_OCShort](#ddx_ocshort)|管理 OLE 控制項屬性和**短**資料成員之間的**短**資料傳輸。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理 OLE 控制項的唯讀屬性和**短**資料成員之間的**短**資料傳輸。|
|[DDX_OCText](#ddx_octext)|管理在 OLE 控制的屬性和**CString**資料成員之間傳輸**CString**資料。|
|[DDX_OCTextRO](#ddx_octextro)|管理在 OLE 控制項的唯讀屬性和**CString**資料成員之間傳輸**CString**資料。|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

該`DDX_OCBool`函數管理**在**對話框、表單檢視或控制項檢視物件中的 OLE 控制項的屬性與對話框、窗體檢視或控制元件檢視物件的**BOOL**資料成員之間的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭：** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

該`DDX_OCBoolRO`函數管理**在**對話框、窗體檢視或控制項檢視物件中的 OLE 控制項的唯讀屬性和對話框、窗體檢視或控制元件檢視物件的**BOOL**資料成員之間的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

該`DDX_OCColor`函數管理在對話框、表單檢視或控制元件檢視物件中的 OLE 控制項的屬性與對話框、窗體檢視或控制元件檢視物件的OLE_COLOR資料成員之間的傳輸OLE_COLOR資料。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

該`DDX_OCColorRO`函數管理在對話框、表單檢視或控制檢視物件的僅讀屬性和對話框、窗體視圖或控制件檢視物件的OLE_COLOR資料成員之間的傳輸OLE_COLOR資料。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

該`DDX_OCFloat`函數管理在對話框、窗體檢視或控制項檢視物件的 OLE 控制項的屬性和對話框、窗體檢視或控制元件檢視物件的**浮點**(或**雙**)數據成員之間的**浮動**(或**雙**)數據之間的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

該`DDX_OCFloatRO`函數管理在對話框、窗體檢視或控制項檢視物件中的 OLE 控制項的唯讀屬性和對話框、窗體檢視或控制元件檢視物件的**浮點**(或**雙**)數據成員之間的**浮動**(或**雙**)數據之間的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

該`DDX_OCInt`函式管理在對話框、表單檢視或控制元件檢視物件中的 OLE 控制項的屬性與對話框、窗體檢視或控制元件檢視物件的**int(** 或**長**)數據成員之間的**int(** 或**長**) 資料之間的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

該`DDX_OCIntRO`函式管理在對話框、表單元件檢視或控制元件檢視物件中的 OLE 控制項的唯讀屬性和對話框、窗體檢視或控制元件檢視物件的**int(** 或**長**)數據成員之間的**int(** 或**長**) 資料的傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

該`DDX_OCShort`函數管理在對話框、窗體檢視或控制項檢視物件中的 OLE 控制項的屬性與對話框、窗體檢視或控制元件檢視物件的短資料成員之間的短資料傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

該`DDX_OCShortRO`函數管理在對話框、窗體檢視或控制項檢視物件中的 OLE 控制項的唯讀屬性和對話框、窗體檢視或控制元件檢視物件的短資料成員之間的短資料傳輸。

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

**DDX_OCText**函數管理**在**對話框、表單檢視或控制元件檢視物件中的 OLE 控制項的屬性與對話框、窗體檢視或控制元件檢視物件的 CString 資料成員之間的**CString**資料傳輸。

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向**CDataExchange**物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或控制項檢視物件中 OLE 控制項的識別碼。

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

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

*不一部分*<br/>
控制項屬性的分派識別碼。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
