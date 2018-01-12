---
title: "Platform:: iboxarray 介面 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs: C++
helpviewer_keywords: Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 421f8517b8a96c40bb44dd959eba90b1bf903113
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray 介面
`IBoxArray` 是實值類型陣列的包裝函式，這些實值類型會在不同的應用程式二進位介面 (ABI) 之間傳遞或是儲存在 `Platform::Object^` 元素的集合中，例如在 XAML 控制項中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 每個陣列元素中 Boxed 值的類型。  
  
### <a name="remarks"></a>備註  
 `IBoxArray`是 C + + /CX 名稱`Windows::Foundation::IReferenceArray`。  
  
### <a name="members"></a>成員  
 `IBoxArray` 介面繼承自 `IValueType` 介面。 `IBoxArray` 也有這些成員：  
  
|方法|描述|  
|------------|-----------------|  
|[值](#value)|傳回之前儲存在這個 `IBoxArray` 執行個體中的 Unboxed 陣列。|  

## <a name="value"></a>Iboxarray:: Value 屬性
傳回一開始儲存在這個物件中的值。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 boxed 值的類型。  
  
### <a name="property-valuereturn-value"></a>屬性值/傳回值  
 傳回一開始儲存在這個物件中的值。  
  
### <a name="remarks"></a>備註  
 如需範例，請參閱[Boxing](../cppcx/boxing-c-cx.md)。  
  
  
## <a name="see-also"></a>請參閱  
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)