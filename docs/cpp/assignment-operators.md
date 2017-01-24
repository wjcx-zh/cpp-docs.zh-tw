---
title: "指派運算子 | Microsoft Docs"
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
  - ">>="
  - "xor_eq"
  - "&="
  - "<<="
  - "-="
  - "and_eq"
  - "^="
  - "|="
  - "/="
  - "%="
  - "or_eq"
  - "+="
  - "*="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%= 運算子"
  - "&= 運算子"
  - "*= 運算子"
  - "/= 運算子"
  - "^= 運算子"
  - "|= 運算子"
  - "+= 運算子"
  - "<<= 運算子"
  - "= 運算子"
  - "-= 運算子"
  - ">>= 運算子"
  - "and_eq 運算子"
  - "指派運算子"
  - "指派運算子, C++"
  - "運算子 >>="
  - "運算子>>="
  - "運算子 [C++], 設定"
  - "or_eq 運算子"
  - "xor_eq 運算子"
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指派運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
        expression assignment-operator expression   
assignment-operator : one of  
   =   *=   /=   %=   +=   –=   <<=   >>=   &=   ^=   |=  
```  
  
## 備註  
 指派運算子會將值儲存在左運算元所指定的物件。  有兩種指派運算：簡單指派，第二個運算元的值儲存在第一個運算元所指定的物件；複合指派，在儲存結果之前執行算術、移位或位元運算。  下表中除了 \= 運算子以外的所有指派運算子都是複合指派運算子。  
  
### 指派運算子  
  
|運算子|意義|  
|---------|--------|  
|**\=**|將第二個運算元的值儲存在第一個運算元所指定的物件 \(簡單指派\)。|  
|**\*\=**|將第一個運算元的值乘以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|  
|`/=`|將第一個運算元的值除以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|  
|`%=`|將第一個運算元以第二個運算元的值取模數；將結果儲存在第一個運算元所指定的物件。|  
|`+=`|將第二個運算元的值加至第一個運算元的值；將結果儲存在第一個運算元所指定的物件。|  
|**–\=**|將第一個運算元的值減去第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|  
|**\<\<\=**|將第一個運算元的值往左移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。|  
|**\>\>\=**|將第一個運算元的值往右移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。|  
|**&\=**|取得第一和第二個運算元的位元 AND；將結果儲存在第一個運算元所指定的物件。|  
|`^=`|取得第一和第二個運算元的位元排除 OR；將結果儲存在第一個運算元所指定的物件。|  
|`&#124;=`|取得第一和第二個運算元的位元包含 OR；將結果儲存在第一個運算元所指定的物件。|  
  
 **運算子關鍵字**  
  
 三個複合指派運算子有文字對等用法。  包括：  
  
|運算子|對等項目|  
|---------|----------|  
|**&\=**|`and_eq`|  
|`&#124;=`|`or_eq`|  
|`^=`|`xor_eq`|  
  
 有兩種方式可存取您程式中的這些運算子關鍵字：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Assignment_Operators.cpp  
// compile with: /EHsc  
// Demonstrate assignment operators  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;  
  
   a += b;      // a is 9  
   b %= a;      // b is 6  
   c >>= 1;      // c is 5  
   d |= e;      // Bitwise--d is 0xFFFF   
  
   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl  
         << "a += b yields " << a << endl  
         << "b %= a yields " << b << endl  
         << "c >>= 1 yields " << c << endl  
         << "d |= e yields " << hex << d << endl;  
}  
```  
  
## 單一指派  
 簡單指派運算子 \(\=\) 會使第二個運算元的值儲存在第一個運算元指定的物件中。  如果兩個物件都是算術類型，右運算元會在儲存值之前轉換成左運算元的類型。  
  
 可以將 const 和 volatile 類型的物件指派給只屬於 volatile 類型的左值，或者是不是 const 和 volatile 類型的左值。  
  
 類別類型 \(結構、等位和類別類型\) 之物件的指派作業是由名為 operator\= 的函式執行。  這個運算子函式的預設行為是執行位元複製；不過可以使用多載運算子修改此行為   \(如需詳細資訊，請參閱[多載運算子](../cpp/operator-overloading.md)\)。  
  
 只要物件是從指定基底類別明確衍生的任何類別，就可以指派給該基底類別的物件。  反向則不成立，因為可從衍生類別隱含轉換為基底類別，但無法從基底類別轉換為衍生類別。  例如:  
  
```  
// expre_SimpleAssignment.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
class ABase  
{  
public:  
    ABase() { cout << "constructing ABase\n"; }  
};  
  
class ADerived : public ABase  
{  
public:  
    ADerived() { cout << "constructing ADerived\n"; }  
};  
  
int main()  
{  
    ABase aBase;  
    ADerived aDerived;  
  
    aBase = aDerived; // OK  
    aDerived = aBase; // C2679  
}  
```  
  
 參考類別的指派作用就像指派參考所指向的物件。  
  
 對於類別類型的物件而言，指派與初始化不同。  為說明指派與初始化的不同之處，假設下列程式碼  
  
```  
UserType1 A;  
UserType2 B = A;  
```  
  
 上述程式碼示範初始化設定式；它會呼叫建構函式 `UserType2`，此建構函式接受屬於類型 `UserType1` 的引數。  假設下列程式碼  
  
```  
UserType1 A;  
UserType2 B;  
  
B = A;  
```  
  
 指派陳述式  
  
```  
B = A;   
```  
  
 可能會有下列其中一項作用：  
  
-   呼叫 `UserType2` 的函式 operator\=，前提是必須提供 `UserType1` 引數給 operator\=。  
  
-   如果 `UserType1::operator UserType2` 函式存在，呼叫這類明確轉換函式。  
  
-   呼叫建構函式 `UserType2::UserType2`，前提是這類建構函式存在，而且接受 `UserType1` 引數並複製結果。  
  
## 複合指派  
 [指派運算子](../cpp/assignment-operators.md)的表中顯示的複合指派運算子是以 *e1* `op`\= *e2* 的形式指定，其中 *e1* 是不屬於 const 類型的可修改左值，而 *e2* 是下列其中一項：  
  
-   算術類型  
  
-   指標 \(如果 `op` 為 \+ 或 –\)  
  
 *e1* `op`\= *e2* 形式的行為就像 *e1* *\= e1* `op` *e2*，不過 *e1* 只會評估一次。  
  
 對列舉類型的複合指派會產生錯誤訊息。  如果左運算元為指標類型，則右運算元必須是指標類型，或者必須是判斷值為 0 的常數運算式。  如果左運算元為整數類資料類型，則右運算元不能是指標類型。  
  
## 指派運算子的結果  
 指派運算子會在指派之後傳回左運算元所指定的物件值。  結果的類型會是左運算元的類型。  指派運算式的結果一律是左值。  這些運算子具有由右到左的順序關聯性。  左運算元必須是可修改的左值。  
  
 在 ANSI C 中，指派運算式的結果不是左值。  因此，合法的 C\+\+ 運算式 `(a += b) += c` 在 C 中是不合法的。  
  
## 請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 指派運算子](../c-language/c-assignment-operators.md)