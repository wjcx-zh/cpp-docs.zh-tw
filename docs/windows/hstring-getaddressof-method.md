---
title: 'Hstring:: Getaddressof 方法 |Microsoft Docs'
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
ms.openlocfilehash: 4ea49833107bf58443bf4a8238229d1d63a86742
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010343"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf 方法
擷取基礎 HSTRING 控制代碼的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HSTRING* GetAddressOf() throw()  
```  
  
## <a name="return-value"></a>傳回值  
 基礎 HSTRING 控制代碼指標。  
  
## <a name="remarks"></a>備註  
 此作業之後，就會終結基礎 HSTRING 控制代碼的字串值。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)