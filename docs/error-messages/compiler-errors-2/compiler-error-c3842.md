---
title: "編譯器錯誤 C3842 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3842
dev_langs: C++
helpviewer_keywords: C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9fe94a50939af6d28f9dc29eb1eb7aa91a7d47c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3842"></a>編譯器錯誤 C3842
'function'：不支援 WinRT 或 Managed 類型的成員函式上的 'const' 和 'volatile' 限定詞  
  
 [const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md)不支援 Windows 執行階段或 managed 的類型的成員函式。  
  
 下列範例會產生 C3842：  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
```