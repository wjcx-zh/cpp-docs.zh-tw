---
title: "Hstringreference:: Copyto 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f93dd138490834451a665761f4c575a751bfe7ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)