---
title: "共用 (OpenMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90491e6e8b415c79e21b4fa518f7e60327ac823e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.4 共用](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## <a name="example"></a>範例  
 請參閱[私人](../../../parallel/openmp/reference/private-openmp.md)的使用範例`shared`。  
  
## <a name="see-also"></a>請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)