---
title: OMP_SCHEDULE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5052aaadc673e38a844ea5b0d1e11ff3a96f3fbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="ompschedule"></a>OMP_SCHEDULE
可修改[排程](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。  
  
## <a name="syntax"></a>語法  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `size` (選擇性)  
 指定反覆項目的大小。 `size` 必須是正整數。 預設值為 1，除非`type`是靜態的。 不正確時`type`是`runtime`。  
  
 `type`  
 排程的類型：  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>備註  
 OpenMP 標準的 Visual c + + 實作中的預設值是`OMP_SCHEDULE=static,0`。  
  
 如需詳細資訊，請參閱[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。  
  
## <a name="example"></a>範例  
 下列命令**OMP_SCHEDULE**環境變數：  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 下列命令會顯示目前的設定**OMP_SCHEDULE**環境變數：  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>另請參閱  
 [環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)