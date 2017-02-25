---
title: "編譯器警告 (層級 1) C4503 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4503"
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 裝飾名稱的長度超出範圍，名稱已截斷  
  
 裝飾名稱長於編譯器的限制 \(4096\)，而且已被截斷。  若要避免發生此警告與截斷，請減少引數個數或識別項名稱的長度。  
  
 發出這項警告的情況之一是：當您的程式碼中包含重複對樣板進行特製化的樣板時。例如，對應的對應 \(從 Standard C\+\+ 程式庫\)。在這種情況下，您可以讓 typedef 成為包含對應的型別 \(例如，struct\)。  
  
 但是，您可能會決定不要重組程式碼的結構。您是可以隨附產生 C4503 的應用程式交貨，但如果您在截斷的符號上接到連結時間錯誤，就會更難以決定錯誤中的符號型別。偵錯也將會更困難，偵錯工具也會很難對應符號名稱至型別名稱。不過程式的正確性不會因為截斷的名稱而受影響。  
  
 下列範例會產生 C4503：  
  
```  
// C4503.cpp  
// compile with: /W1 /EHsc /c  
// C4503 expected  
#include <string>  
#include <map>  
  
class Field{};  
  
typedef std::map<std::string, Field> Screen;  
typedef std::map<std::string, Screen> WebApp;  
typedef std::map<std::string, WebApp> WebAppTest;  
typedef std::map<std::string, WebAppTest> Hello;  
Hello MyWAT;  
```  
  
 下列範例將示範一種重寫程式碼的方式，可解決 C4503 的問題：  
  
```  
// C4503b.cpp  
// compile with: /W1 /EHsc /c  
#include <string>  
#include <map>  
  
class Field{};  
struct Screen2 {  
   std::map<std::string, Field> Element;  
};  
  
struct WebApp2 {  
   std::map<std::string, Screen2> Element;  
};  
  
struct WebAppTest2 {  
   std::map<std::string, WebApp2> Element;  
};  
  
struct Hello2 {  
   std::map<std::string, WebAppTest2> Element;  
};  
  
Hello2 MyWAT2;  
```