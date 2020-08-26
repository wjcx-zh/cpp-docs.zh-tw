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
ms.openlocfilehash: 06d0511317c21f6b132349d7d6cd6c2d6f20bc1b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837368"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的對話方塊資料交換函式

本主題列出用來在 [CRecordset](../../mfc/reference/crecordset-class.md) 和 [CRecordView](../../mfc/reference/crecordview-class.md) 表單或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 和 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 表單之間交換資料的 DDX_Field 函數。 DAO 可搭配 Access 資料庫使用，並透過 Office 2013 支援。 DAO 3.6 是最終版本，且會被視為已淘汰。

> [!NOTE]
> DDX_Field 函式就像是 DDX 函數，因為它們會與表單中的控制項交換資料。 但與 DDX 不同的是，它們會使用 view 相關聯的記錄集物件的欄位來交換資料，而不是使用記錄視圖本身的欄位來交換資料。 如需詳細資訊，請參閱類別 `CRecordView` 和 `CDaoRecordView` 。

### <a name="ddx_field-functions"></a>DDX_Field 函式

|名稱|描述|
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|在記錄集欄位資料成員與 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)中下拉式方塊中目前選取範圍的索引之間傳輸整數資料。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|`CString`在或中，于記錄集欄位資料成員與下拉式方塊的編輯控制項之間傳輸 `CRecordView` 資料 `CDaoRecordView` 。 將資料從記錄集移至控制項時，此函式會在下拉式方塊中選取以指定字串中的字元開頭的專案。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|`CString`在或中，于記錄集欄位資料成員與下拉式方塊的編輯控制項之間傳輸 `CRecordView` 資料 `CDaoRecordView` 。 將資料從記錄集移至控制項時，此函式會在下拉式方塊中選取完全符合指定字串的專案。|
|[DDX_FieldCheck](#ddx_fieldcheck)|在記錄集的欄位資料成員和或中的核取方塊之間傳輸布林資料 `CRecordView` `CDaoRecordView` 。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|在或的清單方塊中，傳輸記錄集欄位資料成員與目前選取範圍索引之間的整數資料 `CRecordView` `CDaoRecordView` 。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理清單方塊控制項與記錄集的欄位資料成員之間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸。 將資料從記錄集移至控制項時，此函式會在清單方塊中選取以指定字串中的字元開頭的專案。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理 `CString` 清單方塊控制項與記錄集的欄位資料成員之間的資料傳輸。 將資料從記錄集移至控制項時，此函式會選取與指定字串完全相符的第一個專案。|
|[DDX_FieldRadio](#ddx_fieldradio)|在或中，傳輸記錄集欄位資料成員與一組選項按鈕之間的整數資料 `CRecordView` `CDaoRecordView` 。|
|[DDX_FieldScroll](#ddx_fieldscroll)|設定或取得捲軸控制項在或中的滾動位置 `CRecordView` `CDaoRecordView` 。 從您的 [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) 函數呼叫。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步處理記錄視圖中滑杆控制項的捲動方塊位置，以及 **`int`** 記錄集的欄位資料成員。 |
|[DDX_FieldText](#ddx_fieldtext)|在記錄集的欄位資料成員和或的編輯方塊之間，可以使用多載的版本來傳送 **`int`** 、 **UINT**、 **`long`** 、 `DWORD` [CString](../../atl-mfc-shared/reference/cstringt-class.md)、 **`float`** 、 **`double`** 、 **`short`** 、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和 [COleCurrency](../../mfc/reference/colecurrency-class.md) 資料 `CRecordView` `CDaoRecordView` 。|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a> DDX_FieldCBIndex

函式會 `DDX_FieldCBIndex` 同步處理記錄視圖中下拉式方塊控制項之清單方塊控制項中所選取專案的索引，以及 **`int`** 與記錄視圖相關聯之記錄集的欄位資料成員。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*index*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會根據 [ *索引*] 中指定的值，設定控制項中的選取專案。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，MFC 會將索引的值設定為0。 在 [從控制項到記錄集的傳送] 上，如果控制項是空的或沒有選取任何專案，則 [記錄集] 欄位會設定為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 此範例類似于 `DDX_FieldCBIndex` 。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a> DDX_FieldCBString

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將下拉式方塊中目前的選取範圍設定為開頭為 [ *值*] 中指定之字串字元的第一個資料列。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則會從下拉式方塊中移除任何選取專案，並將下拉式方塊的編輯控制項設為空白。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則當欄位允許時，[記錄集] 欄位會設為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 此範例包含的呼叫 `DDX_FieldCBString` 。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a> DDX_FieldCBStringExact

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將下拉式方塊中目前的選取範圍設定為與 [ *值*] 中指定之字串完全相符的第一個資料列。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則會從下拉式方塊中移除任何選取專案，並將下拉式方塊的編輯方塊設為空白。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則會將 [記錄集] 欄位設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldCBStringExact` 很類似。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a> DDX_FieldCheck

此函式會 `DDX_FieldCheck` 管理 **`int`** 對話方塊中核取方塊控制項、表單檢視或控制項視圖物件的資料傳輸 **`int`** ，以及對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性相關聯之核取方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

當 `DDX_FieldCheck` 呼叫時，[ *值* ] 會設定為核取方塊控制項的目前狀態，或控制項的 [狀態] 會設定為 [ *值*]，視傳送方向而定。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a> DDX_FieldLBIndex

函式會 `DDX_FieldLBIndex` 同步處理記錄視圖中清單方塊控制項中所選取專案的索引，以及 **`int`** 與記錄視圖相關聯之記錄集的欄位資料成員。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*index*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會根據 [ *索引*] 中指定的值，設定控制項中的選取專案。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，MFC 會將索引的值設定為0。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則會將 [記錄集] 欄位設定為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a> DDX_FieldLBString

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

在反向方向中，此函式會將清單方塊中目前的選取範圍設定為開頭為 [ *值*] 所指定之字串字元的第一個資料列。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則會從清單方塊中移除任何選取專案。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則會將 [記錄集] 欄位設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldLBString` 很類似。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a> DDX_FieldLBStringExact

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

在反向方向中，此函式會將清單方塊中目前的選取範圍設定為與 [ *值*] 中指定之字串完全相符的第一個資料列。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則會從清單方塊中移除任何選取專案。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則會將 [記錄集] 欄位設定為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldLBStringExact` 很類似。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a> DDX_FieldRadio

函數會將 `DDX_FieldRadio` 記錄視圖記錄集之以零為基底的 **`int`** 成員變數與 [記錄] 視圖的選項按鈕群組中目前選取的選項按鈕產生關聯。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
群組中第一個的識別碼 (具有 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 物件中相鄰選項按鈕控制項的樣式 WS_GROUP) 。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

從記錄集欄位傳送到視圖時，此函式會開啟第 *n* 個選項按鈕 (以零為基礎的) 並關閉其他按鈕。 在反向方向中，此函式會將記錄集欄位設定為目前在 (檢查) 之選項按鈕的序號。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則不會選取任何按鈕。 在「從控制項到記錄集的傳送」上，如果未選取任何控制項，則如果欄位允許，則 [記錄集] 欄位會設為 Null。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldRadio` 很類似。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a> DDX_FieldScroll

此函式會 `DDX_FieldScroll` 同步處理記錄視圖中捲軸控制項的滾動位置，以及 **`int`** 與記錄視圖相關聯之記錄集的欄位資料成員 (或您選擇將其對應至) 的任何整數變數。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
群組中第一個的識別碼 (具有 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 物件中相鄰選項按鈕控制項的樣式 WS_GROUP) 。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。

### <a name="remarks"></a>備註

將資料從記錄集移至控制項時，此函式會將捲軸控制項的滾動位置設定為 [ *值*] 中指定的值。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則捲軸控制項設定為0。 在 [從控制項到記錄集的傳送] 上，如果控制項是空的，則 [記錄集] 欄位的值為0。

如果您使用的是以 ODBC 為基礎的類別，請使用第一個版本。 如果您使用的是 DAO 型類別，請使用第二個版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldScroll` 很類似。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a> DDX_FieldSlider

函式 `DDX_FieldSlider` 會同步處理記錄視圖中滑杆控制項的捲動方塊位置，以及 **`int`** 與記錄視圖相關聯之記錄集的欄位資料成員 (或您選擇將其對應至) 的任何整數變數。

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
[CDataExchange](cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
滑杆控制項的資源識別碼。

*value*<br/>
要交換之值的參考。 此參數會保留或將用來設定滑杆控制項的目前 thumb 位置。

*pRecordset*<br/>
用來交換資料之相關聯 `CRecordset` 或物件的指標 `CDaoRecordset` 。

### <a name="remarks"></a>備註

將資料從記錄集移至滑杆時，此函式會將滑杆的位置設定為 [ *值*] 中指定的值。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，滑杆控制項的位置會設定為0。 在從控制項到記錄集的傳輸上，如果控制項是空的，則記錄集欄位的值為0。

`DDX_FieldSlider` 不會交換範圍資訊與滑杆控制項是否能設定範圍，而不只是位置。

如果您要使用以 ODBC 為基礎的類別，請使用函式的第一個覆寫。 使用第二個覆寫搭配 DAO 型類別。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。 如需和欄位之 DDX 的範例和詳細資訊 `CRecordView` `CDaoRecordView` ，請參閱 [記錄視圖](../../data/record-views-mfc-data-access.md)。 如需滑杆控制項的詳細資訊，請參閱 [使用 CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>範例

如需一般 DDX_Field 範例，請參閱 [DDX_FieldText](#ddx_fieldtext) 。 的呼叫會 `DDX_FieldSlider` 很類似。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a> DDX_FieldText

`DDX_FieldText`函數會管理 **`int`** **`short`** **`long`** [CString](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** 編輯方塊控制項與記錄集的欄位資料成員之間的**BOOL**、、、DWORD、CString、、、BOOL 或**位元組**資料的傳輸。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件中的控制項識別碼。

*value*<br/>
關聯或物件中的欄位資料成員參考 `CRecordset` `CDaoRecordset` 。 值的資料類型取決於您所使用的多載版本 `DDX_FieldText` 。

*pRecordset*<br/>
用來交換資料之 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件的指標。 此指標可偵測 `DDX_FieldText` 並設定 Null 值。

### <a name="remarks"></a>備註

針對 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件， `DDX_FieldText` 也會管理傳輸 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和 [COleCurrency](../../mfc/reference/colecurrency-class.md) 值。 空白的編輯方塊控制項會指出 Null 值。 從記錄集傳送到控制項時，如果記錄集欄位為 Null，則編輯方塊會設定為空白。 在「從控制項到記錄集的傳送」上，如果控制項是空的，則會將 [記錄集] 欄位設定為 Null。

如果您使用以 ODBC 為基礎的類別，請使用具有 [CRecordset](../../mfc/reference/crecordset-class.md) 參數的版本。 如果您使用的是 DAO 型類別，請使用具有 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 參數的版本。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 欄位之 DDX 的範例和詳細資訊，請參閱文章 [記錄視圖](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>範例

[CRecordView](../../mfc/reference/crecordview-class.md) 的`DoDataExchange`下列函式包含`DDX_FieldText`三種資料類型的函式呼叫： `IDC_COURSELIST`是下拉式方塊，其他兩個控制項是編輯方塊。 針對 DAO 程式設計， *m_pSet* 參數是指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)的指標。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)
