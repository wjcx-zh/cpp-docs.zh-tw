---
title: 'Idbpropertiesimpl:: Setproperties |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5067173da531bb8a4f437666ccfc9c9c61bb47f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106475"
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
  
## <a name="see-also"></a>另請參閱  
 [IDBPropertiesImpl 類別](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)