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
ms.openlocfilehash: 8b216941837cd79492aa6cb707481073b5321bce
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303442"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的對話方塊資料交換函式

本主題列出用來在[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)表單或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)表單之間交換資料的 DDX_Field 函數。 DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。

> [!NOTE]
>  DDX_Field 函式就像是 DDX 函式，因為它們會與表單中的控制項交換資料。 但與 DDX 不同的是，它們會與視圖相關聯之記錄集物件的欄位交換資料，而不是使用記錄視圖本身的欄位。 如需詳細資訊，請參閱類別 `CRecordView` 和 `CDaoRecordView`。

### <a name="ddx_field-functions"></a>DDX_Field 函式

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|在[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)的下拉式方塊中，傳送記錄集欄位資料成員與目前選取範圍的索引之間的整數資料。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|在記錄集欄位資料成員與 `CRecordView` 或 `CDaoRecordView`中下拉式方塊的編輯控制項之間傳輸 `CString` 資料。 將資料從記錄集移至控制項時，此函式會在下拉式方塊中選取以指定之字串中的字元開頭的專案。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|在記錄集欄位資料成員與 `CRecordView` 或 `CDaoRecordView`中下拉式方塊的編輯控制項之間傳輸 `CString` 資料。 將資料從記錄集移至控制項時，此函式會在下拉式方塊中選取與指定字串完全相符的專案。|
|[DDX_FieldCheck](#ddx_fieldcheck)|在記錄集欄位資料成員與 `CRecordView` 或 `CDaoRecordView`中的核取方塊之間傳輸布林資料。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|在 `CRecordView` 或 `CDaoRecordView`的清單方塊中，傳送記錄集欄位資料成員與目前選取範圍的索引之間的整數資料。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理清單方塊控制項與記錄集的欄位資料成員之間的[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料傳送。 將資料從記錄集移至控制項時，此函式會選取清單方塊中以指定字串中的字元開頭的專案。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理清單方塊控制項與記錄集的欄位資料成員之間 `CString` 資料的傳輸。 將資料從記錄集移至控制項時，此函數會選取與指定字串完全相符的第一個專案。|
|[DDX_FieldRadio](#ddx_fieldradio)|在記錄集欄位資料成員與 `CRecordView` 或 `CDaoRecordView`中的一組選項按鈕之間傳輸整數資料。|
|[DDX_FieldScroll](#ddx_fieldscroll)|設定或取得捲軸控制項在 `CRecordView` 或 `CDaoRecordView`中的滾動位置。 從您的[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函數呼叫。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步處理記錄視圖中滑杆控制項的捲動方塊位置，以及記錄集的 `int` 欄位資料成員。 |
|[DDX_FieldText](#ddx_fieldtext)|多載的版本可供傳輸`int`， **UINT**， **long**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float** **雙**，**簡短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，以及[COleCurrency](../../mfc/reference/colecurrency-class.md)之間的資料錄集欄位資料成員和編輯資料方塊`CRecordView`或`CDaoRecordView`。|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

`DDX_FieldCBIndex` 函式會同步處理記錄視圖中下拉式方塊控制項的清單方塊控制項中所選取專案的索引，以及與記錄視圖相關聯之記錄集的 `int` 欄位資料成員。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*index*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會根據 [*索引*] 中指定的值來設定控制項中的選取專案。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，MFC 會將索引的值設定為0。 在從控制項到記錄集的傳輸上，如果控制項是空的或未選取任何專案，則 [記錄集] 欄位會設定為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 此範例類似于 `DDX_FieldCBIndex`。

### <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

函式會管理`DDX_FieldCBString`記錄視圖中下拉式方塊控制項的編輯控制項與記錄視圖相關聯之記錄集的欄位資料成員之間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸。`CString`

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將下拉式方塊中的目前選取範圍設定為以 [*值*] 中指定之字串中的字元開頭的第一個資料列。 在從記錄集到控制項的傳輸上，如果 [記錄集] 欄位是 Null，則會從下拉式方塊中移除任何選取專案，並將下拉式方塊的編輯控制項設為空白。 在從控制項到記錄集的傳輸上，如果控制項是空的，當欄位允許時，[記錄集] 欄位會設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 此範例包含對 `DDX_FieldCBString`的呼叫。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

函式會管理`DDX_FieldCBStringExact`記錄視圖中下拉式方塊控制項的編輯控制項與記錄視圖相關聯之記錄集的欄位資料成員之間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸。`CString`

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將下拉式方塊中目前的選取範圍設定為與 [*值*] 中指定的字串完全相符的第一個資料列。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，則會從下拉式方塊中移除任何選取專案，並將下拉式方塊的編輯方塊設為空白。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位會設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldCBStringExact` 的呼叫會很類似。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

`DDX_FieldCheck` 函式會管理對話方塊、表單檢視或控制項視圖物件中核取方塊控制項與對話方塊、表單檢視或控制項視圖物件之**int**資料成員之間的**int**資料傳輸。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性相關聯之核取方塊控制項的資源識別碼。

*值*<br/>
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

當呼叫 `DDX_FieldCheck` 時，[*值*] 會設定為核取方塊控制項的目前狀態，或者控制項的 [狀態] 會設定為 [*值*]，視傳送的方向而定。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

`DDX_FieldLBIndex` 函式會同步處理記錄視圖中清單方塊控制項中所選取專案的索引，以及與記錄視圖相關聯之記錄集的**int**欄位資料成員。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*index*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會根據 [*索引*] 中指定的值來設定控制項中的選取專案。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，MFC 會將索引的值設定為0。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位會設定為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldlbstring"></a>DDX_FieldLBString

會將記錄視圖中清單方塊控制項目前的選取範圍複製到與記錄視圖相關聯之記錄集的 `DDX_FieldLBString`CString[欄位資料](../../atl-mfc-shared/reference/cstringt-class.md)成員。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

在反向方向中，此函式會將清單方塊中目前的選取範圍設定為開頭為*值*所指定之字串中之字元的第一個資料列。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，則會從清單方塊中移除任何選取專案。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位會設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldLBString` 的呼叫會很類似。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

函式會將記錄視圖中清單方塊控制項的目前選取範圍複製到與記錄視圖相關聯之記錄集的 `DDX_FieldLBStringExact`CString[ 欄位資料成員。](../../atl-mfc-shared/reference/cstringt-class.md)

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

在反向方向中，此函式會將清單方塊中目前的選取範圍設定為與 [*值*] 中指定的字串完全相符的第一個資料列。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，則會從清單方塊中移除任何選取專案。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位會設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldLBStringExact` 的呼叫會很類似。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldradio"></a>DDX_FieldRadio

`DDX_FieldRadio` 函式會將記錄視圖記錄集之以零為基底的**int**成員變數與記錄視圖中的選項按鈕群組中目前選取的選項按鈕產生關聯。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中相鄰選項按鈕控制項之群組中的第一個識別碼（具有樣式 WS_GROUP）。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

從 [記錄集] 欄位傳輸到視圖時，此函式會開啟第*n*個選項按鈕（以零為基底），並關閉其他按鈕。 在反向方向中，此函式會將 [記錄集] 欄位設定為目前（已核取）之選項按鈕的序數。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，則不會選取任何按鈕。 在從控制項到記錄集的傳輸時，如果未選取任何控制項，如果欄位允許，則 [記錄集] 欄位會設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldRadio` 的呼叫會很類似。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

`DDX_FieldScroll` 函式會同步處理記錄視圖中捲軸控制項的滾動位置，以及與記錄視圖相關聯之記錄集的**int**欄位資料成員（或您選擇將它對應到的任何整數變數）。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中相鄰選項按鈕控制項之群組中的第一個識別碼（具有樣式 WS_GROUP）。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將捲軸控制項的滾動位置設定為 [*值*] 中指定的值。 在從記錄集到控制項的傳輸上，如果 [記錄集] 欄位是 Null，則捲軸控制項會設定為0。 在從控制項到記錄集的傳輸上，如果控制項是空的，則記錄集欄位的值為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您要使用以 DAO 為基礎的類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldScroll` 的呼叫會很類似。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

  ## <a name="ddx_fieldslider"></a>DDX_FieldSlider
`DDX_FieldSlider` 函式會同步處理記錄視圖中滑杆控制項的捲動方塊位置，以及與記錄視圖相關聯之記錄集的**int**欄位資料成員（或您選擇要將其對應至的任何整數變數）。

### <a name="syntax"></a>語法

  ```
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
[CDataExchange](cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
滑杆控制項的資源識別碼。

*值*<br/>
要交換之值的參考。 這個參數會保留或用來設定滑杆控制項的目前捲軸位置。

*pRecordset*<br/>
與交換資料之相關聯 `CRecordset` 或 `CDaoRecordset` 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至滑杆時，此函式會將滑杆的位置設定為 [*值*] 中指定的值。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，滑杆控制項的位置會設定為0。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位的值為0。

`DDX_FieldSlider` 不會使用滑杆控制項來交換範圍資訊，其可設定範圍，而不只是位置。

如果您使用的是以 ODBC 為基礎的類別，請使用函式的第一個覆寫。 使用第二個覆寫搭配以 DAO 為基礎的類別。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。 如需 `CRecordView` 和 `CDaoRecordView` 欄位之 DDX 的範例和詳細資訊，請參閱[記錄 Views](../../data/record-views-mfc-data-access.md)。 如需滑杆控制項的相關資訊，請參閱[使用 CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱[DDX_FieldText](#ddx_fieldtext) 。 `DDX_FieldSlider` 的呼叫會很類似。

### <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="ddx_fieldtext"></a>DDX_FieldText

函式會管理在編輯方塊控制項與的欄位資料成員之間，`DDX_FieldText`int **、** short **、** long **、DWORD、** CString[、](../../atl-mfc-shared/reference/cstringt-class.md)float **、** double **、** BOOL**或** BYTE **資料的傳送。** 集中。

```
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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*值*<br/>
相關聯之 `CRecordset` 或 `CDaoRecordset` 物件中的欄位資料成員參考。 值的資料類型取決於您所使用 `DDX_FieldText` 的多載版本。

*pRecordset*<br/>
交換資料的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件指標。 這個指標可讓 `DDX_FieldText` 偵測和設定 Null 值。

### <a name="remarks"></a>備註

對於[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件，`DDX_FieldText` 也會管理傳送[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 空的編輯方塊控制項表示 Null 值。 在從記錄集到控制項的傳輸上，如果記錄集欄位是 Null，編輯方塊就會設為空白。 在從控制項到記錄集的傳輸上，如果控制項是空的，則 [記錄集] 欄位會設定為 Null。

如果您要使用以 ODBC 為基礎的類別，請使用具有[CRecordset](../../mfc/reference/crecordset-class.md)參數的版本。 如果您要使用以 DAO 為基礎的類別，請使用具有[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)參數的版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需[CRecordView](../../mfc/reference/crecordview-class.md)和[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)欄位之 DDX 的範例和詳細資訊，請參閱[記錄視圖](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>範例

`DoDataExchange`CRecordView[ 的](../../mfc/reference/crecordview-class.md)下列函式包含`DDX_FieldText`三種資料類型的函式呼叫： `IDC_COURSELIST`是下拉式方塊，其他兩個控制項是編輯方塊。 針對 DAO 程式設計， *m_pSet*參數是指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)的指標。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdao。h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)
