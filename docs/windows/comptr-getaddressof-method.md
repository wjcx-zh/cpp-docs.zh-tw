---
title: 'Comptr:: Getaddressof 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2da8e134c4ba1ec01a6694cd886d44b14c6cac8c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf 方法
擷取 [ptr_](../windows/comptr-ptr-data-member.md) 資料成員的位址，其中包含這個 ComPtr 所代表之介面的指標。  
  
## <a name="syntax"></a>語法  
  
```  
T* const* GetAddressOf() const;  
T** GetAddressOf();  
```  
  
## <a name="return-value"></a>傳回值  
 變數的位址。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)