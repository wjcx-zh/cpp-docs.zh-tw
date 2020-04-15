---
title: CDBVariant 類別
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 3c13c1a965014af271ce2911505742d9a50eedd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376457"
---
# <a name="cdbvariant-class"></a>CDBVariant 類別

表示 MFC ODBC 類別的 Variant 資料類型。

## <a name="syntax"></a>語法

```
class CDBVariant
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDB 變數::CDB 變數](#cdbvariant)|建構 `CDBVariant` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDB 變數:清除](#clear)|清除`CDBVariant`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDB 變數::m_dwType](#m_dwtype)|包含當前存儲值的數據類型。 輸入 `DWORD`。|

### <a name="public-union-members"></a>公共工會成員

|名稱|描述|
|----------|-----------------|
|[國開行::m_boolVal](#m_boolval)|包含**BOOL**類型的值。|
|[CDB 變數::m_chVal](#m_chval)|包含類型**無符號字元**的值。|
|[CDB 變數::m_dblVal](#m_dblval)|包含**雙精度**類型的值。|
|[CDB 變數::m_fltVal](#m_fltval)|包含類型**浮點**的值。|
|[CDB 變數::m_iVal](#m_ival)|包含**短類型**的值。|
|[CDB變數::m_lVal](#m_lval)|包含**長**類型的值。|
|[CDB 變數:m_pbinary](#m_pbinary)|包含指向類型`CLongBinary`物件的指標。|
|[國開行::m_pdate](#m_pdate)|包含指向型**態 TIMESTAMP_STRUCT物件的指標**。|
|[國開行::m_pstring](#m_pstring)|包含指向類型`CString`物件的指標。|
|[CDB 變數::m_pstringA](#m_pstringa)|存儲指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。|
|[CDB 變數::m_pstringW](#m_pstringw)|存儲指向寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。|

## <a name="remarks"></a>備註

`CDBVariant`沒有基類。

`CDBVariant`類似於[COleVariant;](../../mfc/reference/colevariant-class.md)但是,`CDBVariant`不使用 OLE。 `CDBVariant`允許您存儲值,而不必擔心該值的數據類型。 `CDBVariant`跟蹤存儲在聯合中的當前值的數據類型。

CRecordset[類別](../../mfc/reference/crecordset-class.md)`CDBVariant`利用三個成員函數的物件`GetFieldValue``GetBookmark`:`SetBookmark`和 。 例如,`GetFieldValue`允許您動態提取列中的資料。 由於列的數據類型在運行時可能不知道,因此`GetFieldValue`使用`CDBVariant`物件來存儲列的數據。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDBVariant`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDB 變數::CDB 變數

創建 NULL`CDBVariant`物件。

```
CDBVariant();
```

### <a name="remarks"></a>備註

