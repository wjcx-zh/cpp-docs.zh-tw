---
title: "struct (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "struct"
  - "struct_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "struct 建構函式"
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# struct (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`struct` 關鍵字會定義結構類型和 \(或\) 結構類型的變數。  
  
## 語法  
  
```  
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### 參數  
 `template-spec`  
 選擇性樣板規格。  如需詳細資訊，請參閱[樣板規格](../Topic/Template%20Specifications.md)。  
  
 `struct`  
 `struct` 關鍵字。  
  
 `ms-decl-spec`  
 選擇性儲存類別規格。  如需詳細資訊，請參閱 [\_\_declspec](../cpp/declspec.md) 關鍵字。  
  
 `tag`  
 提供給結構的類型名稱。  標記會變成結構範圍內的保留字。  標記是選擇項。  如果省略，則會定義匿名結構。  如需詳細資訊，請參閱[匿名類別類型](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 這個結構從中衍生其成員的選擇性類別或結構清單。  如需詳細資訊，請參閱[基底類別](../cpp/base-classes.md)。  每一個基底類別或結構名稱前面都可以加上存取規範 \([public](../cpp/public-cpp.md)、[private](../cpp/private-cpp.md)、[protected](../cpp/protected-cpp.md)\) 和 [virtual](../cpp/virtual-cpp.md) 關鍵字。  如需詳細資訊，請參閱[控制對類別成員的存取](../misc/controlling-access-to-class-members.md)中的成員存取表。  
  
 `member-list`  
 結構成員清單。  如需詳細資訊，請參閱[類別成員概觀](../cpp/class-member-overview.md)。  這裡唯一的差異在於，`struct` 會用來取代 `class`。  
  
 `declarators`  
 指定類別名稱的宣告子清單。  宣告子清單會宣告結構類型的一個或多個執行個體。  如果類別的所有資料成員都是 `public`，則宣告子可包含初始設定式清單。  初始設定式清單在結構中很常見，因為資料成員預設為 `public`。如需詳細資訊，請參閱[宣告子概觀](../cpp/overview-of-declarators.md)。  
  
## 備註  
 結構類型是使用者定義的複合類型。  它是由具有不同類型的欄位或成員所組成。  
  
 在 C\+\+ 中，結構與類別相同，差別在於結構的成員預設為 `public`。  
  
 如需 Managed 類別和結構的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## 使用結構  
 在 C 中，您必須明確使用 `struct` 關鍵字宣告結構。  在 C\+\+ 中，您不需要在定義類型後使用 `struct` 關鍵字。  
  
 您可以選擇在定義結構類型時宣告變數，方法是將一個或多個逗號分隔的變數名稱放在右大括號和分號之間。  
  
 結構變數可以初始化。  每個變數的初始化都必須以大括號括住。  
  
 如需相關資訊，請參閱[類別](../cpp/class-cpp.md)、[等位](../cpp/unions.md)和[列舉](../cpp/enumerations-cpp.md)。  
  
## 範例  
  
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
  
## 請參閱  
 [\(NOTINBUILD\) Defining Class Types](http://msdn.microsoft.com/zh-tw/e8c65425-0f3a-4dca-afc2-418c3b1e57da)