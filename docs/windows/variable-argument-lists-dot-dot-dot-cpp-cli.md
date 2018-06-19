---
title: 變數引數清單 （...）(C + + /CLI) |Microsoft 文件
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
ms.openlocfilehash: eec0e3591da2417137fda3bae4ed9e7860472fb2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889819"
---
# <a name="variable-argument-lists--ccli"></a>變數引數清單 (...) (C++/CLI)
此範例示範如何使用`...`實作具有可變數目的引數的函式的 Visual c + + 語法。  
  
> [!NOTE]
>  本主題適用於 C + + /CLI。 如需使用`...`ISO 標準 c + +，請參閱[省略符號和 Variadic 樣板](../cpp/ellipses-and-variadic-templates.md)省略符號和預設引數中[後置運算式](../cpp/postfix-expressions.md)。  
  
 使用參數`...`必須是參數清單中的最後一個參數。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
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
 下列範例會示範如何從 C# 呼叫接受可變數目的引數的 Visual c + + 函式。  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 此函式`f`可以從呼叫 C# 或 Visual Basic 中，比方說，就好像是可以接受可變數目的引數的函式。  
  
 在 C# 中的引數，傳遞至`ParamArray`可變數目的引數由呼叫參數。 下列程式碼範例是以 C#。  
  
```  
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
  
 呼叫`f`Visual c + + 可以傳遞初始化的陣列或可變長度陣列。  
  
```  
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