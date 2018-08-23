---
title: CDBPropSet 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b94898cbe4a041ac1bb9a5d01c55380ee496106
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42575460"
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
|[operator =](#op_equal)|指派設定到另一個屬性的內容。|  
  
## <a name="remarks"></a>備註  
 OLE DB 提供者和取用者使用`DBPROPSET`結構，以傳遞的陣列`DBPROP`結構。 每個`DBPROP`結構代表可設定的單一屬性。  

## <a name="addproperty"></a> Cdbpropset:: Addproperty
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
 *dwPropertyID*  
 [in]要加入之屬性識別碼。 用來初始化`dwPropertyID`的`DBPROP`結構加入至屬性集。  
  
 *var*  
 [in]用來初始化的屬性值的 variant`DBPROP`結構加入至屬性集。  
  
 *szValue*  
 [in]用來初始化的屬性值的字串`DBPROP`結構加入至屬性集。  
  
 *bValue*  
 [in]A`BYTE`或 布林值，用來初始化的屬性值`DBPROP`結構加入至屬性集。  
  
 *n 值*  
 [in]用來初始化的屬性值的整數值`DBPROP`結構加入至屬性集。  
  
 *fltValue*  
 [in]用來初始化的屬性值的浮點值`DBPROP`結構加入至屬性集。  
  
 *dblValue*  
 [in]用來初始化的屬性值的雙精確度浮點值`DBPROP`結構加入至屬性集。  
  
 *cyValue*  
 [in]CY 貨幣值，用來初始化的屬性值`DBPROP`結構加入至屬性集。  
  
### <a name="return-value"></a>傳回值  
 **true**如果已成功加入屬性。 否則，請**false**。 

## <a name="cdbpropset"></a> Cdbpropset:: Cdbpropset
建構函式。 初始化`rgProperties`， `cProperties`，並`guidPropertySet`的欄位[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構。  
  
### <a name="syntax"></a>語法  
  
```cpp
CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>參數  
 *guid*  
 [in]GUID; 用來初始化`guidPropertySet`欄位。  
  
 *propset*  
 [in] 複製建構的另一個 `CDBPropSet` 物件。  

## <a name="setguid"></a> Cdbpropset:: Setguid
設定組`guidPropertySet`欄位中`DBPROPSET`結構。  
  
### <a name="syntax"></a>語法  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *guid*  
 [in]GUID; 用來設定`guidPropertySet`欄位[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構。  
  
### <a name="remarks"></a>備註  
 可以設定此欄位[建構函式](../../data/oledb/cdbpropset-cdbpropset.md)以及。  

## <a name="op_equal"></a> Cdbpropset:: Operator =
將一個屬性集的內容指派給另一個屬性集。  
  
### <a name="syntax"></a>語法  
  
```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();  
```  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET 結構](/previous-versions/windows/desktop/ms714367\(v=vs.85\))   
 [DBPROP 結構](/previous-versions/windows/desktop/ms717970\(v=vs.85\))