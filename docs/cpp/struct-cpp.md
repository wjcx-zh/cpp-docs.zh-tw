---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: e9ffd30dd0017e912fd7c196e2d3f0e987fb0810
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780856"
---
# <a name="struct-c"></a>struct (C++)

**結構**關鍵字定義的結構類型和/或結構類型的變數。

## <a name="syntax"></a>語法

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>參數

*template-spec*<br/>
選擇性樣板規格。 如需詳細資訊，請參閱[樣板規格](templates-cpp.md)。

*struct*<br/>
**結構**關鍵字。

*ms-decl-spec*<br/>
選擇性儲存類別規格。 如需詳細資訊，請參閱[__declspec](../cpp/declspec.md)關鍵字。

*tag*<br/>
提供給結構的類型名稱。 標記會變成結構範圍內的保留字。 標記是選擇項。 如果省略，則會定義匿名結構。 如需詳細資訊，請參閱 <<c0> [ 匿名類別類型](../cpp/anonymous-class-types.md)。

*base-list*<br/>
這個結構從中衍生其成員的選擇性類別或結構清單。 請參閱[基底類別](../cpp/base-classes.md)如需詳細資訊。 每個基底類別或結構名稱可以加上存取規範 ([公開金鑰](../cpp/public-cpp.md)，[私人](../cpp/private-cpp.md)，[保護](../cpp/protected-cpp.md)) 和[虛擬](../cpp/virtual-cpp.md)關鍵字。 請參閱中的成員存取表[控制對類別成員存取](member-access-control-cpp.md)如需詳細資訊。

*member-list*<br/>
結構成員清單。 請參閱[類別成員概觀](../cpp/class-member-overview.md)如需詳細資訊。 唯一的差別在於**struct**用來取代**類別**。

*declarators*<br/>
指定名稱的結構宣告子清單。 宣告子清單會宣告結構類型的一個或多個執行個體。 如果結構的所有資料成員宣告子可包含初始設定式清單**公開**。 初始設定式清單是在結構中常見的因為資料成員**公開**預設。  請參閱[的宣告子概觀](../cpp/overview-of-declarators.md)如需詳細資訊。

## <a name="remarks"></a>備註

結構類型是使用者定義的複合類型。 它是由具有不同類型的欄位或成員所組成。

C + + 結構是與類別相同之處在於其成員**公開**預設。

如需 managed 的類別和結構在 C + + /cli CLI，請參閱[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="using-a-structure"></a>使用結構

在 C 中，您必須明確地使用**結構**關鍵字來宣告結構。 在 c + +，您不需要使用**結構**關鍵字之後已定義的類型。

您可以選擇在定義結構類型時宣告變數，方法是將一個或多個逗號分隔的變數名稱放在右大括號和分號之間。

結構變數可以初始化。 每個變數的初始化都必須以大括號括住。

如需相關資訊，請參閱[類別](../cpp/class-cpp.md)， [union](../cpp/unions.md)，並[enum](../cpp/enumerations-cpp.md)。

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
