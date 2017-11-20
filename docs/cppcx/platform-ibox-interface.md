---
title: "Platform:: ibox 介面 |Microsoft 文件"
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
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e3cbeed5893e6a757ca5ac3c17e596d3a1526e46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformibox-interface"></a>Platform::IBox 介面
[Platform::IBox](../cppcx/platform-ibox-interface.md) 介面是適用於 `Windows::Foundation::IReference` 介面的 C++ 名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 boxed 值的類型。  
  
### <a name="remarks"></a>備註  
 `IBox<T>` 介面主要是在內部用來代表可為 Null 的實值類型 (如 [實值類別與結構 (C++/CX)](../cppcx/value-classes-and-structs-c-cx.md)中所述)。 此介面也用來將傳遞給 C++ 方法的實值類型進行 box 處理，這些方法會採用 `Object^`類型的參數。 您可以明確地將輸入參數宣告為 `IBox<SomeValueType>`。 如需範例，請參閱[Boxing](../cppcx/boxing-c-cx.md)。  
  
### <a name="requirements"></a>需求  
  
### <a name="members"></a>成員  
 `Platform::IBox` 介面繼承自 [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) 介面。 `IBox` 有這些成員：  
  
 **屬性**  
  
|方法|描述|  
|------------|-----------------|  
|[值](#value)|傳回之前儲存在這個 `IBox` 執行個體中的 Unboxed 值。|  

## <a name="value"></a>Ibox:: Value 屬性
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
  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)