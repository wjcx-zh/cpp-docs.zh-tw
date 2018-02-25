---
title: float_control | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1525b92b43a688cdec970c646613aa4474d44cc3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="floatcontrol"></a>float_control
指定函式的浮點行為。  
  
## <a name="syntax"></a>語法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>旗標  
 `value``setting` **[推送]**  
 指定浮點行為。 `value` 可以是**精確**或**除了**。 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。 `setting` 可以是**上**或**關閉**。  
  
 如果`value`是**精確**，設定**精確**和**除了**所指定。 **除了**只能設定為**上**時**精確**也會設為**上**。  
  
 如果選擇性**發送**語彙基元會加入，目前設定`value`推入至內部編譯器堆疊。  
  
 **push**  
 將目前的 `float_control` 設定推入至內部編譯器堆疊。  
  
 **pop**  
 移除`float_control`設定從內部編譯器堆疊的頂端，並使該項新`float_control`設定。  
  
## <a name="remarks"></a>備註  
 您無法開啟`float_control precise`關閉時**除了**上。 同樣地，**精確**無法關閉時`fenv_access`上。 若要使用 `float_control` pragma 從 strict 模型移至 fast 模型，請使用下列程式碼：  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
// The following line is needed on Itanium processors  
#pragma fp_contract(on)  
```  
  
 若要使用 `float_control` pragma 從 fast 模型移至 strict 模型，請使用下列程式碼：  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
// The following line is needed on Itanium processors.  
#pragma fp_contract(off)  
```  
  
 其他浮點 pragma 包括：  
  
-   [fenv_access](../preprocessor/fenv-access.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 pragma `float_control` 攔截溢位浮點例外狀況。  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)