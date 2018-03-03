---
title: "Weakref:: Weakref 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125fe25179ddbe975530a0c368a4dfc7e4caaf1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef 建構函式
初始化 WeakRef 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ptr`  
 指標、 參考或右值參考，來初始化目前的 WeakRef 物件的現有物件。  
  
## <a name="remarks"></a>備註  
 第一個建構函式會初始化空的 WeakRef 物件。 第二個建構函式初始化 WeakRef 物件從指標到 IWeakReference 介面。 第三個建構函式初始化 WeakRef 物件從參考 ComPtr\< IWeakReference > 物件。 第四個和第五個建構函式會初始化 WeakRef 物件從另一個 WeakRef 物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [WeakRef 類別](../windows/weakref-class.md)