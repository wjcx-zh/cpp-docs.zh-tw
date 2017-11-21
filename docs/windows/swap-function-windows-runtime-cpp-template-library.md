---
title: "Swap 函式 （Windows 執行階段 c + + 樣板程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::Swap
dev_langs: C++
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b48be8c5cd4702d0d4ee2dd7d541829e3bf94ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="swap-function-windows-runtime-c-template-library"></a>Swap 函式 (Windows 執行階段 C++ 樣板程式庫)
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW inline void Swap(  
   _Inout_ T& left,  
   _Inout_ T& right  
);  
```  
  
#### <a name="parameters"></a>參數  
 `left`  
 第一個引數。  
  
 `right`  
 第二個引數。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 交換兩個指定的引數的值。  
  
## <a name="requirements"></a>需求  
 **標頭：** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)