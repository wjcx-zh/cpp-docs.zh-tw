---
title: MakeAndInitialize 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4bebe74ae855cf303f09dd8798fcceec0df455b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 函式
初始化指定的 Windows 執行階段類別。 使用此函式來具現化在相同模組中定義的元件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <typename T, typename I,   
typename TArg1,   
typename TArg2,   
typename TArg3,   
typename TArg4,   
typename TArg5,   
typename TArg6,   
typename TArg7,   
typename TArg8,   
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 使用者指定的類別繼承自`WRL::RuntimeClass`。  
  
 `TArg1`  
 傳遞至指定的執行階段類別的引數 1 的類型。  
  
 `TArg2`  
 傳遞至指定的執行階段類別的引數 2 的型別。  
  
 `TArg3`  
 傳遞至指定的執行階段類別的引數 3 的類型。  
  
 `TArg4`  
 傳遞至指定的執行階段類別的引數 4 的類型。  
  
 `TArg5`  
 傳遞至指定的執行階段類別的引數 5 的型別。  
  
 `TArg6`  
 傳遞至指定的執行階段類別的引數 6 種。  
  
 `TArg7`  
 傳遞至指定的執行階段類別的引數 7 的類型。  
  
 `TArg8`  
 傳遞至指定的執行階段類別的引數 8 的型別。  
  
 `TArg9`  
 型別傳遞至指定的執行階段類別的引數 9。  
  
 `arg1`  
 傳遞至指定的執行階段類別的引數 1。  
  
 `arg2`  
 傳遞至指定的執行階段類別的引數 2。  
  
 `arg3`  
 傳遞至指定的執行階段類別的引數 3。  
  
 `arg4`  
 傳遞至指定的執行階段類別的引數 4。  
  
 `arg5`  
 傳遞至指定的執行階段類別的引數 5。  
  
 `arg6`  
 傳遞至指定的執行階段類別的引數 6。  
  
 `arg7`  
 傳遞至指定的執行階段類別的引數 7。  
  
 `arg8`  
 傳遞至指定的執行階段類別的引數 8。  
  
 `arg9`  
 傳遞至指定的執行階段類別的引數 9。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT` 值。  
  
## <a name="remarks"></a>備註  
 請參閱[如何： 直接執行個體化 WRL 元件](../windows/how-to-instantiate-wrl-components-directly.md)若要了解此函式之間的差異和[Microsoft::WRL::Make](../windows/make-function.md)，及範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)