---
title: "Hstring:: Getaddressof 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4c15570b65b62b22f0dd9a7f66f8c244e2bf22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [HString 類別](../windows/hstring-class.md)