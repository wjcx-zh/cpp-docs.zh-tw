---
title: "lastprivate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7945edb879d81bb50753619c1206b9da575dbcda
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## <a name="example"></a>範例  
 請參閱[排程](../../../parallel/openmp/reference/schedule.md)的使用範例`lastprivate`子句。  
  
## <a name="see-also"></a>請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)