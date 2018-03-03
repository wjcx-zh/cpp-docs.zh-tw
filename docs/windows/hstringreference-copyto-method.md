---
title: "Hstringreference:: Copyto 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fb6ac1f645207c048e88078c7fcdc8297f8d1b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo 方法
複製目前 HStringReference HSTRING 物件的物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 接收複製 HSTRING。  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫[WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx)函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)