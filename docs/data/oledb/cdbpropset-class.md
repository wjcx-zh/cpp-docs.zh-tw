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
- SetGUID
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
ms.openlocfilehash: b58c0262d361ede37bc3db68784177ec4c29f3a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034230"
---
# <a name="cdbpropset-class"></a>CDBPropSet 類別

繼承自`DBPROPSET`結構，並新增初始化索引鍵欄位的建構函式以及`AddProperty`存取方法。

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
|[SetGUID](#setguid)|設定組`guidPropertySet`欄位`DBPROPSET`結構。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子 =](#op_equal)|指派設定到另一個屬性的內容。|

## <a name="remarks"></a>備註

OLE DB 提供者和取用者使用`DBPROPSET`結構，以傳遞的陣列`DBPROP`結構。 每個`DBPROP`結構代表可設定的單一屬性。

## <a name="addproperty"></a> CDBPropSet::AddProperty

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
[in]要加入之屬性識別碼。 用來初始化`dwPropertyID`的`DBPROP`結構加入至屬性集。

*var*<br/>
[in]用來初始化的屬性值的 variant`DBPROP`結構加入至屬性集。

*szValue*<br/>
[in]用來初始化的屬性值的字串`DBPROP`結構加入至屬性集。

*bValue*<br/>
[in]A`BYTE`或 布林值，用來初始化的屬性值`DBPROP`結構加入至屬性集。

*nValue*<br/>
[in]用來初始化的屬性值的整數值`DBPROP`結構加入至屬性集。

*fltValue*<br/>
[in]用來初始化的屬性值的浮點值`DBPROP`結構加入至屬性集。

*dblValue*<br/>
[in]用來初始化的屬性值的雙精確度浮點值`DBPROP`結構加入至屬性集。

*cyValue*<br/>
[in]CY 貨幣值，用來初始化的屬性值`DBPROP`結構加入至屬性集。

### <a name="return-value"></a>傳回值

**true**如果已成功加入屬性。 否則，請**false**。

## <a name="cdbpropset"></a> CDBPropSet::CDBPropSet

建構函式。 初始化`rgProperties`， `cProperties`，並`guidPropertySet`的欄位[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構。

### <a name="syntax"></a>語法

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>參數

*guid*<br/>
[in]GUID; 用來初始化`guidPropertySet`欄位。

*propset*<br/>
[in] 複製建構的另一個 `CDBPropSet` 物件。

## <a name="setguid"></a> CDBPropSet::SetGUID

設定組`guidPropertySet`欄位中`DBPROPSET`結構。

### <a name="syntax"></a>語法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
[in]GUID; 用來設定`guidPropertySet`欄位[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構。

### <a name="remarks"></a>備註

可以設定此欄位[建構函式](../../data/oledb/cdbpropset-cdbpropset.md)以及。

## <a name="op_equal"></a> CDBPropSet::operator =

將一個屬性集的內容指派給另一個屬性集。

### <a name="syntax"></a>語法

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 結構](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP 結構](/previous-versions/windows/desktop/ms717970(v=vs.85))