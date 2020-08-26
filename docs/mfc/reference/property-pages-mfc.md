---
title: 屬性頁 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 9a04395aec8c2eb968e5cefaf410643a1ce03e32
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843582"
---
# <a name="property-pages-mfc"></a>屬性頁 (MFC)

屬性頁會在可自訂的圖形化介面中顯示特定 OLE 控制項屬性的目前值，藉由支援根據對話方塊資料交換 (DDX) 的資料對應機制，來進行流覽和編輯。

此資料對應機制會將屬性頁控制項對應至 OLE 控制項的個別屬性。 控制項屬性的值會反映屬性頁面控制項的狀態或內容。 屬性頁控制項和屬性之間的對應是由屬性頁成員函式中 **DDP_** 函式呼叫所指定 `DoDataExchange` 。 以下是 **DDP_** 函式的清單，這些函式會使用控制項的屬性頁來交換輸入的資料：

### <a name="property-page-data-transfer"></a>屬性頁面資料傳輸

|名稱|描述|
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|使用控制項的屬性，將選取的字串在下拉式方塊中的索引連結。|
|[DDP_CBString](#ddp_cbstring)|將下拉式方塊中選取的字串連結至控制項的屬性。 選取的字串可以用與屬性值相同的字母開頭，但不需要完全相符。|
|[DDP_CBStringExact](#ddp_cbstringexact)|將下拉式方塊中選取的字串連結至控制項的屬性。 選取的字串和屬性的字串值必須完全相符。|
|[DDP_Check](#ddp_check)|將控制項屬性頁中的核取方塊連結至控制項的屬性。|
|[DDP_LBIndex](#ddp_lbindex)|使用控制項的屬性，將選取的字串在清單方塊中的索引連結。|
|[DDP_LBString](#ddp_lbstring)|將清單方塊中選取的字串連結至控制項的屬性。 選取的字串可以用與屬性值相同的字母開頭，但不需要完全相符。|
|[DDP_LBStringExact](#ddp_lbstringexact)|將清單方塊中選取的字串連結至控制項的屬性。 選取的字串和屬性的字串值必須完全相符。|
|[DDP_PostProcessing](#ddp_postprocessing)|從您的控制項完成屬性值的傳送。|
|[DDP_Radio](#ddp_radio)|將控制項屬性頁中的選項按鈕群組連結至控制項的屬性。|
|[DDP_Text](#ddp_text)|將控制項屬性頁中的控制項連結至控制項的屬性。 此函式會處理數種不同類型的屬性，例如 **`double`** 、、 **`short`** BSTR 和 **`long`** 。|

如需有關 `DoDataExchange` 函數和屬性頁的詳細資訊，請參閱 [ActiveX 控制項：屬性頁](../../mfc/mfc-activex-controls-property-pages.md)一文。

以下是用來建立和管理 OLE 控制項屬性頁的宏清單：

### <a name="property-pages"></a>屬性頁

|名稱|描述|
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|開始屬性頁識別碼的清單。|
|[END_PROPPAGEIDS](#end_proppageids)|結束屬性頁面識別碼的清單。|
|[PROPPAGEID](#proppageid)|宣告控制項類別的屬性頁。|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a> DDP_CBIndex

呼叫您屬性頁的 `DoDataExchange` 函式中的這個函式，來同步處理整數屬性的值與在屬性頁中下拉式方塊裡目前選取範圍的索引。

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
下拉式方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定的下拉式方塊控制項交換之控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBIndex` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a> DDP_CBString

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以在屬性頁上的下拉式方塊中，同步處理字串屬性的值與目前的選取範圍。

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
下拉式方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定的下拉式方塊字串交換之控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBString` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a> DDP_CBStringExact

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以同步處理完全符合屬性頁下拉式方塊中目前選取範圍的字串屬性值。

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
下拉式方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定的下拉式方塊字串交換之控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBStringExact` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_check"></a><a name="ddp_check"></a> DDP_Check

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以同步處理屬性的值與相關聯的屬性頁核取方塊控制項。

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
核取方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定之核取方塊控制項交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Check` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a> DDP_LBIndex

在屬性頁的函式中呼叫此函 `DoDataExchange` 式，以將整數屬性的值與屬性頁上清單方塊中目前選取範圍的索引進行同步處理。

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
清單方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定清單方塊字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBIndex` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a> DDP_LBString

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以在屬性頁上的清單方塊中，同步處理字串屬性的值與目前的選取範圍。

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
清單方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定清單方塊字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBString` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a> DDP_LBStringExact

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以同步處理完全符合屬性頁清單方塊中目前選取範圍的字串屬性值。

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
清單方塊控制項的資源識別碼，與 *pszPropName*所指定的控制項屬性相關聯。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*所指定清單方塊字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBStringExact` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a> DDP_PostProcessing

在屬性頁的函式中呼叫此函式 `DoDataExchange` ，以在儲存屬性值時，完成將屬性值從屬性頁傳送至控制項的作業。

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

### <a name="remarks"></a>備註

完成所有資料交換函式之後，應該呼叫此函式。 例如：

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_radio"></a><a name="ddp_radio"></a> DDP_Radio

在控制項的函式中呼叫此函式 `DoPropExchange` ，以將屬性的值與相關聯的 [屬性頁] 選項按鈕控制項進行同步處理。

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
與 *pszPropName*指定的控制項屬性相關聯之選項按鈕控制項的資源識別碼。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與依 *識別碼*指定之選項按鈕控制項交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Radio` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="ddp_text"></a><a name="ddp_text"></a> DDP_Text

在控制項的函式中呼叫此函式 `DoDataExchange` ，以同步處理屬性值與相關聯的屬性頁面控制項。

```cpp
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*id*<br/>
與 *pszPropName*指定的控制項屬性相關聯之控制項的資源識別碼。

*成員*<br/>
與 *id* 所指定之屬性頁控制項相關聯的成員變數，以及由 *pszPropName*指定的屬性。

*pszPropName*<br/>
要與 *id*指定的控制項交換之控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Text` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a> BEGIN_PROPPAGEIDS

開始定義控制項的屬性頁面識別碼清單。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>參數

*class_name*<br/>
要指定屬性頁的控制項類別名稱。

*計數*<br/>
控制項類別所使用的屬性頁數目。

### <a name="remarks"></a>備註

在為您的類別定義成員函式的 ( .cpp) 檔中，使用 BEGIN_PROPPAGEIDS 宏來啟動屬性頁清單，然後為每個屬性頁加入宏專案，然後使用 END_PROPPAGEIDS 宏來完成屬性頁清單。

如需屬性頁的詳細資訊，請參閱 [ActiveX 控制項：屬性頁（Property pages](../../mfc/mfc-activex-controls-property-pages.md)）一文。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="end_proppageids"></a><a name="end_proppageids"></a> END_PROPPAGEIDS

結束屬性頁面識別碼清單的定義。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
擁有屬性頁的控制項類別名稱。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="proppageid"></a><a name="proppageid"></a> PROPPAGEID

加入可供您的 OLE 控制項使用的屬性頁。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>參數

*Clsid*<br/>
屬性頁的唯一類別識別碼。

### <a name="remarks"></a>備註

所有的 PROPPAGEID 宏都必須放在控制項的執行檔中的 BEGIN_PROPPAGEIDS 和 END_PROPPAGEIDS 宏之間。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
