---
title: 編譯器錯誤 C3813 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e947b281c90c4d2ace83971f1de972c29bde72ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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