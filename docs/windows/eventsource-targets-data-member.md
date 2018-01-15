---
title: "Eventsource:: Targets_ 資料成員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::targets_
dev_langs: C++
helpviewer_keywords: targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1fb14e7cfa25cd34d6bbaf6d0b48870f1d93f991
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ 資料成員
陣列的一個或多個事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>備註  
 目前的 EventSource 物件所代表的事件發生時，會呼叫事件處理常式。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>請參閱
 [EventSource 類別](../windows/eventsource-class.md)