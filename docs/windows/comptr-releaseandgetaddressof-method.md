---
title: 'Comptr:: Releaseandgetaddressof 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32d846a1fc41596812ca6e8578f25f9ae8115182
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883795"
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
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)   
 [ComPtr::ptr_ 資料成員](../windows/comptr-ptr-data-member.md)