---
title: 類別成員概觀
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 02c5593d9fb5e72ee6b398c9637397ab26c9f3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229060"
---
# <a name="class-member-overview"></a>類別成員概觀

類別或結構包含其成員。 類別所執行的工作是由其成員函式執行。 它所維護的狀態會儲存在其資料成員中。 成員的初始化是由「函式」完成，而清除工作（例如釋放記憶體和釋出資源）則由「析構函式」完成。 在 C++11 和更新版本中，可以 (且通常應該) 在宣告時初始化資料成員。

## <a name="kinds-of-class-members"></a>類別成員的類型

成員分類的完整清單如下：

- [特殊成員](special-member-functions.md)函式。

- [成員函式的總覽](overview-of-member-functions.md)。

- 包含內建類型和其他使用者定義類型的[資料成員](static-members-cpp.md)。

- 操作員

- [嵌套類別](nested-class-declarations.md)宣告和。）

- [等位](unions.md)

- [Enumerations](../cpp/enumerations-cpp.md)列舉。

- [位欄位](../cpp/cpp-bit-fields.md)。

- [朋友](../cpp/friend-cpp.md)。

- [別名和 typedef](../cpp/aliases-and-typedefs-cpp.md)。

    > [!NOTE]
    >  前述清單包含 Friend，是因為它們包含在類別宣告中。 不過，它們不是真正的類別成員，因為它們不在類別的範圍內。

## <a name="example-class-declaration"></a>範例類別宣告

下列範例示範簡單類別宣告：

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>成員存取範圍

成員清單中所宣告類別的成員。 類別的成員清單可以使用稱為存取規範的關鍵字，分割成任意數目的 **`private`** **`protected`** 和 **`public`** 區段。  冒號 **：** 必須遵循存取規範。  這些區段不需要是連續的，也就是說，這些關鍵字中任何一個都可以在成員清單中出現多次。  關鍵字會指定到下一個存取指定名稱，或右大括號之前所有成員的存取權限。 如需詳細資訊，請參閱[成員存取控制（c + +）](../cpp/member-access-control-cpp.md)。

## <a name="static-members"></a>靜態成員

資料成員可以宣告為靜態，這表示類別的所有物件都可以存取其相同複本。 成員函式可以宣告為靜態，在此情況下，它只能存取類別的靜態資料成員（而且沒有*此*指標）。 如需詳細資訊，請參閱[靜態資料成員](../cpp/static-members-cpp.md)。

## <a name="special-member-functions"></a>特殊成員函式

特殊成員函式是未在原始程式碼中指定函式時由編譯器自動提供的函式。

1. 預設建構函式

1. 複製建構函式

1. **（C + + 11）** 移動構造函式

1. 複製指派運算子

1. **（C + + 11）** 移動指派運算子

1. 解構函式

如需詳細資訊，請參閱[特殊成員](../cpp/special-member-functions.md)函式。

## <a name="memberwise-initialization"></a>成員方式初始化

在 C++11 和更新版本中，非靜態成員宣告子可以包含初始設定式。

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

如果成員在建構函式中獲指派值，該值會覆寫用來在宣告時初始化成員的值。

特定類別類型的所有物件只會有一個共用的靜態資料成員複本。 靜態資料成員必須以檔案範圍定義，而且可以依檔案範圍初始化  （如需靜態資料成員的詳細資訊，請參閱[靜態資料成員](../cpp/static-members-cpp.md)）。下列範例顯示如何執行這些初始化：

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
> 類別名稱 `CanInit2` 前面必須加上 `i`，才能將所要定義的 `i` 指定為 `CanInit2` 類別的成員。

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)
