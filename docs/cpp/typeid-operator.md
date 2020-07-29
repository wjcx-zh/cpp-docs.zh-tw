---
title: typeid 運算子
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: e17b88d81d9987ec586401e025e108cfbe88cb3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223520"
---
# <a name="typeid-operator"></a>typeid 運算子

## <a name="syntax"></a>語法

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>備註

**`typeid`** 運算子可讓您在執行時間決定物件的型別。

的結果 **`typeid`** 是 `const type_info&` 。 此值是 `type_info` 物件的參考，代表*類型識別碼*或*運算式*的類型，視使用何種形式而定 **`typeid`** 。 如需詳細資訊，請參閱[Type_info 類別](../cpp/type-info-class.md)。

**`typeid`** 運算子不適用於 managed 類型（抽象宣告子或實例）。 如需取得 <xref:System.Type> 指定類型之的詳細資訊，請參閱[typeid](../extensions/typeid-cpp-component-extensions.md)。

運算子會在套用至多型 **`typeid`** 類別類型的左值時執行執行時間檢查，其中物件的 true 類型無法由提供的靜態資訊判斷。 這類案例包括：

- 類別的參考

- 參考的指標，使用`*`

- 一個下標指標（ `[ ]` ）。 （以多型類型的指標來使用注標並不安全）。

如果*運算式*指向基類型別，但物件實際上是衍生自該基類的型別， `type_info` 則衍生類別的參考就是結果。 *運算式*必須指向多型類型（具有虛擬函式的類別）。 否則，結果會是 `type_info` *運算式*中所參考之靜態類別的。 此外，必須對指標進行取值，讓使用的物件是它所指向的物件。 如果沒有取值指標，則結果會是 `type_info` 指標的，而不是它所指向的。 例如：

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

如果*運算式*正在取值指標，且該指標的值為零，則會擲回 **`typeid`** [bad_typeid 例外](../cpp/bad-typeid-exception.md)狀況。 如果指標未指向有效的物件，則會擲回 `__non_rtti_object` 例外狀況。 這表示嘗試分析觸發錯誤的 RTTI，是因為物件是不正確。 （例如，它是錯誤指標，或程式碼未使用[/GR](../build/reference/gr-enable-run-time-type-information.md)進行編譯）。

如果*運算式*不是指標，而不是物件之基類的參考，則結果會是 `type_info` 代表*運算式*靜態類型的參考。 運算式的*靜態類型*會參考在編譯時期已知的運算式類型。 評估運算式的靜態類型時，會忽略執行語意。 此外，在判斷運算式的靜態類型時，會盡可能忽略參考：

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** 也可以在範本中用來判斷樣板參數的類型：

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>另請參閱

[執行時間類型資訊](../cpp/run-time-type-information.md)\
[關鍵字](../cpp/keywords-cpp.md)
