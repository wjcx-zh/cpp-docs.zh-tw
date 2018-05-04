---
title: 遞增和遞減運算子多載 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dee35098dbf78e04241f04687c74c40ded1a0010
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="increment-and-decrement-operator-overloading-c"></a>遞增和遞減運算子多載 (C++)
遞增和遞減運算子屬於特殊的分類，因為每個運算子都有兩種變數：  
  
-   前置遞增和後置遞增  
  
-   前置遞減和後置遞減  
  
 當您撰寫多載運算子函式時，分別針對這些運算子實作前置和後置的不同版本可能會很有用。 若要區別這兩者，請遵守下列規則：運算子的前置格式宣告方式就和其他一元運算子完全相同，後置格式可接受類型為 `int` 的其他引數。  
  
> [!NOTE]
>  為多載運算子指定遞增或遞減運算子的後置格式時，其他引數必須為 `int` 類型，指定其他類型會產生錯誤。  
  
 下列範例顯示如何為 `Point` 類別定義前置和後置遞增及遞減運算子：  
  
```  
// increment_and_decrement1.cpp  
class Point  
{  
public:  
   // Declare prefix and postfix increment operators.  
   Point& operator++();       // Prefix increment operator.  
   Point operator++(int);     // Postfix increment operator.  
  
   // Declare prefix and postfix decrement operators.  
   Point& operator--();       // Prefix decrement operator.  
   Point operator--(int);     // Postfix decrement operator.  
  
   // Define default constructor.  
   Point() { _x = _y = 0; }  
  
   // Define accessor functions.  
   int x() { return _x; }  
   int y() { return _y; }  
private:  
   int _x, _y;  
};  
  
// Define prefix increment operator.  
Point& Point::operator++()  
{  
   _x++;  
   _y++;  
   return *this;  
}  
  
// Define postfix increment operator.  
Point Point::operator++(int)  
{  
   Point temp = *this;  
   ++*this;  
   return temp;  
}  
  
// Define prefix decrement operator.  
Point& Point::operator--()  
{  
   _x--;  
   _y--;  
   return *this;  
}  
  
// Define postfix decrement operator.  
Point Point::operator--(int)  
{  
   Point temp = *this;  
   --*this;  
   return temp;  
}  
int main()  
{  
}  
```  
  
 相同的運算子可以在檔案範圍 (全域) 中使用下列函式標頭加以定義：  
  
```  
friend Point& operator++( Point& )      // Prefix increment  
friend Point& operator++( Point&, int ) // Postfix increment  
friend Point& operator--( Point& )      // Prefix decrement  
friend Point& operator--( Point&, int ) // Postfix decrement  
```  
  
 用於表示遞增或遞減運算子之後置格式的類型 `int` 引數，通常不會用於傳遞引數。 它通常包含值 0。 不過，可以依如下的方式使用：  
  
```  
// increment_and_decrement2.cpp  
class Int  
{  
public:  
    Int &operator++( int n );  
private:  
    int _i;  
};  
  
Int& Int::operator++( int n )  
{  
    if( n != 0 )    // Handle case where an argument is passed.  
        _i += n;  
    else  
        _i++;       // Handle case where no argument is passed.  
    return *this;  
}  
int main()  
{  
   Int i;  
   i.operator++( 25 ); // Increment by 25.  
}  
```  
  
 除了明確的引動過程之外，沒有其他語法會使用遞增或遞減運算子來傳遞這些值，如上述程式碼所示。 實作這項功能較簡單的方式是多載加法/指派運算子 (`+=`)。  
  
## <a name="see-also"></a>另請參閱  
 [運算子多載](../cpp/operator-overloading.md)