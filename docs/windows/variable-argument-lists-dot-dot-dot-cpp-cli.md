---
title: "Variable Argument Lists (...) (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variable argument lists"
  - "parameter arrays"
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Variable Argument Lists (...) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何在 Visual C\+\+ 中使用 `...` 語法來實作引數數目可變的函式。  
  
> [!NOTE]
>  這個主題有關於 C\+\+\/CLI。  如需有關在 ISO Standard C\+\+ 中使用 `...` 的詳細資訊，請參閱 [省略符號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md) 和 [省略符號和預設引數](../misc/ellipses-and-default-arguments.md)。  
  
 使用 `...` 的參數必須是參數清單中的最後一個參數。  
  
## 範例  
  
### 程式碼  
  
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
  
### Output  
  
```  
3  
```  
  
## 程式碼範例  
 下列範例示範如何從 C\# 呼叫接受可變數目之引數的 Visual C\+\+ 函式。  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 例如，可以從 C\# 或 Visual Basic 呼叫 `f` 函式，就好像是可以接受可變數目之引數的函式。  
  
 在 C\# 中，傳遞至 `ParamArray` 參數的引數可以由可變數目的引數呼叫。  下列程式碼範例使用 C\#。  
  
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
  
 在 Visual C\+\+ 中對 `f` 的呼叫可以傳遞初始化的陣列或可變長度的陣列。  
  
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
  
## 請參閱  
 [Arrays](../windows/arrays-cpp-component-extensions.md)