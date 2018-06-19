---
title: affinity_partitioner 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2242346bda717117e2b43ba108d86fd2a77a3b58
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691127"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner 類別
`affinity_partitioner` 類別與 `static_partitioner` 類別類似，不過，它可依據對應背景工作執行緒子範圍的選擇來改善快取依存性。 當迴圈重複執行相同的資料集，且快取容納得下該資料時，它可以大幅改善效能。 請注意，若要取得資料位置的優勢，必須使用相同的 `affinity_partitioner` 物件來搭配平行迴圈的後續反覆項目，且該平行迴圈應執行於特定資料集上。  
  
## <a name="syntax"></a>語法  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[affinity_partitioner](#ctor)|建構 `affinity_partitioner` 物件。|  
|[~ affinity_partitioner 解構函式](#dtor)|終結`affinity_partitioner`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `affinity_partitioner`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="dtor"></a> ~affinity_partitioner 

 終結`affinity_partitioner`物件。  
  
```
~affinity_partitioner();
```  
  
##  <a name="ctor"></a> affinity_partitioner 

 建構 `affinity_partitioner` 物件。  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
