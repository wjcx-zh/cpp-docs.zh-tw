---
title: omp_get_wtime | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_wtime
dev_langs:
- C++
helpviewer_keywords:
- omp_get_wtime OpenMP function
ms.assetid: c8dee105-ec1b-42e5-a6e3-edeedcf9854c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57307df6a2e13c6bd3dbd90892669119f8526d70
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetwtime"></a>omp_get_wtime
傳回從某個時間點所經過時間的秒鐘值。  
  
## <a name="syntax"></a>語法  
  
```  
double omp_get_wtime( );  
```  
  
## <a name="return-value"></a>傳回值  
 傳回一些任意的但一致的點之間所經歷的時間 （秒） 中的值。  
  
## <a name="remarks"></a>備註  
 該點程式執行，因此後續比較可能會維持一致。  
  
 如需詳細資訊，請參閱[3.3.1 omp_get_wtime 函式](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_get_wtime.cpp  
// compile with: /openmp  
#include "omp.h"  
#include <stdio.h>  
#include <windows.h>  
  
int main() {  
    double start = omp_get_wtime( );  
    Sleep(1000);  
    double end = omp_get_wtime( );  
    double wtick = omp_get_wtick( );  
  
    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",  
             start, end, end - start);  
  
    printf_s("wtick = %.16g\n1/wtick = %.16g\n",  
             wtick, 1.0 / wtick);  
}  
```  
  
```Output  
start = 594255.3671159324  
end = 594256.3664474116  
diff = 0.9993314791936427  
wtick = 2.793651148400146e-007  
1/wtick = 3579545  
```  
  
## <a name="see-also"></a>請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)