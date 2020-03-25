---
title: 遞增和遞減運算子多載 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 8d64f0af994f88d0f4ecd3a5921de4a16b8bdaaa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178279"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>遞增和遞減運算子多載 (C++)

遞增和遞減運算子屬於特殊的分類，因為每個運算子都有兩種變數：

- 前置遞增和後置遞增

- 前置遞減和後置遞減

當您撰寫多載運算子函式時，分別針對這些運算子實作前置和後置的不同版本可能會很有用。 為了區分兩者，會觀察到下列規則：運算子的前置格式宣告方式與任何其他一元運算子完全相同;後置形式會接受**int**類型的額外引數。

> [!NOTE]
>  為遞增或遞減運算子的後置形式指定多載運算子時，其他引數必須為**int**類型。指定任何其他類型會產生錯誤。

下列範例顯示如何為 `Point` 類別定義前置和後置遞增及遞減運算子：

```cpp
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

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

**Int**類型的引數，代表遞增或遞減運算子的後置形式，通常不會用來傳遞引數。 它通常包含值 0。 不過，可以依如下的方式使用：

```cpp
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

除了明確的引動過程之外，沒有其他語法會使用遞增或遞減運算子來傳遞這些值，如上述程式碼所示。 執行此功能的更簡單方法是多載加法/指派運算子（ **+=** ）。

## <a name="see-also"></a>另請參閱

[運算子多載](../cpp/operator-overloading.md)
