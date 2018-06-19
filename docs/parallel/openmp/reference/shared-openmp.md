---
title: 共用 (OpenMP) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8287f96f80748272e29b22ed5c43c364f4353b86
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691673"
---
# <a name="shared-openmp"></a>shared (OpenMP)
指定一個或多個變數，應該所有執行緒之間共用。  
  
## <a name="syntax"></a>語法  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `var`  
 共用一個以上的變數。 如果指定了多個變數，請以逗號分隔變數名稱。  
  
## <a name="remarks"></a>備註  
 共用變數在執行緒之間的另一個方法是使用[copyprivate](../../../parallel/openmp/reference/copyprivate.md)子句。  
  
 `shared` 適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.4 共用](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## <a name="example"></a>範例  
 請參閱[私人](../../../parallel/openmp/reference/private-openmp.md)的使用範例`shared`。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)