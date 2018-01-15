---
title: "Eventtargetarray:: Eventtargetarray 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8c8ada61a18437ed159452355e8286bc9d190f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray 建構函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hr`  
 這個建構函式作業之後，參數`hr`指出配置陣列的成功或失敗。 下表列出可能的值為`hr`。  
  
 S_OK  
 作業成功。  
  
 E_OUTOFMEMORY  
 陣列，無法配置記憶體。  
  
 S_FALSE  
 參數`items`小於或等於零。  
  
 `items`  
 要配置的陣列元素數目。  
  
## <a name="remarks"></a>備註  
 初始化 EventTargetArray 類別的新執行個體。  
  
 EventTargetArray 用來保留 EventSource 物件中的事件處理常式的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [EventTargetArray 類別](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)