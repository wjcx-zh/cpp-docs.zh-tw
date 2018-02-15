---
title: IConvertTypeImpl::CanConvert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 47b1d5ddf0d5ad3cba1745767bfe82256a39cdd8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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
  
## <a name="see-also"></a>請參閱  
 [IConvertTypeImpl 類別](../../data/oledb/iconverttypeimpl-class.md)