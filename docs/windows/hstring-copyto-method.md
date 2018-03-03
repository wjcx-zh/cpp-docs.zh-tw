---
title: "Hstring:: Copyto 方法 |Microsoft 文件"
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
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dd0cab708832a9872c55c53ad058fe0cd78e6bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hstringcopyto-method"></a>HString::CopyTo 方法
複製目前 HString HSTRING 物件的物件。  
  
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
 [HString 類別](../windows/hstring-class.md)