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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f8af13ffdcd71d760a180340a79a863cecb5e32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4503"></a>編譯器警告 (層級 1) C4503
'identifier': 裝飾名稱長度超出範圍，名稱已遭截斷  
  
 裝飾的名稱長度超過編譯器限制 (4096)，而且已被截斷。 若要避免這個警告，而且截斷，減少的引數或使用的識別項名稱長度。  
  
 會發出這個警告的其中一種情況時，您的程式碼包含樣板特製化的範本上重複。  例如，對應 （從 c + + 標準程式庫） 的對應。  在此情況下，您可以讓您的 typedef 包含對應的型別 （例如結構）。  
  
 不過，您可能會決定不重建您的程式碼。  很可能會產生 C4503 的應用程式，但如果您在截斷的符號連結時間時發生錯誤，它將會更難判斷錯誤的符號類型。  偵錯也會比較困難;偵錯工具也會有困難對應符號名稱，輸入名稱。  正確性的程式，不過，不會受到截斷的名稱。  
  
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
  
 下列範例會示範一種方法重新撰寫程式碼，若要解決 C4503:  
  
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