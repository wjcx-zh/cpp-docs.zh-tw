---
title: 'Iconverttypeimpl:: Canconvert |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2f7e32fd01c932f24b617951d601ddcfe7fb5af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099884"
---
# <a name="iconverttypeimplcanconvert"></a>IConvertTypeImpl::CanConvert
命令或上一個資料列集，請提供可用性資訊的型別轉換。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 使用中的 OLE DB 資料轉換`MSADC.DLL`。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IConvertTypeImpl 類別](../../data/oledb/iconverttypeimpl-class.md)