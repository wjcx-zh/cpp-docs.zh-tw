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
ms.openlocfilehash: 41ea20bcddc53142773d474af41021e9c71af1aa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289854"
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
|[CDBVariant::CDBVariant](#cdbvariant)|建構 `CDBVariant` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|清除`CDBVariant`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|包含目前儲存的值的資料類型。 輸入 `DWORD`。|

### <a name="public-union-members"></a>公用的等位成員

|名稱|描述|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|包含類型的值**BOOL**。|
|[CDBVariant::m_chVal](#m_chval)|包含類型的值**unsigned char**。|
|[CDBVariant::m_dblVal](#m_dblval)|包含類型的值**double**。|
|[CDBVariant::m_fltVal](#m_fltval)|包含類型的值**浮點數**。|
|[CDBVariant::m_iVal](#m_ival)|包含類型的值**簡短**。|
|[CDBVariant::m_lVal](#m_lval)|包含類型的值**長**。|
|[CDBVariant::m_pbinary](#m_pbinary)|包含型別的物件的指標`CLongBinary`。|
|[CDBVariant::m_pdate](#m_pdate)|包含型別的物件的指標**TIMESTAMP_STRUCT**。|
|[CDBVariant::m_pstring](#m_pstring)|包含型別的物件的指標`CString`。|
|[CDBVariant::m_pstringA](#m_pstringa)|儲存的指標 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。|
|[CDBVariant::m_pstringW](#m_pstringw)|會儲存成寬指標[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。|

## <a name="remarks"></a>備註

`CDBVariant` 沒有基底類別。

`CDBVariant` 類似於[COleVariant](../../mfc/reference/colevariant-class.md); 不過，`CDBVariant`不會使用 OLE。 `CDBVariant` 可讓您儲存的值，而不需擔心值的資料類型。 `CDBVariant` 會追蹤目前的值等位中儲存的資料類型。

類別[CRecordset](../../mfc/reference/crecordset-class.md)利用`CDBVariant`三個成員函式中的物件： `GetFieldValue`， `GetBookmark`，和`SetBookmark`。 比方說，`GetFieldValue`可讓您以動態方式擷取資料行中的資料。 因為在執行階段，可能不知道資料行的資料型別`GetFieldValue`使用`CDBVariant`物件來儲存資料行的資料。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDBVariant`

## <a name="requirements"></a>需求

**標頭：** afxdb.h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

建立 NULL`CDBVariant`物件。

```
CDBVariant();
```

### <a name="remarks"></a>備註

設定組[m_dwType](#m_dwtype) DBVT_NULL 資料成員。

##  <a name="clear"></a>  CDBVariant::Clear

呼叫此成員函式，以清除`CDBVariant`物件。

```
void Clear();
```

### <a name="remarks"></a>備註

如果值[m_dwType](#m_dwtype)資料成員是 DBVT_DATE、 DBVT_STRING 或 DBVT_BINARY，`Clear`釋放與等位的指標成員相關聯的記憶體。 `Clear` 設定`m_dwType`DBVT_NULL 到。

`CDBVariant`解構函式呼叫`Clear`。

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

儲存型別 BOOL 的值。

### <a name="remarks"></a>備註

`m_boolVal`資料成員所屬的等位。 才能存取`m_boolVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_BOOL，則`m_boolVal`會包含有效的值; 否則存取`m_boolVal`會產生不可靠的結果。

##  <a name="m_chval"></a>  CDBVariant::m_chVal

儲存值的型別**unsigned char**。

### <a name="remarks"></a>備註

`m_chVal`資料成員所屬的等位。 才能存取`m_chVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_UCHAR，則`m_chVal`包含有效的值; 否則存取`m_chVal`會產生不可靠的結果。

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

儲存值的型別**double**。

### <a name="remarks"></a>備註

`m_dblVal`資料成員所屬的等位。 才能存取`m_dblVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_DOUBLE，則`m_dblVal`包含有效的值; 否則存取`m_dblVal`會產生不可靠的結果。

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

此資料成員包含資料類型的值，目前儲存在`CDBVariant`物件的等位資料成員。

### <a name="remarks"></a>備註

才能存取這個聯集，您必須檢查的值`m_dwType`以判斷哪一個等位資料成員，來存取。 下表列出可能的值為`m_dwType`和對應的等位資料成員。

|m_dwType|等位資料成員|
|---------------|-----------------------|
|DBVT_NULL|任何等位的成員不僅適用於存取項目。|
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

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

儲存值的型別**浮點數**。

### <a name="remarks"></a>備註

`m_fltVal`資料成員所屬的等位。 才能存取`m_fltVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_SINGLE，則`m_fltVal`包含有效的值; 否則存取`m_fltVal`會產生不可靠的結果。

##  <a name="m_ival"></a>  CDBVariant::m_iVal

儲存值的型別**簡短**。

### <a name="remarks"></a>備註

`m_iVal`資料成員所屬的等位。 才能存取`m_iVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_SHORT，則`m_iVal`包含有效的值; 否則存取`m_iVal`會產生不可靠的結果。

##  <a name="m_lval"></a>  CDBVariant::m_lVal

儲存值的型別**長**。

### <a name="remarks"></a>備註

`m_lVal`資料成員所屬的等位。 才能存取`m_lVal`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_LONG，則`m_lVal`包含有效的值; 否則存取`m_lVal`會產生不可靠的結果。

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

儲存類型的物件的指標[CLongBinary](../../mfc/reference/clongbinary-class.md)。

### <a name="remarks"></a>備註

`m_pbinary`資料成員所屬的等位。 才能存取`m_pbinary`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_BINARY，則`m_pbinary`包含有效的指標; 否則存取`m_pbinary`會產生不可靠的結果。

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

儲存物件的型別 TIMESTAMP_STRUCT 的指標。

### <a name="remarks"></a>備註

`m_pdate`資料成員所屬的等位。 才能存取`m_pdate`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_DATE，則`m_pdate`包含有效的指標; 否則存取`m_pdate`會產生不可靠的結果。

如需 TIMESTAMP_STRUCT 資料類型的詳細資訊，請參閱主題[C 資料類型](/previous-versions/windows/desktop/ms714556)的附錄 D 中*ODBC 程式設計人員參考*Windows SDK 中。

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

儲存類型的物件的指標[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

`m_pstring`資料成員所屬的等位。 才能存取`m_pstring`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_STRING，則`m_pstring`包含有效的指標; 否則存取`m_pstring`會產生不可靠的結果。

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

儲存的指標 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

`m_pstringA`資料成員所屬的等位。 才能存取`m_pstringA`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_ASTRING，則`m_pstringA`包含有效的指標; 否則存取`m_pstringA`會產生不可靠的結果。

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

會儲存成寬指標[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

`m_pstringW`資料成員所屬的等位。 才能存取`m_pstringW`，先檢查的值[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為 DBVT_WSTRING，則`m_pstringW`包含有效的指標; 否則存取`m_pstringW`會產生不可靠的結果。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
