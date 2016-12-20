---
title: "明確類型轉換運算子：() | Microsoft Docs"
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
  - "轉換 [C++], explicit"
  - "資料類型轉換 [C++], explicit"
  - "明確資料類型轉換運算子"
  - "運算子 [C++], 明確類型轉換"
  - "類型轉換 [C++], 明確轉換"
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 明確類型轉換運算子：()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 允許使用類似函式呼叫的語法進行明確的類型轉換。  
  
## 語法  
  
```  
  
simple-type-name ( expression-list )  
```  
  
## 備註  
 *simple\-type\-name* 後方加上以括號括住的 *expression\-list*，可使用指定的運算式建構指定類型的物件。  下列範例顯示將類型明確地轉換為類型 int：  
  
```  
int i = int( d );  
```  
  
 下列範例會使用在[函式呼叫結果](../misc/function-call-results.md)中定義之 `Point` 類別的修改版本。  
  
## 範例  
  
```  
// expre_Explicit_Type_Conversion_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
public:  
    // Define default constructor.  
    Point() { _x = _y = 0; }  
    // Define another constructor.  
    Point( int X, int Y ) { _x = X; _y = Y; }  
  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
    void Show()   { cout << "x = " << _x << ", "  
                         << "y = " << _y << "\n"; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
int main()  
{  
    Point Point1, Point2;  
  
    // Assign Point1 the explicit conversion  
    //  of ( 10, 10 ).  
    Point1 = Point( 10, 10 );  
  
    // Use x() as an l-value by assigning an explicit  
    //  conversion of 20 to type unsigned.  
    Point1.x() = unsigned( 20 );  
    Point1.Show();  
  
    // Assign Point2 the default Point object.  
    Point2 = Point();  
    Point2.Show();  
}  
```  
  
## 輸出  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 雖然上述範例示範的是使用常數進行明確類型轉換，相同的技巧也可以在物件上進行這些轉換。  下列程式碼片段示範這項功能：  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 使用「轉換」語法也可以指定明確類型轉換。  上述範例若是使用轉換語法重新撰寫則會如下所示：  
  
```  
d = (float)i;  
```  
  
 從單一值進行轉換時，轉換和函式樣式轉換的結果相同。  不過，在函式樣式語法中，您可以在轉換時指定一個以上的引數。  這項差異對於使用者定義的類型而言是很重要的。  請考慮 `Point` 類別及其轉換：  
  
```  
struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  
```  
  
 上述範例 \(使用函式樣式轉換\) 顯示如何將兩個值 \(其中一個為 *x*，另一個為 *y*\) 轉換為使用者定義類型 `Point`。  
  
> [!CAUTION]
>  由於其中覆寫了 C\+\+ 編譯器的內建類型檢查，因此請小心使用明確類型轉換。  
  
 沒有 *simple\-type\-name* \(例如，指標或參考類型\) 的類型轉換必須使用[轉換](../cpp/cast-operator-parens.md)標記法進行。  使用 *simple\-type\-name* 表示轉換類型可以撰寫為下列任一種形式。  如需構成 *simple\-type\-name* 的詳細資訊，請參閱[類型指定名稱](http://msdn.microsoft.com/zh-tw/34b6c737-0ef1-4470-9b77-b26e46c0bbd4)。  
  
 在轉換中定義類型是不合法。  
  
## 請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)