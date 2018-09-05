---
title: begin 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4954e98c1e6f1da30e321aad0c0e37cc5c1ab994
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765356"
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
 向量的集合\<T > 或 VectorView\<T > 物件存取的 IVector\<T > 或 IVectorView\<T > 介面。  
  
 `i`  
 任意物件集合的 Windows 執行階段存取的 IIterable\<T > 介面。  
  
### <a name="return-value"></a>傳回值  
 指向集合開頭的迭代器。  
  
### <a name="remarks"></a>備註  
 前兩個樣板函式會傳回迭代器，第三個樣板函式會傳回輸入迭代器。  
  
 VectorIterator 開始所傳回的物件會儲存類型 VectorProxy 項目的 proxy 迭代器\<T >。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>另請參閱  
 [Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)