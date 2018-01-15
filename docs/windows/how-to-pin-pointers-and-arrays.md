---
title: "如何： 固定指標和陣列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68824b9fcdf2f4de47900d5b0c4b03db9e28d9fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-pin-pointers-and-arrays"></a>如何：固定指標和陣列
對 Managed 物件中定義的子物件執行 Pin 動作，與對整個物件執行 Pin 動作具有相同的效果。  例如，如果對陣列中的任何元素執行 Pin 動作，則整體陣列都會受到 Pin 動作影響。 語言並未提供任何擴充功能可用來宣告 Pin 陣列。 若要對陣列執行 Pin，請對其元素類型宣告 Pin 指標，然後對其中一個元素執行 Pin 動作。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
++  
```  
  
## <a name="see-also"></a>請參閱  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)