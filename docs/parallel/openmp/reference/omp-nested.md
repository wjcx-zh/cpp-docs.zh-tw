---
title: "OMP_NESTED |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NESTED
dev_langs: C++
helpviewer_keywords: OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d90d43727227593cccbd3d885f71f5cabaf10429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ompnested"></a>OMP_NESTED
指定是否巢狀平行處理原則已啟用，除非啟用或停用巢狀平行處理原則`omp_set_nested`。  
  
## <a name="syntax"></a>語法  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>備註  
 `OMP_NESTED`環境變數可以覆寫[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)函式。  
  
 OpenMP 標準的 Visual c + + 實作中的預設值是`OMP_DYNAMIC=FALSE`。  
  
 如需詳細資訊，請參閱[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。  
  
## <a name="example"></a>範例  
 下列命令`OMP_NESTED`環境變數設為 TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 下列命令會顯示目前的設定`OMP_NESTED`環境變數：  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>請參閱  
 [環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)