---
title: "begin 函式 |Microsoft 文件"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::begin
dev_langs: C++
helpviewer_keywords: begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d47244e6428979f5319c9ee02f252ef3e559f7ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="begin-function"></a>begin 函式
傳回迭代器，指向指定的介面參數所存取之集合的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板類型參數。  
  
 `v`  
 向量的集合\<T > 或 VectorView\<T > 物件存取透過 Ivector<platform\<T > 或 IVectorView\<T > 介面。  
  
 `i`  
 IIterable 所存取的任意 Windows 執行階段物件的集合\<T > 介面。  
  
### <a name="return-value"></a>傳回值  
 指向集合開頭的迭代器。  
  
### <a name="remarks"></a>備註  
 前兩個樣板函式會傳回迭代器，第三個樣板函式會傳回輸入迭代器。  
  
 所傳回的物件開始的 VectorIterator 是 proxy 迭代器可以儲存的型別 VectorProxy 元素\<T >。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>請參閱  
 [Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)