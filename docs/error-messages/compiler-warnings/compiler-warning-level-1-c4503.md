---
title: "編譯器警告 （層級 1） C4503 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: f999fcb73860bfd2fabb3484e78f313a32240dee
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4503"></a>編譯器警告 (層級 1) C4503
'identifier': 裝飾名稱長度超出範圍，名稱被截斷  
  
 裝飾的名稱長於編譯器的限制 (4096)，而且已被截斷。 若要避免這個警告，而且截斷，減少的引數或使用的識別項名稱長度。  
  
 一種情況下將會發出這個警告時，您的程式碼包含樣板的特製化樣板重複。  例如，對應 （從 c + + 標準程式庫） 的對應。  在此情況下，您可以讓您的 typedef 包含對應的型別 （例如結構）。  
  
 不過，您可能決定不重建您的程式碼。  很可能會產生 C4503 的應用程式，但是如果您在截斷的符號連結時間時發生錯誤，它會更難判斷錯誤中符號的類型。  偵錯也會比較困難。偵錯工具也會有困難對應的符號名稱，輸入名稱。  正確性的程式，不過，不會受到截斷的名稱。  
  
 下列範例會產生 C4503:  
  
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
  
 下列範例會示範一種方式重寫程式碼來解決 C4503:  
  
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
