---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 4404767fc6cf07c2a7a23d460e13bb191fef387a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555138"
---
# <a name="class-c"></a>class (C++)

**類別**關鍵字宣告類別類型，或定義類別類型的物件。

## <a name="syntax"></a>語法

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>參數

*範本規格*<br/>
選擇性樣板規格。 如需詳細資訊，請參閱[範本](templates-cpp.md)。

*class*<br/>
**類別**關鍵字。

*ms-decl-modifier-規格*<br/>
選擇性儲存類別規格。 如需詳細資訊，請參閱[__declspec](../cpp/declspec.md)關鍵字。

*標記*<br/>
提供給類別的類型名稱。 標記會變成類別範圍內的保留字。 標記是選擇項。 如果省略，則會定義匿名類別。 如需詳細資訊，請參閱 <<c0> [ 匿名類別類型](../cpp/anonymous-class-types.md)。

*基底清單*<br/>
這個類別從中衍生其成員的選擇性類別或結構清單。 請參閱[基底類別](../cpp/base-classes.md)如需詳細資訊。 每個基底類別或結構名稱可以加上存取規範 ([公開金鑰](../cpp/public-cpp.md)，[私人](../cpp/private-cpp.md)，[保護](../cpp/protected-cpp.md)) 和[虛擬](../cpp/virtual-cpp.md)關鍵字。 請參閱中的成員存取表[控制對類別成員存取](member-access-control-cpp.md)如需詳細資訊。

*成員清單*<br/>
類別成員的清單。 請參閱[類別成員概觀](../cpp/class-member-overview.md)如需詳細資訊。

*宣告子*<br/>
宣告子清單，指定類別類型的一個或多個執行個體名稱。 如果類別的所有資料成員宣告子可包含初始設定式清單**公開**。 這是在結構中，資料成員是較常見**公開**根據預設，比在類別。 請參閱[的宣告子概觀](../cpp/overview-of-declarators.md)如需詳細資訊。

## <a name="remarks"></a>備註

一般來說，如需類別的詳細資訊，請參閱下列其中一個主題：

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

如需 managed 的類別和結構的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>範例

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[類別和結構](../cpp/classes-and-structs-cpp.md)