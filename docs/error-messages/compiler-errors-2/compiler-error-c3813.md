---
title: "編譯器錯誤 C3813 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 74c976fb090533ade91e5debf067371d5d3295c1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3813"></a>編譯器錯誤 C3813
屬性宣告只可以出現於 managed 或 WinRT 類型的定義中  
  
A[屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能在受管理或 Windows 執行階段中宣告型別。 原生類型不支援 `property` 關鍵字。  
  
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
