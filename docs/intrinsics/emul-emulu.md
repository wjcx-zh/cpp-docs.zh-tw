---
title: "__emul、 __emulu |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
dev_langs:
- C++
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba97b1160b9b0bff9e6014d73d1c79bf4627139c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="emul-emulu"></a>__emul、__emulu
**Microsoft 特定的**  
  
 會執行乘法可以保存的 32 位元整數的溢位。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 __emul(  
   int a,  
   int b  
);  
unsigned __int64 __emulu(  
   unsigned int a,  
   unsigned int b  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `a`  
 相乘的第一個整數運算元。  
  
 [輸入] `b`  
 相乘的第二個整數運算元。  
  
## <a name="return-value"></a>傳回值  
 相乘的結果。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__emul`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__emulu`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `__emul` 會採用兩個 32 位元帶正負號的值，並傳回做為 64 位元帶正負號的整數值相乘的結果。  
  
 `__emulu` 會採用兩個 32 位元不帶正負號的整數值，並傳回做為 64 位元不帶正負號的整數值相乘的結果。  
  
## <a name="example"></a>範例  
  
```  
// emul.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__emul)  
#pragma intrinsic(__emulu)  
  
int main()  
{  
   int a = -268435456;   
   int b = 2;   
  
   __int64 result = __emul(a, b);  
  
   cout << a << " * " << b << " = " << result << endl;  
  
   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295  
   unsigned int ub = 0xF000000;  // Dec value: 251658240  
  
   unsigned __int64 uresult = __emulu(ua, ub);  
  
   cout << ua << " * " << ub << " = " << uresult << endl;  
  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
-268435456 * 2 = -536870912  
4294967295 * 251658240 = 1080863910317260800  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)