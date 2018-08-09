---
title: 'Runtimeclass:: Getiids 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91d0a082a422657f6716e16c8b53ab33e0313d82
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020131"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids 方法
取得陣列，其中可包含的介面識別碼，藉由將目前**RuntimeClass**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>參數  
 *iidCount*  
 這項作業完成時，陣列中的元素總數*iid*。  
  
 *iid*  
 這項作業完成時，介面識別碼的陣列的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，E_OUTOFMEMORY。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)