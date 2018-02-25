---
title: "Idbpropertiesimpl:: Setproperties |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- SetProperties method
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f556cf112f9364cd2459bd4d1fdc30691281ca30
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimplsetproperties"></a>IDBPropertiesImpl::SetProperties
列舉值的資料來源和初始化屬性群組，資料來源物件或初始化屬性群組中，設定屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[idbproperties:: Setproperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 如果提供者初始化時，這個方法會設定中的屬性值**DBPROPSET_DATASOURCE**， **DBPROPSET_DATASOURCEINFO**， **DBPROPSET_DBINIT**屬性資料來源物件的群組。 如果未初始化提供者，它會設定**DBPROPSET_DBINIT**群組只包含內容。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IDBPropertiesImpl 類別](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)