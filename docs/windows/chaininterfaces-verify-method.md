---
title: 'Chaininterfaces:: Verify 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81b3a166215f7731a43333e230621072d760260c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013528"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify 方法
確認每個介面定義的範本參數*I0*透過*I9*繼承`IUnknown`及/或`IInspectable`，而且*I0*繼承自*I1*透過*I9*。  
  
## <a name="syntax"></a>語法  
  
```cpp  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>備註  
 如果驗證作業失敗， **static_assert**發出描述失敗的錯誤訊息。  

 範本參數*I0*並*I1*是必要的以及參數*I2*透過*I9*是選擇性的。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)