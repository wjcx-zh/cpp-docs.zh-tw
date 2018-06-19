---
title: lastprivate |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696223"
---
# <a name="lastprivate"></a>lastprivate
指定變數的版本，封入內容設定等於私用版本的任何執行緒執行的最後一個反覆項目 （如迴圈建構） 或最後一節 （#pragma 區段）。  
  
## <a name="syntax"></a>語法  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `var`  
 此變數會設為等於執行緒私用版本執行的最後一個反覆項目 （如迴圈建構） 或最後一節 （#pragma 區段）。  
  
## <a name="remarks"></a>備註  
 `lastprivate` 適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## <a name="example"></a>範例  
 請參閱[排程](../../../parallel/openmp/reference/schedule.md)的使用範例`lastprivate`子句。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)