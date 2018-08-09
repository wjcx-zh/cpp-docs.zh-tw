---
title: 'Comptrref:: Getaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 797df323-a2fa-412b-ab60-32cce3721096
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7811bcc61d5390257b7cbee95e2c504d3e376298
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641137"
---
# <a name="comptrrefgetaddressof-method"></a>ComPtrRef::GetAddressOf 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
InterfaceType* const * GetAddressOf() const;  
```  
  
## <a name="return-value"></a>傳回值  
 代表由目前之介面的指標位址**ComPtrRef**物件。  
  
## <a name="remarks"></a>備註  
 擷取目前所代表之介面的指標位址**ComPtrRef**物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [ComPtrRef 類別](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)