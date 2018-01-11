---
title: "firstprivate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: firstprivate
dev_langs: C++
helpviewer_keywords: firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c7d4a5ba23e343f7858bf3320ed05ebce84f1c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 `firstprivate`適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 如需詳細資訊，請參閱[2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。  
  
## <a name="example"></a>範例  
 如需使用`firstprivate`，請參閱中的範例[私人](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)