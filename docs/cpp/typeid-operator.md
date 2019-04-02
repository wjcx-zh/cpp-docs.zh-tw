---
title: typeid 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: b1185f48df4a941eb2a5d81bfa67d07cdf4387d0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780882"
---
# <a name="typeid-operator"></a>typeid 運算子

## <a name="syntax"></a>語法

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>備註

**Typeid**運算子允許在執行階段判斷物件的類型。

結果**typeid**是`const type_info&`。 值是參考`type_info`物件，表示*型別 id*或型別*運算式*，視哪種**typeid**用。 請參閱[type_info 類別](../cpp/type-info-class.md)如需詳細資訊。

**Typeid**運算子無法搭配 managed 類型 （抽象宣告子或執行個體），請參閱[typeid](../extensions/typeid-cpp-component-extensions.md)如需取得資訊<xref:System.Type>指定的型別。

**Typeid**運算子會執行階段檢查套用至多型類別類型的左值時，無法判斷真正的物件類型所提供的靜態資訊。 這類案例包括：

- 類別的參考

- 使用取值的指標 \*

- 註標的指標 (也就是 [ ])。 (請注意，使用具有多型類型指標的註標通常並不安全)。

如果*運算式*指向基底類別類型，但物件實際上是衍生自該基底類別，型別的`type_info`參考衍生的類別是結果。 *運算式*必須指向多型類型 （具有虛擬函式的類別）。 否則，結果就是`type_info`靜態類別中所指*運算式*。 此外，指標必須已取值，才會使用其指向的物件。 不取值的指標，結果會是`type_info`指標，不是它會指向。 例如: 

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo.h>

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

如果*運算式*會為指標取值，指標的值為零，並**typeid**就會擲回[bad_typeid 例外狀況](../cpp/bad-typeid-exception.md)。 如果指標不指向有效的物件，`__non_rtti_object`會擲回例外狀況，表示嘗試分析觸發錯誤的 RTTI （類似存取違規），因為物件是以某種方式無效 （不正確的指標或程式碼不以編譯[/GR](../build/reference/gr-enable-run-time-type-information.md))。

如果*運算式*指標和物件的基底類別的參考都不是那麼`type_info`表示的靜態類型的參考*運算式*。 *靜態型別*運算式的參考類型的運算式所知在編譯時期。 評估運算式的靜態類型時，會忽略執行語意。 此外，在判斷運算式的靜態類型時，會盡可能忽略參考：

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**typeid**也可用在範本中判斷樣板參數的類型：

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

[執行階段類型資訊](../cpp/run-time-type-information.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)