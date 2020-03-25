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
ms.openlocfilehash: a52d7443ab335e8546a4bcce03cf68c3b1d60e3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212007"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 類別

繼承自 `DBPROPIDSET` 結構，並加入初始化索引鍵欄位以及[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)存取方法的函式。

## <a name="syntax"></a>語法

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddPropertyID](#addpropertyid)|將屬性加入至設定的屬性識別碼。|
|[CDBPropIDSet](#cdbpropidset)|建構函式。|
|[SetGUID](#setguid)|設定屬性 ID 集的 GUID。|

### <a name="operators"></a>操作員

|||
|-|-|
|[operator =](#op_equal)|將一個屬性識別碼設定的內容指派給另一個。|

## <a name="remarks"></a>備註

OLE DB 取用者會使用 `DBPROPIDSET` 結構來傳遞屬性識別碼的陣列，供取用者想要取得屬性資訊。 單一[DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85))結構中識別的屬性屬於一個屬性集。

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a>CDBPropIDSet：： AddPropertyID

將屬性 ID 加入至屬性 ID 集。

### <a name="syntax"></a>語法

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>參數

*propid*<br/>
[in] 要加入至屬性 ID 集的屬性 ID。

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a>CDBPropIDSet：： CDBPropIDSet

建構函式。 初始化[DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85))結構的 `rgProperties`、`cProperties`和（選擇性） `guidPropertySet` 欄位。

### <a name="syntax"></a>語法

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來初始化 `guidPropertySet` 欄位的 GUID。

*propidset*<br/>
[in] 複製建構的另一個 `CDBPropIDSet` 物件。

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a>CDBPropIDSet：： SetGUID

設定 `DBPROPIDSET` 結構中的 GUID 欄位。

### <a name="syntax"></a>語法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來設定[DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85))結構之 `guidPropertySet` 欄位的 GUID。

### <a name="remarks"></a>備註

此欄位也可以由「[函數](../../data/oledb/cdbpropidset-cdbpropidset.md)」設定。 如果您為這個類別使用預設建構函式，則呼叫此函式。

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a>CDBPropIDSet：： operator =

將一個屬性 ID 集的內容指派至另一個 ID 屬性集。

### <a name="syntax"></a>語法

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
