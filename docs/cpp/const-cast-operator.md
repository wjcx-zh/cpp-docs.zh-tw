---
title: "const_cast 運算子 | Microsoft Docs"
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
  - "const_cast"
  - "const_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_cast 關鍵字 [C++]"
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const_cast 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從類別移除 **const**、`volatile` 和 **\_\_unaligned** 屬性。  
  
## 語法  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## 備註  
 除了 **const**、`volatile` 和 **\_\_unaligned** 限定詞之外，任何物件類型的指標或資料成員的指標都可以明確地轉換為相同的類型。  對於指標和參考，其結果會參考原始物件。  對於資料成員的指標，則結果會參考與資料成員的原始 \(未轉型\) 指標相同的成員。  根據所參考物件的類型，透過產生的指標、參考或資料成員的指標進行寫入作業，可能會產生未定義的行為。  
  
 您不能使用 `const_cast` 運算子直接覆寫常數變數的常數狀態。  
  
 `const_cast` 運算子會將 null 指標值轉換為目的類型的 null 指標值。  
  
## 範例  
  
```  
// expre_const_cast_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CCTest {  
public:  
   void setNumber( int );  
   void printNumber() const;  
private:  
   int number;  
};  
  
void CCTest::setNumber( int num ) { number = num; }  
  
void CCTest::printNumber() const {  
   cout << "\nBefore: " << number;  
   const_cast< CCTest * >( this )->number--;  
   cout << "\nAfter: " << number;  
}  
  
int main() {  
   CCTest X;  
   X.setNumber( 8 );  
   X.printNumber();  
}  
```  
  
 在包含 `const_cast` 的程式碼行上，`this` 指標的資料類型為 `const CCTest *`。  `const_cast` 運算子會將 `this` 指標的資料類型變更為 `CCTest *`，允許修改成員 `number`。  轉換只會在其出現之陳述式的其餘部分中持續進行。  
  
## 請參閱  
 [轉型運算子](../cpp/casting-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)