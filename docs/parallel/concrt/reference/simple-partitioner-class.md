---
title: "simple_partitioner 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 08d378c841fd9181fe9a2cf918bde9fe3ebbdc32
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="simplepartitioner-class"></a>simple_partitioner 類別
`simple_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將這個範圍分割成區塊，每個區塊都有由區塊大小指定之反覆項目的最少次數。  
  
## <a name="syntax"></a>語法  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[simple_partitioner](#ctor)|建構 `simple_partitioner` 物件。|  
|[~ simple_partitioner 解構函式](#dtor)|終結 `simple_partitioner` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `simple_partitioner`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="dtor"></a>~ simple_partitioner 

 終結 `simple_partitioner` 物件。  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a>simple_partitioner 

 建構 `simple_partitioner` 物件。  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>參數  
 `_Chunk_size`  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

