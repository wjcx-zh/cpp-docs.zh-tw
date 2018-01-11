---
title: "預設值 (OpenMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: default
dev_langs: C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25b1dd9eb2dcdd5a0a41992ed562ddd290014e25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="default-openmp"></a>default (OpenMP)
指定在平行區域不限範圍變數的行為。  
  
## <a name="syntax"></a>語法  
  
```  
default(shared | none)  
```  
  
## <a name="remarks"></a>備註  
 `shared`這實際上是如果`default`未指定子句，表示，在平行區域中的任何變數會視為與指定[共用](../../../parallel/openmp/reference/shared-openmp.md)子句。 `none`表示不在範圍與在平行區域中所使用的任何變數[私人](../../../parallel/openmp/reference/private-openmp.md)，[共用](../../../parallel/openmp/reference/shared-openmp.md)，[減少](../../../parallel/openmp/reference/reduction.md)， [firstprivate](../../../parallel/openmp/reference/firstprivate.md)，或[lastprivate](../../../parallel/openmp/reference/lastprivate.md)子句會造成編譯器錯誤。  
  
 `default`適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.5 預設](../../../parallel/openmp/2-7-2-5-default.md)。  
  
## <a name="example"></a>範例  
 請參閱[私人](../../../parallel/openmp/reference/private-openmp.md)的使用範例`default`。  
  
## <a name="see-also"></a>請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)