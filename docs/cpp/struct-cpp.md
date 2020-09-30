---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: d0092cf107159f4c84b431f5eeae130df64dc835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507459"
---
# <a name="struct-c"></a>struct (C++)

關鍵字會定義結構類型 **`struct`** 和/或結構類型的變數。

## <a name="syntax"></a>語法

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>參數

*範本-規格*<br/>
選擇性樣板規格。 如需詳細資訊，請參閱 [範本規格](templates-cpp.md)。

*結構*<br/>
**`struct`** 關鍵字。

*decl 規格*<br/>
選擇性儲存類別規格。 如需詳細資訊，請參閱 [__declspec](../cpp/declspec.md) 關鍵字。

*標籤*<br/>
提供給結構的類型名稱。 標記會變成結構範圍內的保留字。 標記是選擇項。 如果省略，則會定義匿名結構。 如需詳細資訊，請參閱 [匿名類別類型](../cpp/anonymous-class-types.md)。

*base-list*<br/>
這個結構從中衍生其成員的選擇性類別或結構清單。 如需詳細資訊，請參閱 [基底類別](../cpp/base-classes.md) 。 每個基類或結構名稱的前面都可以是存取規範 ([public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)、 [protected](../cpp/protected-cpp.md)) 和 [virtual](../cpp/virtual-cpp.md) 關鍵字。 如需詳細資訊，請參閱 [控制類別成員存取](member-access-control-cpp.md) 的成員訪問表格。

*成員清單*<br/>
結構成員清單。 如需詳細資訊，請參閱 [類別成員總覽](../cpp/class-member-overview.md) 。 唯一的差異在於，它是 **`struct`** 用來取代 **`class`** 。

*declarators*<br/>
指定結構名稱的宣告子清單。 宣告子清單會宣告結構類型的一個或多個執行個體。 如果結構的所有資料成員都是，宣告子可以包含初始化運算式清單 **`public`** 。 初始化運算式清單在結構中是常見的，因為資料成員 **`public`** 預設為。  如需詳細資訊，請參閱宣告子的 [總覽](./declarations-and-definitions-cpp.md) 。

## <a name="remarks"></a>備註

結構類型是使用者定義的複合類型。 它是由具有不同類型的欄位或成員所組成。

在 c + + 中，結構與類別相同，不同之處在于它的成員 **`public`** 預設為。

如需 c + +/CLI 中 managed 類別和結構的詳細資訊，請參閱 [類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="using-a-structure"></a>使用結構

在 C 中，您必須明確使用 **`struct`** 關鍵字來宣告結構。 在 c + + 中，您不需要在 **`struct`** 定義型別之後使用關鍵字。

您可以選擇在定義結構類型時宣告變數，方法是將一個或多個逗號分隔的變數名稱放在右大括號和分號之間。

結構變數可以初始化。 每個變數的初始化都必須以大括號括住。

如需相關資訊，請參閱 [class](../cpp/class-cpp.md)、 [union](../cpp/unions.md)和 [enum](../cpp/enumerations-cpp.md)。

## <a name="example"></a>範例

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
