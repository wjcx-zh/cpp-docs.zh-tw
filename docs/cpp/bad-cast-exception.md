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
ms.openlocfilehash: 2efe5be5e44751831a56b29cfc629df2d21843f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229177"
---
# <a name="bad_cast-exception"></a>bad_cast 例外狀況

運算子會擲回**bad_cast**例外狀況， **`dynamic_cast`** 這是轉換成參考型別失敗的結果。

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

下列程式碼包含失敗 **`dynamic_cast`** 的範例，它會擲回**bad_cast**例外狀況。

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

然後在區塊中反轉轉換的意義 **`try`** ，如下所示：

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 類型物件的建構函式。|

### <a name="functions"></a>函式

|函式|說明|
|-|-|
|[我](#what)|TBD|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[operator =](#op_eq)|指派運算子，可將一個 `bad_cast` 物件指派給另一個。|

## <a name="bad_cast"></a><a name="bad_cast"></a>bad_cast

`bad_cast` 類型物件的建構函式。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="operator"></a><a name="op_eq"></a>operator =

指派運算子，可將一個 `bad_cast` 物件指派給另一個。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a><a name="what"></a>我

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>另請參閱

[dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)\
[字](../cpp/keywords-cpp.md)\
[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)
