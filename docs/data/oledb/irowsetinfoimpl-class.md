---
title: IRowsetInfoImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d07c0e64e969e599393a657d4c41a8dd544901c9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572340"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 類別
提供實作[IRowsetInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\))介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IRowsetInfoImpl`。  
  
 *PropClass*  
 使用者可定義屬性類別，預設值為*T*。 

## <a name="requirements"></a>需求  
 **標頭：** altdb.h   
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|傳回資料列集所支援的所有屬性的目前的設定。|  
|[GetReferencedRowset](#getreferencedrowset)|要套用書籤的資料列集傳回的介面指標。|  
|[GetSpecification](#getspecification)|建立此資料列集物件 （命令或工作階段） 上傳回的介面指標。|  
  
## <a name="remarks"></a>備註  
 在 資料列集上必要的介面。 這個類別會實作所使用的資料列集屬性[屬性集對應](../../data/oledb/begin-propset-map.md)命令類別中定義。 雖然所出現的資料列集類別，使用命令類別的屬性集，資料列集提供它自己的複本，執行階段內容中的命令或工作階段的物件建立時。  
  
## <a name="getproperties"></a> Irowsetinfoimpl:: Getproperties
傳回屬性的目前設定`DBPROPSET_ROWSET`群組。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowsetinfo:: Getproperties](/previous-versions/windows/desktop/ms719611\(v=vs.85\))中*OLE DB 程式設計人員參考*。 

## <a name="getreferencedrowset"></a> Irowsetinfoimpl:: Getreferencedrowset
要套用書籤的資料列集傳回的介面指標。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145\(v=vs.85\))中*OLE DB 程式設計人員參考*。 *IOrdinal*參數必須是書籤資料行。 

## <a name="getspecification"></a> Irowsetinfoimpl:: Getspecification
建立此資料列集物件 （命令或工作階段） 上傳回的介面指標。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 使用這個方法搭配[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)來擷取從資料來源物件的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)