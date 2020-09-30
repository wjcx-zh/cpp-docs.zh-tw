---
title: CDBPropIDSet 類別
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: 4de218188326dad434c5b0d355a3a15d39bb576c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502506"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 類別

繼承自 `DBPROPIDSET` 結構，並加入可初始化索引鍵欄位以及 [AddPropertyID](#addpropertyid) 存取方法的函式。

## <a name="syntax"></a>Syntax

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[AddPropertyID](#addpropertyid)|將屬性加入至屬性識別碼集。|
|[CDBPropIDSet](#cdbpropidset)|建構函式。|
|[SetGUID](#setguid)|設定屬性識別碼集的 GUID。|

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|-|-|
|[運算子 =](#op_equal)|將某個屬性 ID 的內容指派給另一個屬性識別碼。|

## <a name="remarks"></a>備註

OLE DB 取用者會使用 `DBPROPIDSET` 結構來傳遞屬性識別碼的陣列，而取用者想要取得屬性資訊。 單一 [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) 結構中所識別的屬性屬於一個屬性集。

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a> CDBPropIDSet：： AddPropertyID

將屬性 ID 加入至屬性 ID 集。

### <a name="syntax"></a>語法

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>參數

*propid*<br/>
[in] 要加入至屬性 ID 集的屬性 ID。

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a> CDBPropIDSet：： CDBPropIDSet

建構函式。 `rgProperties` `cProperties` (選擇性地) `guidPropertySet` [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85))結構的欄位，初始化、和。

### <a name="syntax"></a>語法

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來初始化欄位的 GUID `guidPropertySet` 。

*propidset*<br/>
[in] 複製建構的另一個 `CDBPropIDSet` 物件。

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a> CDBPropIDSet：： SetGUID

設定結構中的 GUID 欄位 `DBPROPIDSET` 。

### <a name="syntax"></a>語法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來設定 `guidPropertySet` [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) 結構之欄位的 GUID。

### <a name="remarks"></a>備註

這個 [欄位也可以](#cdbpropidset) 由函式設定。 如果您為這個類別使用預設建構函式，則呼叫此函式。

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a> CDBPropIDSet：： operator =

將一個屬性 ID 集的內容指派至另一個 ID 屬性集。

### <a name="syntax"></a>語法

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
