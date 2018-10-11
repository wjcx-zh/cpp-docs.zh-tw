---
title: ICommandPropertiesImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 432fb57b1505733b4f9cbda4e558699a8108a3ad
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083992"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 類別

提供實作[ICommandProperties](/previous-versions/windows/desktop/ms723044)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>參數  

*T*<br/>
您的類別，衍生自  
  
*PropClass*<br/>
您屬性的類別。  

## <a name="requirements"></a>需求  

**Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|目前要求的資料列集的資料列集屬性群組中傳回屬性的清單。|  
|[SetProperties](#setproperties)|設定資料列集屬性群組中的屬性。|  
  
## <a name="remarks"></a>備註  

這是命令的必要參數。 所定義的靜態函式提供實作[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)巨集。  

## <a name="getproperties"></a> Icommandpropertiesimpl:: Getproperties

傳回使用命令的屬性對應的所有要求的屬性集。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>參數  

請參閱[icommandproperties:: Getproperties](/previous-versions/windows/desktop/ms723119)中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="setproperties"></a> Icommandpropertiesimpl:: Setproperties

設定命令物件的屬性。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>參數  

請參閱[icommandproperties:: Setproperties](/previous-versions/windows/desktop/ms711497)中*OLE DB 程式設計人員參考*。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)