---
title: "Platform:: box 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Box
dev_langs: C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 101c3b3bc5572dbf8bf87ed3730abbbee3157404
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformbox-class"></a>Platform::Box 類別
允許將實值類型 (例如 `Windows::Foundation::DateTime` ) 或純量類型 (例如 `int` ) 儲存在 `Platform::Object` 類型中。 通常不需要明確使用 `Box` ，因為當您將實值類型轉換成 `Object^`時，將會隱含地進行 Boxing 作業。  
  
### <a name="syntax"></a>語法  
  
```cpp  
ref class Box abstract;  
```  
  ### <a name="remarks"></a>備註  
  
### <a name="requirements"></a>需求  
 **標頭：** vccorlib.h  
  
 **命名空間：** Platform
|成員|說明|  
|------------|-----------------|
|[Box](#ctor)|建立`Box`其可封裝指定類型的值。|
|[運算子方塊&lt;const T&gt;^](#box-const-t)|可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。|
|[運算子方塊&lt;常數 volatile T&gt;^](#box-const-volatile-t)|可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。 |
|[運算子方塊&lt;T&gt;^](#box-t)|可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。|
|[運算子方塊&lt;volatile T&gt;^](#box-volatile-t)|可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。|
|[Box:: operator T](#t)|可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。| 
## <a name="ctor"></a>Box:: box 建構函式
建立`Box`其可封裝指定類型的值。 | |[值屬性](#value)|傳回值，會封裝在`Box`物件。 |  
### <a name="syntax"></a>語法  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>參數  
 `valueArg`  
 為 boxed 值的類型 — 例如， `int`， `bool`， `float64`， `DateTime`。  
  

## <a name="box-const-t"></a>Box::&lt;const T&gt;^ 運算子
可以透過 Boxing 處理，從 `const` 實值類別 `T` 或 `enum` 類別 `T` 轉換為 `Box<T>`。  
  
### <a name="syntax"></a>語法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 任何實值類別、實值結構或列舉類型。 包含內建的型別中[預設命名空間](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>傳回值  
 A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。  
  
## <a name="box-const-volatile-t"></a>Box::&lt;常數 volatile T&gt;^ 運算子
可以透過 Boxing 處理，從 `const volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。  
  
### <a name="syntax"></a>語法  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 任何列舉類型、實值類別或實值結構。 包含內建的型別中[預設命名空間](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>傳回值  
 A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。  
  
## <a name="box-t"></a>Box::&lt;T&gt;^ 運算子
可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。  
  
### <a name="syntax"></a>語法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 任何列舉類型、實值類別或實值結構。 包含內建的型別中[預設命名空間](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>傳回值  
 A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。  
  
## <a name="box-volatile-t"></a>Box::&lt;volatile T&gt;^ 運算子
可以透過 Boxing 處理，從 `volatile` 實值類別 `T` 或 `enum` 類型 `T` 轉換為 `Box<T>`。  
  
### <a name="syntax"></a>語法  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 任何列舉類型、實值類別或實值結構。 包含內建的型別中[預設命名空間](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>傳回值  
 A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。  
  
## <a name="t"></a>Box:: operator T 運算子
可以透過 Boxing 處理，從 `T` 實值類別或 `enum` 類別 `T` 轉換為 `Box<T>`。  
  
### <a name="syntax"></a>語法  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 任何列舉類型、實值類別或實值結構。 包含內建的型別中[預設命名空間](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>傳回值  
 A `Platform::Box<T>^` ref 類別中的執行個體，表示原始值進行 boxed 處理。  
  

## <a name="value"></a>Box:: value 屬性
傳回 `Box` 物件中封裝的值。  
  
### <a name="syntax"></a>語法  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
### <a name="return-value"></a>傳回值  
 傳回 Boxed 值，與該值進行 Boxed 處理之前的原始類型相同。  
  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)   
 [Boxing](../cppcx/boxing-c-cx.md)