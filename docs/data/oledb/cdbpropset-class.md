---
title: CDBPropSet 類別
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 182db37a2a42ec91066b58903c873d3e9c8289f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216488"
---
# <a name="cdbpropset-class"></a>CDBPropSet 類別

繼承自 `DBPROPSET` 結構，並加入初始化索引鍵欄位以及存取方法的函式 `AddProperty` 。

## <a name="syntax"></a>語法

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddProperty](#addproperty)|將屬性加入至屬性集。|
|[CDBPropSet](#cdbpropset)|建構函式。|
|[SetGUID](#setguid)|設定 `guidPropertySet` 結構的欄位 `DBPROPSET` 。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#op_equal)|將一個屬性集的內容指派給另一個。|

## <a name="remarks"></a>備註

OLE DB 提供者和取用者會使用 `DBPROPSET` 結構來傳遞結構的陣列 `DBPROP` 。 每個 `DBPROP` 結構都代表可設定的單一屬性。

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet：： AddProperty

將屬性加入至屬性集。

### <a name="syntax"></a>語法

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>參數

*dwPropertyID*<br/>
在要加入之屬性的識別碼。 用來初始化 `dwPropertyID` `DBPROP` 已加入至屬性集之結構的。

*var*<br/>
在Variant，用來初始化 `DBPROP` 加入至屬性集之結構的屬性值。

*szValue*<br/>
在字串，用來初始化 `DBPROP` 已加入屬性集之結構的屬性值。

*其中 bvalue system.boolean.true*<br/>
在`BYTE`或布林值，用來初始化 `DBPROP` 已加入至屬性集之結構的屬性值。

*N 值*<br/>
在整數值，用來初始化 `DBPROP` 已加入至屬性集之結構的屬性值。

*fltValue*<br/>
在浮點值，用來初始化 `DBPROP` 已加入至屬性集之結構的屬性值。

*dblValue*<br/>
在雙精確度浮點數，用來初始化 `DBPROP` 已加入至屬性集之結構的屬性值。

*cyValue*<br/>
在CY 貨幣值，用來初始化 `DBPROP` 已加入屬性集之結構的屬性值。

### <a name="return-value"></a>傳回值

**`true`** 如果已成功加入屬性，則為。 否則為 **`false`** 。

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet：： CDBPropSet

建構函式。 初始化 `rgProperties` `cProperties` DBPROPSET 結構的、和 `guidPropertySet` 欄位。 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))

### <a name="syntax"></a>語法

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來初始化欄位的 GUID `guidPropertySet` 。

*propset*<br/>
[in] 複製建構的另一個 `CDBPropSet` 物件。

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet：： SetGUID

`guidPropertySet`在結構中設定欄位 `DBPROPSET` 。

### <a name="syntax"></a>語法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來設定 `guidPropertySet` [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構之欄位的 GUID。

### <a name="remarks"></a>備註

此欄位也可以由「[函數](../../data/oledb/cdbpropset-cdbpropset.md)」設定。

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet：： operator =

將一個屬性集的內容指派給另一個屬性集。

### <a name="syntax"></a>語法

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 結構](/previous-versions/windows/desktop/ms714367(v=vs.85)) 
[DBPROP 結構](/previous-versions/windows/desktop/ms717970(v=vs.85))
