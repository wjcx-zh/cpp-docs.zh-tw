---
title: 'Hstring:: Getaddressof 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d4804373045d12c2e251e2de61b7aefd52ec916
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874664"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf 方法
擷取基礎 HSTRING 控制代碼的指標。  
  
## <a name="syntax"></a>語法  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## <a name="return-value"></a>傳回值  
 基礎 HSTRING 控制代碼指標。  
  
## <a name="remarks"></a>備註  
 這個作業之後，就會終結基礎 HSTRING 控制代碼的字串值。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)