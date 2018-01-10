---
title: "Comptr:: Releaseandgetaddressof 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs: C++
helpviewer_keywords: ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be56e7afb23295e9b03d801943af25c652d18758
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf 方法
釋放與這個 ComPtr 相關聯的介面，然後擷取 [ptr_](../windows/comptr-ptr-data-member.md) 資料成員的位址，其中包含已釋放之介面的指標。  
  
## <a name="syntax"></a>語法  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>傳回值  
 位址[ptr_](../windows/comptr-ptr-data-member.md)這個 ComPtr 資料成員。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ComPtr 類別](../windows/comptr-class.md)   
 [ComPtr::ptr_ 資料成員](../windows/comptr-ptr-data-member.md)