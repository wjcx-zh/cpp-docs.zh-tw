---
title: "編譯器錯誤 C3271 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3271
dev_langs:
- C++
helpviewer_keywords:
- C3271
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a102429fba0c001d0169e4e96003f86be05f4405
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3271"></a>編譯器錯誤 C3271
'member': 對 FieldOffset 屬性無效的值 'value'  
  
 已傳遞負值給 **FieldOffset** 屬性。  
  
 下列範例會產生 C3271：  
  
```  
// C3271.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Explicit)]  
value class MyStruct1 {  
   public: [FieldOffset(0)] int a;  
   public: [FieldOffset(-1)] long b;   // C3271  
};  
```  
