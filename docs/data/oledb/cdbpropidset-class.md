---
title: CDBPropIDSet 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9619ffdf9fd24bd73548fb3992084eb0a5d437a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114471"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 類別

繼承自`DBPROPIDSET`結構，並新增初始化索引鍵欄位的建構函式，以及[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)存取方法。  
  
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
|[AddPropertyID](#addpropertyid)|將屬性加入至屬性 ID 集。|  
|[CDBPropIDSet](#cdbpropidset)|建構函式。|  
|[SetGUID](#setguid)|設定的屬性 ID 集的 GUID。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](#op_equal)|指派的一個屬性 ID 集的內容到另一個。|  
  
## <a name="remarks"></a>備註  

OLE DB 取用者使用`DBPROPIDSET`結構，以傳遞的取用者想要取得屬性資訊的屬性識別碼的陣列。 識別在單一的屬性[DBPROPIDSET](/previous-versions/windows/desktop/ms717981\(v=vs.85\))結構屬於一個屬性集。  

## <a name="addpropertyid"></a> Cdbpropidset:: Addpropertyid

將屬性 ID 加入至屬性 ID 集。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool AddPropertyID(DBPROPID propid) throw();  
```  
  
#### <a name="parameters"></a>參數  

*propid*<br/>
[in] 要加入至屬性 ID 集的屬性 ID。  

## <a name="cdbpropidset"></a> Cdbpropidset:: Cdbpropidset

建構函式。 初始化`rgProperties`， `cProperties`，以及 （選擇性）`guidPropertySet`的欄位[DBPROPIDSET](/previous-versions/windows/desktop/ms717981\(v=vs.85\))結構。  
  
### <a name="syntax"></a>語法  
  
```cpp
CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
[in]GUID; 用來初始化`guidPropertySet`欄位。  
  
*propidset*<br/>
[in] 複製建構的另一個 `CDBPropIDSet` 物件。  

## <a name="setguid"></a> Cdbpropidset:: Setguid

設定 [GUID] 欄位中`DBPROPIDSET`結構。  
  
### <a name="syntax"></a>語法  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
[in]GUID; 用來設定`guidPropertySet`欄位[DBPROPIDSET](/previous-versions/windows/desktop/ms717981\(v=vs.85\))結構。  
  
### <a name="remarks"></a>備註  

可以設定此欄位[建構函式](../../data/oledb/cdbpropidset-cdbpropidset.md)以及。 如果您為這個類別使用預設建構函式，則呼叫此函式。  

## <a name="op_equal"></a> Cdbpropidset:: Operator =

將一個屬性 ID 集的內容指派至另一個 ID 屬性集。  
  
### <a name="syntax"></a>語法  
  
```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();  
```  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)