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
ms.openlocfilehash: 45a478a5ca6cfb4d9b976a29eae2ae7d98fdd6ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223079"
---
# <a name="cdbvariant-class"></a>CDBVariant 類別

表示 MFC ODBC 類別的 Variant 資料類型。

## <a name="syntax"></a>語法

```
class CDBVariant
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[CDBVariant：： CDBVariant](#cdbvariant)|建構 `CDBVariant` 物件。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[CDBVariant：： Clear](#clear)|清除 `CDBVariant` 物件。|

### <a name="public-data-members"></a>公用資料成員

|Name|說明|
|----------|-----------------|
|[CDBVariant：： m_dwType](#m_dwtype)|包含目前儲存值的資料類型。 輸入 `DWORD`。|

### <a name="public-union-members"></a>公用聯集成員

|Name|說明|
|----------|-----------------|
|[CDBVariant：： m_boolVal](#m_boolval)|包含**BOOL**類型的值。|
|[CDBVariant：： m_chVal](#m_chval)|包含類型的值 **`unsigned char`** 。|
|[CDBVariant：： m_dblVal](#m_dblval)|包含類型的值 **`double`** 。|
|[CDBVariant：： m_fltVal](#m_fltval)|包含類型的值 **`float`** 。|
|[CDBVariant：： m_iVal](#m_ival)|包含類型的值 **`short`** 。|
|[CDBVariant：： m_lVal](#m_lval)|包含類型的值 **`long`** 。|
|[CDBVariant：： m_pbinary](#m_pbinary)|包含類型物件的指標 `CLongBinary` 。|
|[CDBVariant：： m_pdate](#m_pdate)|包含**TIMESTAMP_STRUCT**類型之物件的指標。|
|[CDBVariant：： m_pstring](#m_pstring)|包含類型物件的指標 `CString` 。|
|[CDBVariant：： m_pstringA](#m_pstringa)|儲存 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。|
|[CDBVariant：： m_pstringW](#m_pstringw)|儲存寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。|

## <a name="remarks"></a>備註

`CDBVariant`沒有基類。

`CDBVariant`類似于[COleVariant](../../mfc/reference/colevariant-class.md);不過，不 `CDBVariant` 會使用 OLE。 `CDBVariant`可讓您儲存值，而不需擔心值的資料類型。 `CDBVariant`追蹤目前值的資料類型，儲存在聯集內。

類別[CRecordset](../../mfc/reference/crecordset-class.md)會利用 `CDBVariant` 三個成員函式中的物件： `GetFieldValue` 、 `GetBookmark` 和 `SetBookmark` 。 例如，可 `GetFieldValue` 讓您以動態方式提取資料行中的資料。 因為在執行時間可能不知道資料行的資料類型，所以會 `GetFieldValue` 使用 `CDBVariant` 物件來儲存資料行的資料。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDBVariant`

## <a name="requirements"></a>需求

**標頭：** afxdb。h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant：： CDBVariant

建立 Null `CDBVariant` 物件。

```
CDBVariant();
```

### <a name="remarks"></a>備註

