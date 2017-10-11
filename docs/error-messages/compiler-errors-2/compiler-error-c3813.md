---
title: "編譯器錯誤 C3813 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cabe753691b3d72ede25f0c25404d73fb63ceba8
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3813"></a>編譯器錯誤 C3813
屬性宣告只可以出現於 managed 或 WinRT 類型的定義中  
  
A[屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能宣告在 managed 或 Windows 執行階段類型。 原生類型不支援 `property` 關鍵字。  
  
## <a name="example"></a>範例  
下列範例會產生 C3813，並說明如何加以修正：  
  
```cpp  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```
