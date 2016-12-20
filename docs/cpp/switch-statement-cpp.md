---
title: "switch 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "default"
  - "default_cpp"
  - "switch"
  - "switch_cpp"
  - "case"
  - "case_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case 關鍵字 [C++], 在 switch 陳述式中"
  - "default 關鍵字 [C++]"
  - "switch 關鍵字 [C++]"
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# switch 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據整數運算式的值，允許在多個程式碼區段中選取範圍。  
  
## 語法  
  
```  
  
      switch ( expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## 備註  
 *expression* 必須是整數類資料類型或類別類型，這會有對整數類型的模稜兩可轉換。  已依[整數提升](../misc/integral-promotions.md)中所述執行整數提升。  
  
 `switch` 陳述式主體包含一連串 **case** 標籤和選擇性的 **default** 標籤。  在 **case** 陳述式中，沒有任何兩個常數運算式可以評估為相同的值。  **default** 標籤只能出現一次。  有標記的陳述式不是語法需求，但是 `switch` 陳述式沒有它們就沒有意義。default 陳述式不需要出現在結尾，可以出現在 switch 陳述式主體中的任何位置。  case 或 default 標籤只能出現在 switch 陳述式內。  
  
 每個 **case** 標籤中的 *constant\-expression* 會轉換為 *expression* 的類型，並與 *expression* 進行相等比較。  控制權會傳遞給 **case** *constant\-expression* 比對 *expression* 的值的陳述式。  產生的行為如下表所示。  
  
### switch 陳述式行為  
  
|條件|動作|  
|--------|--------|  
|轉換的值與升級之控制運算式的值相符。|控制權會轉移至標籤後面的陳述式。|  
|沒有常數符合 **case** 標籤中的常數；有 **default** 標籤存在。|控制權會轉移到 **default** 標籤。|  
|沒有任何常數符合 **case** 標籤中的常數，且不存在**default** 標籤。|控制權會轉移至 `switch` 陳述式之後的陳述式。|  
  
 如果找到相符運算式，則控制權不會受到後續 **case** 和 **default** 標籤妨礙。  [break](../cpp/break-statement-cpp.md) 陳述式是用來停止執行，並將控制權轉移至 `switch` 陳述式之後的陳述式。  沒有 **break** 陳述式，就會從相符的 **case** 標籤執行至 `switch` 結尾 \(包括 **default**\) 的所有陳述式。  例如：  
  
```  
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 在上述範例中，如果 `c` 是大寫 `A`，則遞增 `capa`。  在 `capa++` 之後的 `break` 陳述式會結束 `switch` 陳述式主體的執行，並將控制權傳遞給 `while` 迴圈。  沒有 `break` 陳述式，`lettera` 和 `nota` 也會遞增。  `case 'a'` 的 `break` 陳述式也提供類似的用途。  如果 `c` 是小寫 `a`，`lettera` 會遞增，而 `break` 陳述式會結束 `switch` 陳述式主體。  如果 `c` 不是 `a` 或 `A`，就會執行 `default` 陳述式。  
  
 只要初始化是可執行到的，也就是所有可能的執行路徑都不略過，`switch` 陳述式的內部區塊可以包含有初始化的定義。  使用這些宣告引入的名稱有區域範圍。  例如：  
  
```  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 `switch` 陳述式可以是巢狀結構。  在這種情況下，**case** 或 **default** 標籤會與含括它們的最接近 `switch` 陳述式產生關聯。  
  
## Microsoft 特定的  
 Microsoft C 不會限制 `switch` 陳述式中 case 值的數目。  此數目會受到可用記憶體的限制。  ANSI C 要求在 `switch` 陳述式中允許至少 257 個 case 標籤。  
  
 Microsoft C 預設會啟用 Microsoft 擴充功能。  使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) 編譯器選項可停用這些擴充功能。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) Using Labels in the case Statement](http://msdn.microsoft.com/zh-tw/a6ff057d-1aee-42ed-a28d-ee6a565b3197)