將[m_dwType](#m_dwtype)的資料成員設定為 DBVT_Null。

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant：： Clear

呼叫這個成員函式以清除 `CDBVariant` 物件。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

如果[m_dwType](#m_dwtype)資料成員的值是 DBVT_DATE、DBVT_STRING 或 DBVT_BINARY，就會 `Clear` 釋出與聯集指標成員關聯的記憶體。 `Clear`將設定 `m_dwType` 為 DBVT_Null。

此 `CDBVariant` 析構函式會呼叫 `Clear` 。

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant：： m_boolVal

儲存 BOOL 類型的值。

### <a name="remarks"></a>備註

`m_boolVal`資料成員屬於聯集。 存取之前 `m_boolVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_BOOL，則 `m_boolVal` 會包含有效的值，否則存取 `m_boolVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant：： m_chVal

儲存類型的值 **`unsigned char`** 。

### <a name="remarks"></a>備註

`m_chVal`資料成員屬於聯集。 存取之前 `m_chVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_UCHAR，則會 `m_chVal` 包含有效的值; 否則，存取 `m_chVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant：： m_dblVal

儲存類型的值 **`double`** 。

### <a name="remarks"></a>備註

`m_dblVal`資料成員屬於聯集。 存取之前 `m_dblVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_DOUBLE，則會 `m_dblVal` 包含有效的值; 否則，存取 `m_dblVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant：： m_dwType

此資料成員包含目前儲存于 `CDBVariant` 物件聯集資料成員中之值的資料類型。

### <a name="remarks"></a>備註

存取此等位之前，您必須檢查的值， `m_dwType` 以判斷要存取的聯集資料成員。 下表列出 `m_dwType` 和對應聯集資料成員的可能值。

|m_dwType|聯集資料成員|
|---------------|-----------------------|
|DBVT_Null|無聯集成員對存取有效。|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant：： m_fltVal

儲存類型的值 **`float`** 。

### <a name="remarks"></a>備註

`m_fltVal`資料成員屬於聯集。 存取之前 `m_fltVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_SINGLE，則會 `m_fltVal` 包含有效的值; 否則，存取 `m_fltVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant：： m_iVal

儲存類型的值 **`short`** 。

### <a name="remarks"></a>備註

`m_iVal`資料成員屬於聯集。 存取之前 `m_iVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_SHORT，則會 `m_iVal` 包含有效的值; 否則，存取 `m_iVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant：： m_lVal

儲存類型的值 **`long`** 。

### <a name="remarks"></a>備註

`m_lVal`資料成員屬於聯集。 存取之前 `m_lVal` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_LONG，則會 `m_lVal` 包含有效的值; 否則，存取 `m_lVal` 將會產生不可靠的結果。

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant：： m_pbinary

儲存[CLongBinary](../../mfc/reference/clongbinary-class.md)類型之物件的指標。

### <a name="remarks"></a>備註

`m_pbinary`資料成員屬於聯集。 存取之前 `m_pbinary` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_BINARY，則會 `m_pbinary` 包含有效的指標; 否則，存取 `m_pbinary` 將會產生不可靠的結果。

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant：： m_pdate

儲存類型物件的指標 TIMESTAMP_STRUCT。

### <a name="remarks"></a>備註

`m_pdate`資料成員屬於聯集。 存取之前 `m_pdate` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_DATE，則會 `m_pdate` 包含有效的指標; 否則，存取 `m_pdate` 將會產生不可靠的結果。

如需有關 TIMESTAMP_STRUCT 資料類型的詳細資訊，請參閱 Windows SDK 中 ODBC 程式設計*人員參考*的[C # 資料類型](/sql/odbc/reference/appendixes/c-data-types)主題。

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant：： m_pstring

儲存類型為[CString](../../atl-mfc-shared/reference/cstringt-class.md)之物件的指標。

### <a name="remarks"></a>備註

`m_pstring`資料成員屬於聯集。 存取之前 `m_pstring` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_STRING，則會 `m_pstring` 包含有效的指標; 否則，存取 `m_pstring` 將會產生不可靠的結果。

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant：： m_pstringA

儲存 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。

### <a name="remarks"></a>備註

`m_pstringA`資料成員屬於聯集。 存取之前 `m_pstringA` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_ASTRING，則會 `m_pstringA` 包含有效的指標; 否則，存取 `m_pstringA` 將會產生不可靠的結果。

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant：： m_pstringW

儲存寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的指標。

### <a name="remarks"></a>備註

`m_pstringW`資料成員屬於聯集。 存取之前 `m_pstringW` ，請先檢查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 設定為 DBVT_WSTRING，則會 `m_pstringW` 包含有效的指標; 否則，存取 `m_pstringW` 將會產生不可靠的結果。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
