---
title: bad_cast 例外狀況
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998781"
---
# <a name="bad_cast-exception"></a>bad_cast 例外狀況

**Dynamic_cast**運算子會擲回**bad_cast**例外狀況，做為轉換成參考型別失敗的結果。

## <a name="syntax"></a>語法

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>備註

**Bad_cast**的介面為：

```cpp
class bad_cast : public exception
```

下列程式碼包含會擲回**bad_cast**例外狀況之失敗**dynamic_cast**的範例。

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

會擲回例外狀況，因為轉換的物件（圖形）不是從指定的轉換類型（圓形）衍生而來。 若要避免例外狀況，請將這些宣告加入至 `main`：

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

然後，在**try**區塊中反轉轉換的意義，如下所示：

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 類型物件的建構函式。|

### <a name="functions"></a>Functions

|函數|描述|
|-|-|
|[what](#what)|TBD|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|指派運算子，可將一個 `bad_cast` 物件指派給另一個。|

## <a name="bad_cast"></a>bad_cast

`bad_cast` 類型物件的建構函式。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operator =

指派運算子，可將一個 `bad_cast` 物件指派給另一個。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>我

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>另請參閱

[Dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)\
[關鍵字](../cpp/keywords-cpp.md)\
[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
