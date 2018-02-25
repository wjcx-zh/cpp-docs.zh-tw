---
title: copyin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae680b2af468b9b11a7d2de44966ad554eec0150
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="copyin"></a>copyin
可讓執行緒存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。  
  
## <a name="syntax"></a>語法  
  
```  
copyin(var)  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `var`  
 `threadprivate`存在於之前平行建構將主執行緒中的變數的值初始化的變數。  
  
## <a name="remarks"></a>備註  
 `copyin` 適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## <a name="example"></a>範例  
 請參閱[threadprivate](../../../parallel/openmp/reference/threadprivate.md)的使用範例`copyin`。  
  
## <a name="see-also"></a>請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)