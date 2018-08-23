---
title: IDBPropertiesImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0dfc28a510ab9fcc18149f1cd96037e6754d3d7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571665"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 類別
提供的實作`IDBProperties`介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IDBPropertiesImpl`。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|傳回目前所設定的資料來源物件初始化屬性群組中目前所設定的屬性值的資料來源、 資料來源資訊，並初始化屬性群組中的屬性值列舉值。|  
|[GetPropertyInfo](#getpropertyinfo)|傳回提供者所支援的所有屬性的相關資訊。|  
|[SetProperties](#setproperties)|列舉值的資料來源，並初始化屬性群組，針對資料來源物件或初始化屬性群組中，設定屬性。|  
  
## <a name="remarks"></a>備註  
 [IDBProperties](/previous-versions/windows/desktop/ms719607\(v=vs.85\))是資料來源物件的強制介面和列舉值的選用介面。 不過，如果列舉程式會公開[IDBInitialize](/previous-versions/windows/desktop/ms713706\(v=vs.85\))，它必須公開`IDBProperties`。 `IDBPropertiesImpl` 會實作`IDBProperties`使用所定義的靜態函式[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

## <a name="getproperties"></a> Idbpropertiesimpl:: Getproperties
傳回目前所設定的資料來源物件初始化屬性群組中目前所設定的屬性值的資料來源、 資料來源資訊，並初始化屬性群組中的屬性值列舉值。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[idbproperties:: Getproperties](/previous-versions/windows/desktop/ms714344\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
 某些參數會對應至*OLE DB 程式設計人員參考*參數中所述的不同名稱的`IDBProperties::GetProperties`:  
  
|OLE DB 範本參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
### <a name="remarks"></a>備註  
 如果提供者初始化時，這個方法會傳回 DBPROPSET_DATASOURCE，DBPROPSET_DATASOURCEINFO、 的屬性值的資料來源物件目前所設定的 DBPROPSET_DBINIT 屬性群組。 如果尚未初始化提供者，它會傳回僅限 DBPROPSET_DBINIT 群組屬性。 
  
## <a name="getpropertyinfo"></a> Idbpropertiesimpl:: Getpropertyinfo
傳回資料來源所支援的屬性資訊。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[idbproperties:: Getpropertyinfo](/previous-versions/windows/desktop/ms718175\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
 某些參數會對應至*OLE DB 程式設計人員參考*參數中所述的不同名稱的`IDBProperties::GetPropertyInfo`:  
  
|OLE DB 範本參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
  
### <a name="remarks"></a>備註  
 會使用[idbinitializeimpl:: M_pcutlpropinfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)來實作這項功能。 

## <a name="setproperties"></a> Idbpropertiesimpl:: Setproperties
列舉值的資料來源，並初始化屬性群組，針對資料來源物件或初始化屬性群組中，設定屬性。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[idbproperties:: Setproperties](/previous-versions/windows/desktop/ms723049\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 如果提供者初始化時，此方法會設定 DBPROPSET_DATASOURCE，DBPROPSET_DATASOURCEINFO、 的屬性值的資料來源物件的 DBPROPSET_DBINIT 屬性群組。 如果尚未初始化提供者，它會設定僅限 DBPROPSET_DBINIT 群組屬性。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)