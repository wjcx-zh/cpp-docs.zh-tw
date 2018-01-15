---
title: "Move 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::Move
dev_langs: C++
helpviewer_keywords: Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 360302840d007dde00a16073b546ba31f7ed19b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="move-function"></a>Move 函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   class T  
>  
inline typename RemoveReference<T>::Type&& Move(  
   _Inout_ T&& arg  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 引數型別。  
  
 `arg`  
 要移動的引數。  
  
## <a name="return-value"></a>傳回值  
 參數`arg`之後參考或右值參考的特性，如果有的話，已移除。  
  
## <a name="remarks"></a>備註  
 將指定的引數從一個位置移到另一個。  
  
 如需詳細資訊，請參閱**移動語意**區段[右值參考宣告子： & （& s)](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)