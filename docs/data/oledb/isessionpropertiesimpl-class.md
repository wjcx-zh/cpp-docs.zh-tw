---
title: ISessionPropertiesImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3759b67ef5d9ee9832649b3b0d516dbfb04440b
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322016"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 類別
提供實作[ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`ISessionPropertiesImpl`。  
  
 *PropClass*  
 使用者可定義屬性類別，預設值為*T*。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|傳回目前所設定的工作階段的工作階段屬性群組中的屬性清單。|  
|[SetProperties](#setproperties)|設定工作階段屬性群組中的屬性。|  
  
## <a name="remarks"></a>備註  
 在 工作階段上必要的介面。 這個類別會實作藉由呼叫靜態函式所定義的工作階段屬性[屬性集對應](../../data/oledb/begin-propset-map.md)。 在您的工作階段類別，應該指定屬性集對應。  
  
## <a name="getproperties"></a> Isessionpropertiesimpl:: Getproperties
傳回清單中的屬性`DBPROPSET_SESSION`目前所設定的工作階段的屬性群組。  
  
### <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(GetProperties)(ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ISessionProperties::GetProperties](https://msdn.microsoft.com/library/ms723643.aspx)中*OLE DB 程式設計人員參考*。 

## <a name="setproperties"></a> Isessionpropertiesimpl:: Setproperties
在 設定屬性`DBPROPSET_SESSION`屬性群組。  
  
### <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ISessionProperties::SetProperties](https://msdn.microsoft.com/library/ms714405.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
