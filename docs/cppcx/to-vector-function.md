---
title: "to_vector 函式 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 028acf4b3b049f13c7a9ac2204157432fa144caa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="tovector-function"></a>to_vector 函式
傳回 `std::vector` ，其值與指定的 IVector 或 IVectorView 參數的基礎集合相同。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板類型參數。  
  
 `v`  
 IVector 或 IVectorView 介面，提供對基礎 Vector 或 VectorView 物件的存取。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>請參閱  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)