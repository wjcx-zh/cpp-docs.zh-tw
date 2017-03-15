---
title: "函式內嵌問題 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob1 C++ 編譯器選項"
  - "/Ob2 C++ 編譯器選項"
  - "函式內嵌問題"
  - "內嵌函式, 問題"
  - "-Ob1 C++ 編譯器選項"
  - "-Ob2 C++ 編譯器選項"
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 函式內嵌問題
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您正在使用函式內嵌，您必須：  
  
-   在您包含的標頭檔中實作該內嵌 \(Inline\) 函式。  
  
-   在標頭檔中開啟 \(ON\) 內嵌。  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 然後，  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 如果您使用 `#pragma inline_depth` 編譯器指示詞，請確定您的設定值是 2 或更大的值。  數值為零時會關閉內嵌。  同時也請確定您使用的是 **\/Ob1** 或 **\/Ob2** 編譯器選項。  
  
 在不同模組中混合內嵌與非內嵌編譯選項有時候會發生問題。  如果 C\+\+ 程式庫是在函式內嵌開啟時 \([\/Ob1](../../build/reference/ob-inline-function-expansion.md) 或 [\/Ob2](../../build/reference/ob-inline-function-expansion.md)\) 所建立，但描述該函式的對應標頭檔已關閉內嵌 \(沒有選項\)，就會發生 LNK2001錯誤。  該函式不會由標頭檔內嵌至程式碼中，又因為它們並不存在於程式庫，因此沒有位址可以解析該參考。  
  
 同樣地，如果一個專案使用了函式內嵌，但是卻在 .cpp 檔 \(而不是在標頭檔\) 定義該函式，也會發生 LNK2019 錯誤。  任何適當的地方都可以包含標頭檔，但是該函式只會在 .cpp 檔傳至該編譯器時才會進行內嵌；因此在連結器被其他模組使用時，它會將函式視為無法在外部之程式庫中找到或連結所需之資料型別或函式。  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 然後，  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 然後，  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## 請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)