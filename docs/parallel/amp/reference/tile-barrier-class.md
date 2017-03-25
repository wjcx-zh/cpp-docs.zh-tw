---
title: "tile_barrier 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 247828a6de3a5820d75623ee438810b563f04519
ms.lasthandoff: 03/17/2017

---
# <a name="tilebarrier-class"></a>tile_barrier 類別
同步處理的執行緒群組 （並排顯示） 中使用來執行的執行緒執行`wait`方法。 執行階段可以具現化這個類別。  
  
### <a name="syntax"></a>語法 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[tile_barrier 建構函式](#ctor)|初始化 `tile_barrier` 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[等候](#wait)|指示要停止執行，直到磚中的所有執行緒都完成等候的執行緒群組 （並排） 中的所有執行緒。|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|區塊執行直到完成為止的所有記憶體存取在磚中的所有執行緒和並排顯示中的所有執行緒都已達到此呼叫。|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|所有的執行緒，直到所有的全域記憶體存取在磚中的區塊執行已完成，且並排顯示中的所有執行緒都已都達到此呼叫。|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|阻礙磚中的所有執行緒的執行，直到所有`tile_static`已完成的記憶體存取，且並排顯示中的所有執行緒都已都達到此呼叫。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tile_barrier`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  

## <a name="tile_barrier__ctor"></a>tile_barrier 建構函式  
 藉由複製現有初始化類別的新執行個體。  
  
### <a name="syntax"></a>語法 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `tile_barrier`来複製物件。  

## <a name="wait"></a>等候 
指示來停止執行，直到磚中的所有執行緒都完成等候的執行緒群組 （並排） 中的所有執行緒。  
  
### <a name="syntax"></a>語法 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence   
區塊執行的所有執行緒，直到磚中的所有執行緒都到達此呼叫在磚中。 這可確保所有的記憶體存取會顯示 [執行緒] 磚中，在其他執行緒，而且程式的順序在已經執行。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>wait_with_global_memory_fence   
區塊執行的所有執行緒，直到磚中的所有執行緒都到達此呼叫在磚中。 這可確保所有的全域記憶體存取會顯示 [執行緒] 磚中，在其他執行緒，而且程式的順序在已經執行。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>wait_with_tile_static_memory_fence   
區塊執行的所有執行緒，直到磚中的所有執行緒都到達此呼叫在磚中。 這可確保`tile_static`記憶體存取會顯示 [執行緒] 磚中，在其他執行緒，而且在程式的順序已經執行。  
  
### <a name="syntax"></a>語法 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

