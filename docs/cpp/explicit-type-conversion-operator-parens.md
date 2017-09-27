---
title: "明確類型轉換運算子: （) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 09afbed7f5a399b9ca192ff57be1c866baf59626
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="explicit-type-conversion-operator-"></a>明確類型轉換運算子：()
C++ 允許使用類似函式呼叫的語法進行明確的類型轉換。  
  
## <a name="syntax"></a>語法  
  
```  
simple-type-name ( expression-list )  
```  
  
## <a name="remarks"></a>備註  
 A*簡單類型名稱*後面*運算式清單*括在括號建構使用指定的運算式所指定型別的物件。 下列範例顯示將類型明確地轉換為類型 int：  
  
```  
int i = int( d );  
```  
  
 下列範例所示`Point`類別。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="output"></a>輸出  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 雖然上述範例示範的是使用常數進行明確類型轉換，相同的技巧也可以在物件上進行這些轉換。 下列程式碼片段示範這項功能：  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 使用「轉換」語法也可以指定明確類型轉換。 上述範例若是使用轉換語法重新撰寫則會如下所示：  
  
```  
d = (float)i;  
```  
  
 從單一值進行轉換時，轉換和函式樣式轉換的結果相同。 不過，在函式樣式語法中，您可以在轉換時指定一個以上的引數。 這項差異對於使用者定義的類型而言是很重要的。 請考慮 `Point` 類別及其轉換：  
  
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
  
 上述範例中，使用函式樣式轉換，可示範如何將兩個值 (一個用於*x* ，另一個用於*y*) 使用者定義型別`Point`。  
  
> [!CAUTION]
>  由於其中覆寫了 C++ 編譯器的內建類型檢查，因此請小心使用明確類型轉換。  
  
 [轉換](../cpp/cast-operator-parens.md)標記法，必須使用轉換為類型沒有*簡單類型名稱*（例如，指標或參考類型）。 轉換為型別，可以使用表示*簡單類型名稱*可以採任一格式寫入。 請參閱[類型規範](http://msdn.microsoft.com/en-us/34b6c737-0ef1-4470-9b77-b26e46c0bbd4)如需有關何者構成*簡單類型名稱*。  
  
 在轉換中定義類型是不合法。  
  
## <a name="see-also"></a>另請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
