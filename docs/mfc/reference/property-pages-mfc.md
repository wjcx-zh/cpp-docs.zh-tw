---
title: 屬性頁 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 1064cd99d1820ae8865fa632c3097441172c78c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372988"
---
# <a name="property-pages-mfc"></a>屬性頁 (MFC)

屬性頁透過支援基於對話框資料交換 (DDX) 的資料映射機制,在可自訂的圖形介面中顯示特定 OLE 控制項屬性的當前值,以便查看和編輯。

此資料對應機制將屬性頁控制件映射到 OLE 控制件的各個屬性。 控件屬性的值反映屬性頁控件的狀態或內容。 屬性頁控制項和屬性之間的映射由屬性頁`DoDataExchange`成員函數中**DDP_** 函數調用指定。 以下是交換使用控制的屬性頁輸入的資料**的DDP_** 函數的清單:

### <a name="property-page-data-transfer"></a>屬性頁資料傳輸

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|將選取的字串的索引連結到具有控制項屬性的組合框中。|
|[DDP_CBString](#ddp_cbstring)|將選取的字串連結到組合框中具有控制項的屬性。 所選字串可以以與屬性值相同的字母開頭,但不需要與屬性的值完全匹配。|
|[DDP_CBStringExact](#ddp_cbstringexact)|將選取的字串連結到組合框中具有控制項的屬性。 所選字串和屬性的字串值必須完全匹配。|
|[DDP_Check](#ddp_check)|將控制項的屬性頁中的複選框與控制項的屬性連結。|
|[DDP_LBIndex](#ddp_lbindex)|在清單框中連結所選字串的索引,並帶有控制項的屬性。|
|[DDP_LBString](#ddp_lbstring)|將選取的字串連結到清單框中具有控制項的屬性。 所選字串可以以與屬性值相同的字母開頭,但不必完全匹配它。|
|[DDP_LBStringExact](#ddp_lbstringexact)|將選取的字串連結到清單框中具有控制項的屬性。 所選字串和屬性的字串值必須完全匹配。|
|[DDP_PostProcessing](#ddp_postprocessing)|完成從控制件轉移屬性值。|
|[DDP_Radio](#ddp_radio)|將控制項的屬性頁中的單選按鈕組與控制項的屬性連結。|
|[DDP_Text](#ddp_text)|將控制項的屬性頁中的控制項與控制項的屬性連結。 此函數處理幾種不同類型的屬性,如**雙**、**短**、BSTR 與**長**。|

有關`DoDataExchange`函數和屬性頁的詳細資訊,請參閱[文章 ActiveX 控制件:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。

以下是用來建立與管理 OLE 控制的屬性頁的巨集清單:

### <a name="property-pages"></a>屬性頁

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|開始屬性頁 I 的清單。|
|[END_PROPPAGEIDS](#end_proppageids)|結束屬性頁 I 的清單。|
|[PROPPAGEID](#proppageid)|聲明控件類的屬性頁。|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

呼叫您屬性頁的 `DoDataExchange` 函式中的這個函式，來同步處理整數屬性的值與在屬性頁中下拉式方塊裡目前選取範圍的索引。

```
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
與*pszPropName*指定的控制項屬性關聯的組合框控制件的資源識別碼。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的組合框控制元件交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBIndex` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

在屬性頁的`DoDataExchange`函數中調用此函數,以將字串屬性的值與屬性頁上的組合框中的當前選擇同步。

```
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
與*pszPropName*指定的控制項屬性關聯的組合框控制件的資源識別碼。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的組合框字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBString` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

在屬性頁的`DoDataExchange`函數中調用此函數以同步與屬性頁上組合框中的當前選擇完全匹配的字串屬性的值。

```
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
與*pszPropName*指定的控制項屬性關聯的組合框控制件的資源識別碼。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的組合框字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_CBStringExact` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

在屬性頁的`DoDataExchange`函數中調用此函數,以將屬性的值與關聯的屬性頁複選框控制元件同步。

```
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
與*pszPropName*指定的控制項屬性關聯的複選方塊控制的資源 ID。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*ID*指定的複選方塊交換的控制項屬性的名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Check` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

在屬性頁的`DoDataExchange`函數中調用此函數,以在屬性頁上的清單框中將整數屬性的值與當前選擇的索引同步。

```
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
清單盒控制項的資源 ID 與*pszPropName*指定的控制項屬性相關聯。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的清單框字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBIndex` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

在屬性頁的`DoDataExchange`函數中調用此函數,以將字串屬性的值與屬性頁上的清單框中的當前選擇同步。

```
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
清單盒控制項的資源 ID 與*pszPropName*指定的控制項屬性相關聯。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的清單框字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBString` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

在屬性頁的`DoDataExchange`函數中調用此函數以同步與屬性頁上列表框中的當前選擇完全匹配的字串屬性的值。

```
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
清單盒控制項的資源 ID 與*pszPropName*指定的控制項屬性相關聯。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的清單框字串交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_LBStringExact` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

在屬性頁的`DoDataExchange`函數中調用此函數,以在保存屬性值時完成屬性值從屬性頁傳輸到控制項。

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

### <a name="remarks"></a>備註

完成所有數據交換函數後,應調用此功能。 例如：

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

在控制項的`DoPropExchange`函數中調用此函數,以將屬性的值與關聯的屬性頁單選按鈕控制元件同步。

```
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
與*pszPropName*指定的控制項屬性關聯的單選按鈕控制件的資源 ID。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*ID*指定的單選按鈕控制元件交換的控制項屬性的名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Radio` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

在控制項的`DoDataExchange`函數中調用此函數以將屬性的值與關聯的屬性頁控制元件同步。

```
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
與*pszPropName*指定的控制項屬性關聯的控制項的資源 ID。

*成員*<br/>
與*id*指定的屬性頁控制件和*pszPropName*指定的屬性關聯的成員變數。

*pszProp名稱*<br/>
要與*id*指定的控制項交換的控制項屬性的屬性名稱。

### <a name="remarks"></a>備註

應該在對應的 `DDX_Text` 函式呼叫之前呼叫此函式。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

開始定義控制件的屬性頁頁 I。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>參數

*class_name*<br/>
為其指定屬性頁的屬性類的名稱。

*count*<br/>
控制項類使用的屬性頁數。

### <a name="remarks"></a>備註

在定義類成員函數的實現 (.cpp) 檔中,使用BEGIN_PROPPAGEIDS宏啟動屬性頁清單,然後為每個屬性頁添加宏條目,然後使用END_PROPPAGEIDS宏完成屬性頁清單。

有關屬性頁的詳細資訊,請參閱文章[ActiveX 控制件:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

結束屬性頁識別清單的定義。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
擁有屬性頁的控制類類的名稱。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PropPAGEID

添加屬性頁供 OLE 控制件使用。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>參數

*Clsid*<br/>
屬性頁的唯一類 ID。

### <a name="remarks"></a>備註

所有 PROPPAGEID 宏都必須放置在控制項的實現檔中的BEGIN_PROPPAGEIDS和END_PROPPAGEIDS宏之間。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
