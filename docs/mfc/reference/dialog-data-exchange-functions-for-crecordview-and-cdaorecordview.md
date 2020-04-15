---
title: CRecordView 和 CDaoRecordView 的對話方塊資料交換函式
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365781"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的對話方塊資料交換函式

本主題列出了用於在[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)窗體或[CDaoRecordset 窗體](../../mfc/reference/cdaorecordset-class.md)之間交換數據DDX_Field[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)函數。 DAO 與 Access 資料庫一起使用,並通過 Office 2013 支援。 DAO 3.6 是最終版本,它被視為過時版本。

> [!NOTE]
> DDX_Field函數類似於 DDX 函數,因為它們與窗體中的控制件交換數據。 但與 DDX 不同,它們與檢視關聯的記錄集物件的欄位交換數據,而不是與記錄視圖本身的欄位交換數據。 有關詳細資訊,請參閱`CRecordView`類`CDaoRecordView`和 。

### <a name="ddx_field-functions"></a>DDX_Field功能

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|在[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)中的組合框中,在記錄集欄位數據成員和當前選擇的索引之間傳輸整數數據。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|在`CString`記錄集欄位數據成員`CRecordView`和`CDaoRecordView`或中的組合框的編輯控制件之間傳輸數據。 將資料從記錄集移動到控制項時,此函數將在組合框中選擇以指定字串中的字元開頭的項。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|在`CString`記錄集欄位數據成員`CRecordView`和`CDaoRecordView`或中的組合框的編輯控制件之間傳輸數據。 將資料從記錄集移動到控制項時,此函數將在組合框中選擇與指定字串完全匹配的項。|
|[DDX_FieldCheck](#ddx_fieldcheck)|在記錄集欄位數據成員和`CRecordView``CDaoRecordView`或中的複選框之間傳輸布爾資料。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|在 記錄集欄位資料成員`CRecordView`和`CDaoRecordView`或中的清單框中的當前選取內容的索引之間傳輸整數數據。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理在清單框控制項和記錄集的欄位資料成員之間傳輸[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料。 將資料從記錄集移動到控制項時,此函數將在清單框中選擇以指定字串中的字元開頭的項。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理清單框控制項`CString`和記錄集的欄位數據成員之間的資料傳輸。 將資料從記錄集移動到控制項時,此函數將選擇與指定字串完全匹配的第一個項。|
|[DDX_FieldRadio](#ddx_fieldradio)|在記錄集欄位數據成員和`CRecordView``CDaoRecordView`或中的一組單選按鈕之間傳輸整數數據。|
|[DDX_FieldScroll](#ddx_fieldscroll)|設置或獲取`CRecordView``CDaoRecordView`或中的滾動條控制的滾動位置。 從[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)功能呼叫。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步記錄檢視中滑塊控制項的拇指位置和記錄集的`int`欄位數據成員。 |
|[DDX_FieldText](#ddx_fieldtext)|多載的版本可供傳輸`int`， **UINT**， **long**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float****雙**，**簡短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，以及[COleCurrency](../../mfc/reference/colecurrency-class.md)之間的資料錄集欄位資料成員和編輯資料方塊`CRecordView`或`CDaoRecordView`。|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

該`DDX_FieldCBIndex`函數同步記錄檢視中組合框控件的清單框控制項中所選項的索引以及與記錄檢視關聯的記錄集`int`的欄位數據成員。

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*指數*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

將數據從記錄集移動到控制項時,此函數根據*索引*中指定的值在控制項中設置選擇。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則 MFC 將索引的值設定為 0。 在從控制者傳輸到記錄集時,如果控制項為空,或者如果未選擇任何項,則記錄集欄位設置為 0。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 該示例與`DDX_FieldCBIndex`的範例類似。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

函式會管理`CString`記錄視圖中下拉式方塊控制項的編輯控制項與記錄視圖相關聯之記錄集的欄位資料成員之間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸。`DDX_FieldCBString`

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移動到控制項時,此函數將組合框中的當前選擇設置為以*值*中指定的字串中的字元開頭的第一行。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則從組合框中刪除任何選擇,組合框的編輯控制件設定為空。 在從控制者傳輸到記錄集時,如果控制項為空,則如果欄位允許,記錄集欄位將設置為 Null。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 該示例包括對`DDX_FieldCBString`的調用。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

函式會管理`CString`記錄視圖中下拉式方塊控制項的編輯控制項與記錄視圖相關聯之記錄集的欄位資料成員之間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸。`DDX_FieldCBStringExact`

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移動到控制項時,此函數將組合框中的當前選擇設置為與*值*中指定的字串完全符合的第一行。 在從記錄集傳輸到控制項時,如果記錄集欄位為 NULL,則從組合框中刪除任何選擇,組合框的編輯框設置為空。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位將設置為 NULL。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldCBStringExact`將類似。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

該`DDX_FieldCheck`函數管理在對話框、表單檢視或控制項檢視物件的複選框控制項和對話框、表單檢視或控制元件檢視物件的**int**資料成員之間傳輸**int**資料。

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的複選框控制項的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

呼叫`DDX_FieldCheck`時,*值*設定為複選框控制的當前狀態,或者控制者的狀態設定為*值*,具體取決於傳輸方向。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

該`DDX_FieldLBIndex`函數同步記錄檢視中的清單框控制項中所選項的索引以及與記錄檢視關聯的記錄集的**int**欄位資料成員。

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*指數*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

將數據從記錄集移動到控制項時,此函數根據*索引*中指定的值在控制項中設置選擇。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則 MFC 將索引的值設定為 0。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位設置為 0。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext)

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

會將記錄視圖中清單方塊控制項目前的選取範圍複製到與記錄視圖相關聯之記錄集的 [CString](../../atl-mfc-shared/reference/cstringt-class.md)欄位資料`DDX_FieldLBString`成員。

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

在相反的方向上,此函數將列表框中的當前選擇設置為以*值*指定的字串中的字元開頭的第一行。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則從清單框中刪除任何選擇。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位將設置為 Null。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldLBString`將類似。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

函式會將記錄視圖中清單方塊控制項的目前選取範圍複製到與記錄視圖相關聯之記錄集的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 欄位資料成員。`DDX_FieldLBStringExact`

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

在相反的方向上,此函數將列表框中的當前選擇設置為與*值*中指定的字串完全相同的第一行。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則從清單框中刪除任何選擇。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位將設置為 Null。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldLBStringExact`將類似。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

該`DDX_FieldRadio`函數將記錄檢視的記錄集的零基**int**成員變數與記錄檢視中一組單選按鈕中的當前選定的單選按鈕關聯。

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView 或 CDaoRecordView](../../mfc/reference/crecordview-class.md)物件中相鄰單選按鈕控制元件組中的第一[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)個(具有樣式WS_GROUP)的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

從記錄集欄位傳輸到檢視時,此功能將打開*第 n 個*單選按鈕(從零開始),然後關閉其他按鈕。 在相反的方向上,此函數將記錄集欄位設置為當前打開(已選中)的單選按鈕的定單數。 在從記錄集傳輸到控制項時,如果記錄集欄位為「空」,則不選擇任何按鈕。 在從控制者傳輸到記錄集時,如果未選擇控制項,則如果欄位允許,記錄集欄位將設置為 Null。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldRadio`將類似。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

該`DDX_FieldScroll`函數同步記錄檢視中滾動條控制項的滾動位置以及與記錄檢視關聯的記錄集**的 int**欄位資料成員(或與選擇映射到它的任何整數變數一起)。

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView 或 CDaoRecordView](../../mfc/reference/crecordview-class.md)物件中相鄰單選按鈕控制元件組中的第一[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)個(具有樣式WS_GROUP)的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

將資料從紀錄集移至控制項時,此函數會捲軸控制元件的捲軸位置設定為值中指定的*值*。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則滾動條控制元件設定為 0。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位的值為 0。

如果使用基於 ODBC 的類,請使用第一個版本。 如果使用基於 DAO 的類,請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldScroll`將類似。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

該`DDX_FieldSlider`函數同步記錄檢視中滑塊控制項的拇指位置以及與記錄檢視關聯的記錄集**的 int**欄位資料成員(或與選擇映射到的任何整數變數一起)。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
滑塊控制件的資源 ID。

*值*<br/>
對要交換的值的引用。 此參數保留或將用於設置滑塊控制項的當前拇指位置。

*pRecordset*<br/>
指向與其交換數據的關聯`CRecordset``CDaoRecordset`或物件的指標。

### <a name="remarks"></a>備註

將資料從紀錄集移至滑動區時,此函數會滑入位置設定為值中指定的*值*。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則滑塊控制項的位置設定為 0。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位的值為 0。

`DDX_FieldSlider`不會使用能夠設置範圍的滑塊控件交換範圍資訊,而不僅僅是位置。

如果使用基於 ODBC 的類,請使用函數的第一個重寫。 使用第二個覆蓋與基於 DAO 的類。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。 關於 DDX`CRecordView``CDaoRecordView`與欄位的詳細資訊,請參閱[記錄檢視](../../data/record-views-mfc-data-access.md)。 有關滑動項資訊,請參閱[使用 CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>範例

有關一般DDX_Field示例,請參閱[DDX_FieldText。](#ddx_fieldtext) 調用`DDX_FieldSlider`將類似。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

函式會管理在編輯方塊控制項與的欄位資料成員之間，**int**、**short**、**long**、DWORD、[CString](../../atl-mfc-shared/reference/cstringt-class.md)、**float**、**double**、**BOOL**或 **BYTE** 資料的傳送。`DDX_FieldText`集中。

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項的 ID。

*值*<br/>
對關聯`CRecordset``CDaoRecordset`或物件中的欄位數據成員的引用。 值的資料類型`DDX_FieldText`取決於 您使用的重載版本。

*pRecordset*<br/>
指向與其中交換數據的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。 此指標允許`DDX_FieldText`檢測和設置 Null 值。

### <a name="remarks"></a>備註

對於[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)`DDX_FieldText`物件,還要管理傳輸[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COle 貨幣](../../mfc/reference/colecurrency-class.md)值。 空編輯框控制器指示空值。 在從記錄集傳輸到控制項時,如果記錄集欄位為 Null,則編輯框設置為空。 在從控制者傳輸到記錄集時,如果控制項為空,則記錄集欄位將設置為 Null。

如果使用基於 ODBC 的類,請使用具有[CRecordset](../../mfc/reference/crecordset-class.md)參數的版本。 如果使用基於 DAO 的類,請使用具有[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)參數的版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位的 DDX 的範例和詳細資訊,請參閱文章[「記錄檢視](../../data/record-views-mfc-data-access.md)」。

### <a name="example"></a>範例

[CRecordView](../../mfc/reference/crecordview-class.md) 的`DoDataExchange`下列函式包含`DDX_FieldText`三種資料類型的函式呼叫： `IDC_COURSELIST`是下拉式方塊，其他兩個控制項是編輯方塊。 對於 DAO 程式設計 *,m_pSet*參數是指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset 的](../../mfc/reference/cdaorecordset-class.md)指標。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)
