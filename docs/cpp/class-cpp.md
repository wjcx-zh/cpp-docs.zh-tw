---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 6475bc3703ce1bd7cf6103f4be8c12edc36e98b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226004"
---
# <a name="class-c"></a>class (C++)

關鍵字會宣告 **`class`** 類別類型，或定義類別類型的物件。

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

*範本-規格*<br/>
選擇性樣板規格。 如需詳細資訊，請參閱[範本](templates-cpp.md)。

*class*<br/>
**`class`** 關鍵字。

*extended-decl-modifier-seq-規格*<br/>
選擇性儲存類別規格。 如需詳細資訊，請參閱[__declspec](../cpp/declspec.md)關鍵字。

*標記*<br/>
提供給類別的類型名稱。 標記會變成類別範圍內的保留字。 標記是選擇項。 如果省略，則會定義匿名類別。 如需詳細資訊，請參閱[匿名類別類型](../cpp/anonymous-class-types.md)。

*base-list*<br/>
這個類別從中衍生其成員的選擇性類別或結構清單。 如需詳細資訊，請參閱[基類](../cpp/base-classes.md)。 每個基類或結構名稱的前面都可以是存取規範（[public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)、 [protected](../cpp/protected-cpp.md)）和[virtual](../cpp/virtual-cpp.md)關鍵字。 如需詳細資訊，請參閱[控制類別成員的存取](member-access-control-cpp.md)中的成員存取表格。

*成員清單*<br/>
類別成員的清單。 如需詳細資訊，請參閱[類別成員總覽](../cpp/class-member-overview.md)。

*declarators*<br/>
宣告子清單，指定類別類型的一個或多個執行個體名稱。 如果類別的所有資料成員都是，宣告子可能會包含初始化運算式清單 **`public`** 。 這在結構中更為常見，其資料成員 **`public`** 預設為，而不是在類別中。 如需詳細資訊，請參閱宣告子的[總覽](../cpp/overview-of-declarators.md)。

## <a name="remarks"></a>備註

一般來說，如需類別的詳細資訊，請參閱下列其中一個主題：

- [結構](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

如需 c + +/CLI 和 c + +/CX 中 managed 類別和結構的詳細資訊，請參閱[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>範例

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
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
