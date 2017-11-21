---
title: "affinity_partitioner 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs: C++
helpviewer_keywords: affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3f1ed1b9fee094669a2c1d0ce7c7e51f6d8d5fcd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner 類別
`affinity_partitioner` 類別與 `static_partitioner` 類別類似，不過，它可依據對應背景工作執行緒子範圍的選擇來改善快取依存性。 當迴圈重複執行相同的資料集，且快取容納得下該資料時，它可以大幅改善效能。 請注意，若要取得資料位置的優勢，必須使用相同的 `affinity_partitioner` 物件來搭配平行迴圈的後續反覆項目，且該平行迴圈應執行於特定資料集上。  
  
## <a name="syntax"></a>語法  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[affinity_partitioner](#ctor)|建構 `affinity_partitioner` 物件。|  
|[~ affinity_partitioner 解構函式](#dtor)|終結`affinity_partitioner`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `affinity_partitioner`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="dtor"></a>~ affinity_partitioner 

 終結`affinity_partitioner`物件。  
  
```
~affinity_partitioner();
```  
  
##  <a name="ctor"></a>affinity_partitioner 

 建構 `affinity_partitioner` 物件。  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
