---
title: "Idbpropertiesimpl:: Getproperties |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
dev_langs:
- C++
helpviewer_keywords:
- GetProperties method
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 47286d409f6bc9ffe99faffe46db58245c958f92
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimplgetproperties"></a>IDBPropertiesImpl::GetProperties
傳回目前所設定的資料來源物件或目前設於初始化屬性群組中的屬性值的資料來源、 資料來源資訊，以及初始化屬性群組中的屬性值列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(GetProperties)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx)中*OLE DB 程式設計人員參考*。  
  
 有些參數會對應至*OLE DB 程式設計人員參考*參數不同的名稱，如下所述的**IDBProperties::GetProperties**:  
  
|OLE DB 樣板參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## <a name="remarks"></a>備註  
 如果提供者初始化時，這個方法會傳回中的屬性值**DBPROPSET_DATASOURCE**， **DBPROPSET_DATASOURCEINFO**， **DBPROPSET_DBINIT**目前在資料來源物件所設定的屬性群組。 如果未初始化提供者，它會傳回**DBPROPSET_DBINIT**群組只包含內容。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IDBPropertiesImpl 類別](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)