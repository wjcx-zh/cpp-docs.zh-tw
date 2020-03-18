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
ms.openlocfilehash: 08cab967fbfbd4b3207e96a4fdbd2d2dbc6da793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447449"
---
# <a name="cdbpropset-class"></a>CDBPropSet 類別

繼承自 `DBPROPSET` 結構，並加入初始化索引鍵欄位及 `AddProperty` 存取方法的函式。

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
|[SetGUID](#setguid)|設定 `DBPROPSET` 結構的 `guidPropertySet` 欄位。|

### <a name="operators"></a>操作員

|||
|-|-|
|[operator =](#op_equal)|將一個屬性集的內容指派給另一個。|

## <a name="remarks"></a>備註

OLE DB 提供者和取用者會使用 `DBPROPSET` 結構來傳遞 `DBPROP` 結構的陣列。 每個 `DBPROP` 結構都代表可設定的單一屬性。

## <a name="addproperty"></a>CDBPropSet：： AddProperty

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
在要加入之屬性的識別碼。 用來初始化已加入至屬性集之 `DBPROP` 結構的 `dwPropertyID`。

*var*<br/>
在用來初始化已加入屬性集之 `DBPROP` 結構之屬性值的變數。

*szValue*<br/>
在用來初始化已加入屬性集之 `DBPROP` 結構之屬性值的字串。

*其中 bvalue system.boolean.true*<br/>
在`BYTE` 或布林值，用來初始化加入至屬性集之 `DBPROP` 結構的屬性值。

*N 值*<br/>
在整數值，用來初始化加入至屬性集之 `DBPROP` 結構的屬性值。

*fltValue*<br/>
在浮點值，用來初始化加入至屬性集之 `DBPROP` 結構的屬性值。

*dblValue*<br/>
在雙精確度浮點數，用來初始化加入至屬性集之 `DBPROP` 結構的屬性值。

*cyValue*<br/>
在CY 貨幣值，用來初始化加入至屬性集之 `DBPROP` 結構的屬性值。

### <a name="return-value"></a>傳回值

如果成功加入屬性，**則為 true** 。 否則為 **false**。

## <a name="cdbpropset"></a>CDBPropSet：： CDBPropSet

建構函式。 初始化[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構的 `rgProperties`、`cProperties`和 `guidPropertySet` 欄位。

### <a name="syntax"></a>語法

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來初始化 `guidPropertySet` 欄位的 GUID。

*propset*<br/>
[in] 複製建構的另一個 `CDBPropSet` 物件。

## <a name="setguid"></a>CDBPropSet：： SetGUID

設定 `DBPROPSET` 結構中的 `guidPropertySet` 欄位。

### <a name="syntax"></a>語法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
在用來設定[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構之 `guidPropertySet` 欄位的 GUID。

### <a name="remarks"></a>備註

此欄位也可以由「[函數](../../data/oledb/cdbpropset-cdbpropset.md)」設定。

## <a name="op_equal"></a>CDBPropSet：： operator =

將一個屬性集的內容指派給另一個屬性集。

### <a name="syntax"></a>語法

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 結構](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP 結構](/previous-versions/windows/desktop/ms717970(v=vs.85))