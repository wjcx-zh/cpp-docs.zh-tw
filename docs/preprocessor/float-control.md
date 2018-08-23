---
title: float_control |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540965"
---
# <a name="floatcontrol"></a>float_control
指定函式的浮點行為。  
  
## <a name="syntax"></a>語法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>旗標  
 
*值*，*設定* *[推送]*  
指定浮點行為。 *值*可以是`precise`或`except`。 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。 *設定*可以是`on`或`off`。  
  
如果*值*是`precise`，設定`precise`和`except`所指定。 `except` 只可以設定為`on`時`precise`也會設定為`on`。  
  
如果選擇性*推播*權杖新增，目前設定*值*推入至內部編譯器堆疊。  
  
*push*  
將目前的推送**float_control**設定至內部編譯器堆疊  
  
*pop*  
移除**float_control**設定從內部編譯器堆疊的頂端，並建立新**float_control**設定。  
  
## <a name="remarks"></a>備註  
 
當 `float_control precise` 開啟時，您便無法將 `except` 關閉。 同樣地，當 `precise` 開啟時，便無法關閉 `fenv_access`。 若要從 strict 模型移至 fast 模型與**float_control** pragma，請使用下列程式碼：  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
若要從 fast 模型移至 strict 模型**float_control** pragma，請使用下列程式碼：  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
其他浮點 pragma 包括：  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>範例  
 
下列範例示範如何使用 pragma 攔截溢位浮點例外狀況**float_control**。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
