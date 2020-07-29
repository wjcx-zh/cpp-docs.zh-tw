---
title: 識別項 (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
ms.openlocfilehash: 2d16dd318cd42b6294ef60edf44a16ccaf47b99b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187669"
---
# <a name="identifiers-c"></a>識別項 (C++)

識別項是字元序列，用來表示下列其中一項：

- 物件或變數名稱

- 類別、結構或等位名稱

- 列舉類型名稱

- 類別、結構、等位或列舉的成員

- 函式或類別成員函式

- typedef 名稱

- 標籤名稱

- 巨集名稱

- 巨集參數

下列字元可做為識別項的任何字元：

```
_ a b c d e f g h i j k l m
n o p q r s t u v w x y z
A B C D E F G H I J K L M
N O P Q R S T U V W X Y Z
```

識別項中也允許特定範圍的通用字元名稱。  識別項中的通用字元名稱無法指定控制字元或基本來源字元集中的字元。 如需詳細資訊，請參閱 [Character Sets](../cpp/character-sets.md)。 下列 Unicode 字碼指標數字範圍可做為通用字元名稱，以代表識別項中的任何字元：

- 00A8、00AA、00AD、00AF、00B2-00B5、00B7-00BA、00BC-00BE、00C0-00D6、00D8-00F6、00F8-00FF、0100-02FF、0370-167F、1681-180D、180F-1DBF、1E00-1FFF、200B-200D、202A-202E、203F-2040、2054、2060-206F、2070-20CF、2100-218F、2460-24FF、2776-2793、2C00-2DFF、2E80-2FFF、3004-3007、3021-302F、3031-303F、3040-D7FF、F900-FD3D、FD40-FDCF、FDF0-FE1F、FE30-FE44、FE47-FFFD、10000-1FFFD、20000-2FFFD、30000-3FFFD、40000-4FFFD、50000-5FFFD、60000-6FFFD、70000-7FFFD、80000-8FFFD、90000-9FFFD、A0000-AFFFD、B0000-BFFFD、C0000-CFFFD、D0000-DFFFD、E0000-EFFFD

下列字元在識別項中，除了第一個字元以外，都可做為其任何字元：

```
0 1 2 3 4 5 6 7 8 9
```

下列 Unicode 字碼指標數字範圍也可做為通用字元名稱，以代表識別項中除了第一個字元以外的任何字元：

- 0300-036F、1DC0-1DFF、20D0-20FF、FE20-FE2F

**Microsoft 特定的**

Microsoft C++ 識別項只有前 2048 個字元是有意義的。 使用者定義類型的名稱已由編譯器「裝飾」來保存類型資訊。 產生的名稱 (含類型資訊) 不能超過 2048 個字元 （如需詳細資訊，請參閱[裝飾名稱](../build/reference/decorated-names.md)）。可能影響裝飾識別碼長度的因素如下：

- 識別項表示的是使用者定義類型的物件還是衍生自使用者定義類型的類型。

- 識別項表示的是函式還是衍生自函式的類型。

- 函式的引數數目。

貨幣符號 `$` 是 Microsoft c + + 編譯器（MSVC）中的有效識別碼字元。 MSVC 也可讓您使用識別碼中允許範圍的通用字元名稱所代表的實際字元。 若要使用這些字元，您必須使用包含這些字元的檔案編碼字碼頁來儲存檔案。  下列範例示範如何在程式碼中交換使用擴充字元和通用字元名稱。

```cpp
// extended_identifier.cpp
// In Visual Studio, use File, Advanced Save Options to set
// the file encoding to Unicode codepage 1200
struct テスト         // Japanese 'test'
{
    void トスト() {}  // Japanese 'toast'
};

int main() {
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form
    パン.トスト();        // compiler recognizes UCN or literal form
}
```

編譯 C++/CLI 程式碼時，識別項中允許之字元範圍的限制較少。 使用 /clr 編譯之程式碼中的識別項應該遵循  [標準 ECMA-335：通用語言基礎結構 (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)。

**結束 Microsoft 專有**

識別項的第一個字元必須是字母 (大寫或小寫) 字元或底線 ( **_** )。 由於 C++ 識別項要區分大小寫， `fileName` 與 `FileName`不同。

識別項的拼字、大小寫不能與關鍵字完全相同。 包含關鍵字的識別項是合法的。 例如， `Pint` 是合法的識別碼，即使它包含，也 **`int`** 就是關鍵字。

在識別碼中使用兩個連續底線字元（ **__** ），或單一前置底線後面接著大寫字母，則會保留給所有範圍中的 c + + 程式。 因為可能與目前或未來保留的識別項相衝突，您應該避免在具有檔案範圍的名稱中使用一個後面接著小寫字母的前置底線。

## <a name="see-also"></a>另請參閱

[詞法慣例](../cpp/lexical-conventions.md)
