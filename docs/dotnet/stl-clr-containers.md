---
title: STL/CLR 容器
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: bfdbbeb735f98f77046790e21c19dd2d21b9d5c6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988114"
---
# <a name="stlclr-containers"></a>STL/CLR 容器

STL/CLR 程式庫是由類似于C++標準程式庫中的容器所組成，但它會在 .NET Framework 的受管理環境中執行。 它不會與實際C++的標準程式庫保持在最新狀態，並且會針對舊版支援加以維護。

本文件提供了 STL/CLR 容器的概觀，例如容器項目的需求、您可以插入容器的項目類型，以及容器中項目的擁有權問題。 在適當的情況下，會C++提及原生標準程式庫和 STL/CLR 之間的差異。

## <a name="requirements-for-container-elements"></a>容器項目的需求

插入 STL/CLR 容器中的所有元素都必須遵守特定的指導方針。 如需詳細資訊，請參閱[STL/CLR 容器元素的需求](../dotnet/requirements-for-stl-clr-container-elements.md)。

## <a name="valid-container-elements"></a>有效的容器項目

STL/CLR 容器可保留兩種類型之一的項目：

- 參考類型的控制代碼。

- 參考型別。

- Unboxed 實值類型。

您不能將 Boxed 實值類型插入至任何 STL/CLR 容器。

### <a name="handles-to-reference-types"></a>參考類型的控制代碼

您可以將參考類型的控制代碼插入至 STL/CLR 容器。 C++ 中以 CLR 為目標的控制代碼與原生 C++ 的指標類似。 如需詳細資訊，請參閱[Handle To Object Operator （^）](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)。

#### <a name="example"></a>範例

下列範例顯示如何將 Employee 物件的控制碼插入至[cliext：： set](../dotnet/set-stl-clr.md)。

```cpp
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>參考類型

您也可以將參考類型 (而不是參考類型的控制代碼) 插入至 STL/CLR 容器。 此處的主要差異在於，當參考類型的容器遭到刪除時，會呼叫容器內部所有項目的解構函式。 在參考類型之控制代碼的容器中，將不會呼叫這些項目的解構函式。

#### <a name="example"></a>範例

下列範例說明如何將 Employee 物件插入至 `cliext::set` 內。

```cpp
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Unboxed 實值類型

您也可以將 Unboxed 實值類型插入至 STL/CLR 容器。 未裝箱的實值型別是尚未*封裝*成引用型別的實值型別。

實值類型項目可以是其中一個標準實值類型 (例如 `int`)，也可以是使用者定義的實值類型 (例如 `value class`)。 如需詳細資訊，請參閱[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>範例

下列範例會修改第一個範例，將 Employee 類別改為實值類型。 接著再將這個實值類型插入至 `cliext::set`，如第一個範例中所示。

```cpp
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

如果您嘗試將實數值型別的控制碼插入容器中，就會產生[編譯器錯誤 C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) 。

### <a name="performance-and-memory-implications"></a>效能和記憶體含意

在決定是要使用參考類型的控制代碼或實值類型作為容器項目時，您必須考量許多因素。 如果您決定使用實值類型，請記得在每次將項目插入至容器時建立這個項目的複本。 若為小型物件，這應該不會造成問題，但是如果插入的物件很大，則可能會減損效能。 此外，如果您使用實值類型，則無法同時在多個容器中儲存一個項目，因為每個容器將會擁有其項目的複本。

如果您決定使用參考類型的控制代碼，則可能會提升效能，因為在將項目插入至容器時，不需要製作項目的複本。 此外，不同於實值類型，其同一個項目可以存在於多個容器中。 不過，如果您決定使用控制代碼，則必須確保控制代碼有效，並且它所參考的物件沒有在程式的其他地方遭到刪除。

## <a name="ownership-issues-with-containers"></a>容器的擁有權問題

STL/CLR 中的容器會處理實值語意。 每當您將項目插入至容器時，也會插入該項目的複本。 如果您要取得類似參考的語意，可以插入物件的控制代碼物件而不是物件本身。

當您呼叫控制代碼物件的容器之清除或清理方法時，不會從記憶體釋放控制代碼所參考的物件。 您必須明確地刪除該物件，或者 (因為這些物件位於 Managed 堆積中) 在決定不再使用物件時允許記憶體回收行程釋放記憶體。

## <a name="see-also"></a>請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