將[m_dwType](#m_dwtype)數據成員設置為DBVT_NULL。

## <a name="cdbvariantclear"></a><a name="clear"></a>CDB 變數:清除

調用此成員函數以清除`CDBVariant`物件。

```
void Clear();
```

### <a name="remarks"></a>備註

如果[m_dwType](#m_dwtype)數據成員的值是DBVT_DATE、DBVT_STRING或DBVT_BINARY,則`Clear`釋放與聯合指標成員關聯的記憶體。 `Clear`設置`m_dwType`到DBVT_NULL。

析`CDBVariant`構函式呼叫`Clear`。

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>國開行::m_boolVal

存儲 BOOL 類型的值。

### <a name="remarks"></a>備註

數據`m_boolVal`成員屬於聯合。 在存`m_boolVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_BOOL,`m_boolVal`則將包含一個有效的值;如果設置為"DBVT_BOOL",則將包含一個有效值。否則,訪問`m_boolVal`將產生不可靠的結果。

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDB 變數::m_chVal

儲存類型**無符號字元**的值。

### <a name="remarks"></a>備註

數據`m_chVal`成員屬於聯合。 在存`m_chVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_UCHAR,則包含`m_chVal`有效的 值;如果設置為"DBVT_UCHAR",則包含一個有效值。否則,訪問`m_chVal`將產生不可靠的結果。

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDB 變數::m_dblVal

存儲類型**為雙**的值。

### <a name="remarks"></a>備註

數據`m_dblVal`成員屬於聯合。 在存`m_dblVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_DOUBLE,則包含`m_dblVal`有效的 值;如果設置為"DBVT_DOUBLE",則包含一個有效值。否則,訪問`m_dblVal`將產生不可靠的結果。

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDB 變數::m_dwType

此數據成員包含當前存儲在`CDBVariant`對象的聯合數據成員中的值的數據類型。

### <a name="remarks"></a>備註

在訪問此聯合之前,必須檢查的值`m_dwType`,以確定要訪問哪個聯合數據成員。 下表列出了`m_dwType`和 相應的聯合數據成員的可能值和相應的聯合數據成員。

|m_dwType|聯盟資料成員|
|---------------|-----------------------|
|DBVT_NULL|沒有工會成員對訪問有效。|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDB 變數::m_fltVal

存儲類型**浮點**的值。

### <a name="remarks"></a>備註

數據`m_fltVal`成員屬於聯合。 在存`m_fltVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_SINGLE,則包含`m_fltVal`有效的 值;如果設置為 DBVT_SINGLE,則包含一個有效值。否則,訪問`m_fltVal`將產生不可靠的結果。

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDB 變數::m_iVal

存儲類型**為短**的值。

### <a name="remarks"></a>備註

數據`m_iVal`成員屬於聯合。 在存`m_iVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_SHORT,則包含`m_iVal`有效的 值;如果設置為"DBVT_SHORT",則包含一個有效值。否則,訪問`m_iVal`將產生不可靠的結果。

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDB變數::m_lVal

儲存**長**類型的值。

### <a name="remarks"></a>備註

數據`m_lVal`成員屬於聯合。 在存`m_lVal`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_LONG,則包含`m_lVal`有效的 值;如果設置為 DBVT_LONG,則包含一個有效值。否則,訪問`m_lVal`將產生不可靠的結果。

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDB 變數:m_pbinary

存儲指向[CLongBinary](../../mfc/reference/clongbinary-class.md)類型的物件的指標。

### <a name="remarks"></a>備註

數據`m_pbinary`成員屬於聯合。 在存`m_pbinary`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_BINARY,`m_pbinary`則 包含有效的指標;否則,訪問`m_pbinary`將產生不可靠的結果。

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>國開行::m_pdate

存儲指向類型TIMESTAMP_STRUCT物件的指標。

### <a name="remarks"></a>備註

數據`m_pdate`成員屬於聯合。 在存`m_pdate`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_DATE,`m_pdate`則 包含有效的指標;否則,訪問`m_pdate`將產生不可靠的結果。

有關TIMESTAMP_STRUCT資料類型的詳細資訊,請參閱 Windows SDK 中*ODBC 程式設計師參考*附錄 D 中的主題[C 資料類型](/sql/odbc/reference/appendixes/c-data-types)。

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>國開行::m_pstring

存儲指向[CString](../../atl-mfc-shared/reference/cstringt-class.md)類型的物件的指標。

### <a name="remarks"></a>備註

數據`m_pstring`成員屬於聯合。 在存`m_pstring`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_STRING,`m_pstring`則 包含有效的指標;否則,訪問`m_pstring`將產生不可靠的結果。

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDB 變數::m_pstringA

存儲指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。

### <a name="remarks"></a>備註

數據`m_pstringA`成員屬於聯合。 在存`m_pstringA`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_ASTRING,`m_pstringA`則 包含有效的指標;否則,訪問`m_pstringA`將產生不可靠的結果。

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDB 變數::m_pstringW

存儲指向寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。

### <a name="remarks"></a>備註

數據`m_pstringW`成員屬於聯合。 在存`m_pstringW`取 之前,首先檢查[CDB 變數的值:::m_dwType](#m_dwtype)。 如果`m_dwType`設置為DBVT_WSTRING,`m_pstringW`則包含有效的指標;否則,訪問`m_pstringW`將產生不可靠的結果。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
