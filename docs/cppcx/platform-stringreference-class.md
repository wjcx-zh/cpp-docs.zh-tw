---
title: "Platform:: stringreference 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
dev_langs: C++
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3617f4e9209a9726fcf4801e803259ef921c7b60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformstringreference-class"></a>Platform::StringReference 類別
可以用來從 `Platform::String^` 輸入參數將字串資料傳遞給其他方法的最佳化類型，可將複製作業減至最少。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class StringReference  
```  
  
### <a name="remarks"></a>備註  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Stringreference:: Stringreference](#ctor)|用來建立 `StringReference`執行個體的兩個建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Stringreference:: Data](#data)|傳回字串資料當做 char16 值的陣列。|  
|[Stringreference:: Length](#length)|傳回字串中的字元數。|  
|[Stringreference:: Gethstring](#gethstring)|傳回字串資料當做 HSTRING。|  
|[Stringreference:: Getstring](#getstring)|傳回字串資料當做 `Platform::String^`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[Stringreference:: Operator =](#operator-assign)|將 `StringReference` 指定給新的 `StringReference` 執行個體。|  
|[Stringreference](#operator-call)|將 `StringReference` 轉換成 `Platform::String^`。|  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **標頭：** vccorlib.h  

## <a name="data"></a>Stringreference:: Data 方法
傳回這個內容`StringReference`當做 char16 值的陣列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
const ::default::char16 * Data() const  
```  
  
### <a name="return-value"></a>傳回值  
 char16 UNICODE 文字字元陣列。  
  


## <a name="gethstring"></a>Stringreference:: Gethstring 方法
傳回 `__abi_HSTRING` 形式的字串內容。  
  
### <a name="syntax"></a>語法  
  
```cpp  
__abi_HSTRING GetHSTRING() const  
  
```  
  
### <a name="return-value"></a>傳回值  
 包含字串資料的 `__abi_HSTRING`。  
  
### <a name="remarks"></a>備註  
  


## <a name="getstring"></a>Stringreference:: Getstring 方法
傳回 `Platform::String^` 形式的字串內容。  
  
### <a name="syntax"></a>語法  
  
```cpp  
__declspec(no_release_return) __declspec(no_refcount)  
    ::Platform::String^ GetString() const  
```  
  
### <a name="return-value"></a>傳回值  
 包含字串資料的 `Platform::String^`。  

## <a name="length"></a>Stringreference:: Length 方法
傳回字串中的字元數。  
  
### <a name="syntax"></a>語法  
  
```cpp  
unsigned int Length() const  
```  
  
### <a name="return-value"></a>傳回值  
 指定字串中之字元數的不帶正負號的整數。  
  
### <a name="remarks"></a>備註  
  


## <a name="operator-assign"></a>Stringreference:: Operator = 運算子
將指定的物件指定給目前的 `StringReference` 物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
StringReference& operator=(const StringReference& __fstrArg);  
StringReference& operator=(const ::default::char16* __strArg);    
```  
  
### <a name="parameters"></a>參數  
 `__fstrArg`  
 用來初始化目前 `StringReference` 物件之 `StringReference` 物件的位址。  
  
 `__strArg`  
 用來初始化目前 `StringReference` 物件之 char16 值陣列的指標。  
  
### <a name="return-value"></a>傳回值  
 類型為 `StringReference` 之物件的參考。  
  
### <a name="remarks"></a>備註  
 因為`StringReference`是標準 c + + 類別而不是 ref 類別，它不會顯示在**物件瀏覽器**。  
  


## <a name="operator-call"></a>Stringreference 運算子
將 `StringReference` 物件轉換成 `Platform::String^` 物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
__declspec(no_release_return) __declspec(no_refcount)  
         operator ::Platform::String^() const  
  
```  
  
### <a name="return-value"></a>傳回值  
 `Platform::String` 類型之物件的控制代碼。  

## <a name="ctor"></a>  StringReference::StringReference 建構函式
初始化 `StringReference` 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
### <a name="parameters"></a>參數  
 `__fstrArg`  
 其資料用來初始化新執行個體的 `StringReference`。  
  
 `__strArg`  
 用來初始化新執行個體之 char16 值陣列的指標。  
  
 `__lenArg`  
 `__strArg` 中的元素數目。  
  
### <a name="remarks"></a>備註  
 此建構函式的第一個版本是預設建構函式。 第二個版本會從 `StringReference` 參數指定的物件初始化新的 `__fstrArg` 執行個體類別。 第三個和第四個多載會初始化新`StringReference`char16 值的陣列中的執行個體。 char16 表示 16 位元的 UNICODE 文字字元。  
  


  
## <a name="see-also"></a>請參閱  
 [Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)