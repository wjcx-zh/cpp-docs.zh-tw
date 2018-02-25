---
title: "tile_barrier 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7d868b4bd677d207590de6449e3d5643001e857
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="tilebarrier-class"></a>tile_barrier 類別
同步處理的使用中執行緒群組 （磚） 執行的執行緒執行`wait`方法。 執行階段可以具現化這個類別。  
  
### <a name="syntax"></a>語法 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[tile_barrier 建構函式](#ctor)|初始化 `tile_barrier` 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[wait](#wait)|指示來停止執行，直到在磚中的所有執行緒都完成等候的執行緒群組 （磚） 中的所有執行緒。|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|阻擋所有執行緒，直到完成為止所有記憶體存取在磚中的，磚中的所有執行緒的執行已達到此呼叫。|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|阻擋所有執行緒，直到所有的全域記憶體存取在磚中的執行已經完成，而在磚中的所有執行緒已都達到此呼叫。|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|封鎖，直到所有的磚中的所有執行緒執行`tile_static`已經完成的記憶體存取，而在磚中的所有執行緒已都達到此呼叫。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tile_barrier`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  

## <a name="tile_barrier__ctor">tile_barrier 建構函式</a>  
 藉由複製現有初始化類別的新執行個體。  
  
### <a name="syntax"></a>語法 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `tile_barrier`来複製物件。  

## <a name="wait"></a>  等候 
指示來停止執行，直到在磚中的所有執行緒都完成等候的執行緒群組 （磚） 中的所有執行緒。  
  
### <a name="syntax"></a>語法 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence   
區塊執行的所有執行緒，直到在磚中的所有執行緒已都達到此呼叫在磚中。 這可確保所有記憶體存取檢視中 [執行緒] 磚中，其他執行緒，且已經執行程式的順序。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence   
區塊執行的所有執行緒，直到在磚中的所有執行緒已都達到此呼叫在磚中。 這可確保所有的全域記憶體存取會顯示執行緒在磚中，其他執行緒，而且已經執行程式的順序。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence   
區塊執行的所有執行緒，直到在磚中的所有執行緒已都達到此呼叫在磚中。 如此可確保`tile_static`記憶體存取可以看見其他執行緒的執行緒在磚中，而且已經執行程式的順序。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
