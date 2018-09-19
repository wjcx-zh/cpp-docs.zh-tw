---
title: copyin |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27afaee16a87ddf428570f7854212eed34634d38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059325"
---
# <a name="copyin"></a>copyin
可讓執行緒存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。  
  
## <a name="syntax"></a>語法  
  
```  
copyin(var)  
```  
  
## <a name="parameters"></a>參數
  
*var*<br/>
`threadprivate`存在於平行建構之前將在主執行緒中，變數的值初始化的變數。  
  
## <a name="remarks"></a>備註  
 `copyin` 適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 < [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## <a name="example"></a>範例  
 請參閱[threadprivate](../../../parallel/openmp/reference/threadprivate.md)如需使用的範例`copyin`。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)