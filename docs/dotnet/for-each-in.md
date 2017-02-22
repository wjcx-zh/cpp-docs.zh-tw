---
title: "for each、in | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::foreach"
  - "for"
  - "each"
  - "in"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for each 關鍵字 [C++]"
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# for each、in
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

逐一查看陣列或集合。  此非標準關鍵字在 C\+\+\/CLI 和原生 C\+\+ 專案中皆可用。  但是，不建議使用。  請考慮改用標準 [以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)。  
  
## 所有執行階段  
 **語法**  
  
```  
  
        for each (type identifier in expression) {  
   statements  
}  
  
```  
  
 **參數**  
  
 `type`  
 `identifier` 的類型。  
  
 `identifier`  
 表示集合項目的反覆項目變數。當 `identifier` 是 [Tracking Reference Operator](../windows/tracking-reference-operator-cpp-component-extensions.md) 時，您可以修改項目。  
  
 `expression`  
 陣列運算式或集合。  集合項目必須如此，編譯器才能將其轉換為 `identifier` 類型。  
  
 `statements`  
 要執行的一個或多個陳述式。  
  
 **備註**  
  
 `for each` 陳述式可用來逐一查看集合。  您可以修改集合中的項目，不過，您無法加入或刪除項目。  
  
 針對陣列或集合中的每個項目執行 *statements*。  在完成集合中所有項目的反覆項目之後，程式控制權會轉移到 `for each` 區塊之後的下一個陳述式。  
  
 `for each` 和 `in` 是[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 如需詳細資訊：  
  
-   [使用 for each 反覆查看 STL 集合](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [如何：使用 for each 反覆查看陣列](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [如何：使用 for each 反覆查看泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [如何：使用 for each 反覆查看使用者定義的集合](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 需求  
 編譯器選項：**\/ZW**  
  
### 範例  
 本範例示範如何使用 `for each` 逐一查看字串。  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **Output**  
  
  **abcd**  
 **測試**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 CLR 語法與 **All Runtimes** 語法相同，但不同之處如下。  
  
 *expression*  
 Managed 陣列運算式或集合。  集合項目必須如此，編譯器才能將其從 <xref:System.Object> 轉換為 *identifier* 類型。  
  
 *expression* 會針對實作 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601> 的類型，或定義 `GetEnumerator` 方法的類型 \(該方法會傳回實作 <xref:System.Collections.IEnumerator> 或宣告 `IEnumerator` 中定義之所有方法的類型\) 進行評估。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 本範例示範如何使用 `for each` 逐一查看字串。  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **Output**  
  
  **abcd**  
 **測試**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)