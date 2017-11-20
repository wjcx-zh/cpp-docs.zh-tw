---
title: "copyin |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: copyin
dev_langs: C++
helpviewer_keywords: copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af833219039a03e7e403f7e3cd10210057f3abfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
 `copyin`適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## <a name="example"></a>範例  
 請參閱[threadprivate](../../../parallel/openmp/reference/threadprivate.md)的使用範例`copyin`。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)