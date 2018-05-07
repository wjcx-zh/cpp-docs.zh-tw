---
title: 'Cdatasource:: Getproperty |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
dev_langs:
- C++
helpviewer_keywords:
- GetProperty method
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afe21f6f41491a4f62eda09e2df43aa470417e20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourcegetproperty"></a>CDataSource::GetProperty
傳回連接的資料來源物件的指定屬性的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]GUID，識別要傳回的屬性設定的屬性。  
  
 `propid`  
 [in]屬性 ID 的屬性來傳回。  
  
 *pVariant*  
 [out]Variant 的指標位置**GetProperty**傳回屬性的值。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 若要取得多個屬性，請使用[GetProperties](../../data/oledb/cdatasource-getproperties.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)