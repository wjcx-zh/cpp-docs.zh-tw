---
title: "結構 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- struct_cpp
dev_langs:
- C++
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4918adb779a620afd4a0c1e4ef64ef9892de1ba8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="struct-c"></a>struct (C++)
`struct` 關鍵字會定義結構類型和 (或) 結構類型的變數。  
  
## <a name="syntax"></a>語法  
  
```  
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### <a name="parameters"></a>參數  
 `template-spec`  
 選擇性樣板規格。 如需詳細資訊，請參閱[樣板規格](templates-cpp.md)。  
  
 `struct`  
 `struct` 關鍵字。  
  
 `ms-decl-spec`  
 選擇性儲存類別規格。 如需詳細資訊，請參閱[__declspec](../cpp/declspec.md)關鍵字。  
  
 `tag`  
 提供給結構的類型名稱。 標記會變成結構範圍內的保留字。 標記是選擇項。 如果省略，則會定義匿名結構。 如需詳細資訊，請參閱[匿名類別類型](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 這個結構從中衍生其成員的選擇性類別或結構清單。 請參閱[基底類別](../cpp/base-classes.md)如需詳細資訊。 每個基底類別或結構名稱前面可以有存取規範 ([公用](../cpp/public-cpp.md)，[私人](../cpp/private-cpp.md)，[保護](../cpp/protected-cpp.md)) 和[虛擬](../cpp/virtual-cpp.md)關鍵字。 請參閱中的成員存取表[控制對類別成員存取](member-access-control-cpp.md)如需詳細資訊。  
  
 `member-list`  
 結構成員清單。 請參閱[類別成員概觀](../cpp/class-member-overview.md)如需詳細資訊。 這裡唯一的差異在於，`struct` 會用來取代 `class`。  
  
 `declarators`  
 指定類別名稱的宣告子清單。 宣告子清單會宣告結構類型的一個或多個執行個體。 如果類別的所有資料成員都是 `public`，則宣告子可包含初始設定式清單。 初始設定式清單在結構中很常見，因為資料成員預設為 `public`。  請參閱[宣告子概觀](../cpp/overview-of-declarators.md)如需詳細資訊。  
  
## <a name="remarks"></a>備註  
 結構類型是使用者定義的複合類型。 它是由具有不同類型的欄位或成員所組成。  
  
 在 C++ 中，結構與類別相同，差別在於結構的成員預設為 `public`。  
  
 如需 managed 的類別和結構的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="using-a-structure"></a>使用結構  
 在 C 中，您必須明確使用 `struct` 關鍵字宣告結構。 在 C++ 中，您不需要在定義類型後使用 `struct` 關鍵字。  
  
 您可以選擇在定義結構類型時宣告變數，方法是將一個或多個逗號分隔的變數名稱放在右大括號和分號之間。  
  
 結構變數可以初始化。 每個變數的初始化都必須以大括號括住。  
  
 如需相關資訊，請參閱[類別](../cpp/class-cpp.md)， [union](../cpp/unions.md)，和[列舉](../cpp/enumerations-cpp.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  

