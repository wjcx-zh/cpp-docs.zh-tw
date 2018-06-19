---
title: firstprivate |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b5a270feb638a98c060b58e90af8146ff97325
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691699"
---
# <a name="firstprivate"></a>firstprivate
指定每個執行緒都應該有自己的變數中，執行個體和具有變數的值，應該先初始化變數，因為它存在於平行建構之前。  
  
## <a name="syntax"></a>語法  
  
```  
firstprivate(var)  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`var`|具有執行個體中每個執行緒，變數會初始化變數的值，因為它存在於之前平行建構。 如果指定了多個變數，請以逗號分隔變數名稱。|  
  
## <a name="remarks"></a>備註  
  
## <a name="remarks"></a>備註  
 `firstprivate` 適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 如需詳細資訊，請參閱[2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。  
  
## <a name="example"></a>範例  
 如需使用`firstprivate`，請參閱中的範例[私人](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)