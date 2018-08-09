---
title: 變數引數清單 （...）(C + + /CLI CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 054d91881d136564cdfb956f240789ca5a425ef2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642938"
---
# <a name="variable-argument-lists--ccli"></a>變數引數清單 (...) (C++/CLI)
此範例示範如何使用`...`Visual c + +，來實作具有可變數目的引數的函式的語法。  
  
> [!NOTE]
>  本主題適用於 C + + /cli CLI。 如需有關使用資訊`...`ISO 標準 c + +，請參閱[省略符號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md)省略符號和預設引數[後置運算式](../cpp/postfix-expressions.md)。  
  
 使用參數`...`必須是參數清單中的最後一個參數。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```cpp  
// mcppv2_paramarray.cpp  
// compile with: /clr  
using namespace System;  
double average( ... array<Int32>^ arr ) {  
   int i = arr->GetLength(0);  
   double answer = 0.0;  
  
   for (int j = 0 ; j < i ; j++)  
      answer += arr[j];  
  
   return answer / i;  
}  
  
int main() {  
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
3  
```  
  
## <a name="code-example"></a>程式碼範例  
 下列範例示範如何從 C# 呼叫接受可變數目的引數的 Visual c + + 函式。  
  
```cpp  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 此函式`f`可以從呼叫 C# 或 Visual Basic 中，比方說，就如同函式可接受可變數目的引數。  
  
 在 C# 中，引數傳遞至`ParamArray`可變數目的引數由呼叫參數。 下列程式碼範例是以 C#。  
  
```cs  
// mcppv2_paramarray3.cs  
// compile with: /r:mcppv2_paramarray2.dll  
// a C# program  
  
public class X {  
   public static void Main() {  
      // Visual C# will generate a String array to match the   
      // ParamArray attribute  
      C myc = new C();  
      myc.f("hello", "there", "world");  
   }  
}  
```  
  
 呼叫`f`Visual c + + 可以傳遞初始化的陣列或可變長度的陣列。  
  
```cpp  
// mcpp_paramarray4.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
  
int main() {  
   C ^ myc = gcnew C();  
   myc->f("hello", "world", "!!!");  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../windows/arrays-cpp-component-extensions.md)