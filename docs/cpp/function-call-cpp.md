---
title: "函式呼叫 (C++) | Microsoft Docs"
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
  - "函式呼叫運算子 ()"
  - "函式呼叫, C++ 函式"
  - "函式呼叫, operator"
  - "函式多載化, 函式呼叫運算子"
  - "函式 [C++], 呼叫"
  - "運算子多載, 範例"
  - "運算子多載, 函式呼叫"
  - "運算子 [C++], 多載"
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式呼叫 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用括號叫用的函式呼叫運算子是二元運算子。  
  
## 語法  
  
```  
  
primary-expression ( expression-list )  
```  
  
## 備註  
 在此內容中，`primary-expression` 是第一個運算元，而 `expression-list` \(可能空白的引數清單\) 是第二個運算元。  函式呼叫運算子用於需要一些參數的運算。  這不會有問題，因為 `expression-list` 是清單，而不是單一運算元。  函式呼叫運算子必須是非靜態成員函式。  
  
 函數呼叫運算子在多載時，不會修改呼叫函式的方式；而是會修改運算子在套用到特定類別類型的物件時如何解譯。  例如，下列程式碼通常會沒有意義：  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 但若是有適當多載的函式呼叫運算子，此語法可以用來將 `x` 座標偏移 3 個單位，`y` 座標偏移 2 個單位。  下列程式碼表示此定義：  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 請注意，函式呼叫運算子會套用到物件的名稱，而不是函式的名稱。  
  
 您也可以使用函式指標 \(而不是函式本身\) 來多載函式呼叫運算子。  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
  
```  
  
## 請參閱  
 [運算子多載](../cpp/operator-overloading.md)