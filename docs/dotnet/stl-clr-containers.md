---
title: "STL/CLR 容器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, STL/CLR"
  - "STL/CLR, 容器"
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 程式庫有 Standard C\+\+ 程式庫中可找到的相同容器，不過它是執行在 .NET Framework 中的 Managed 環境。  如果您已熟悉 Standard Template Library \(STL\)， STL\/CLR 是您繼續使用在升級程式碼至 Common Language Runtime \(CLR\) 時已熟悉的技巧之最佳方法。  
  
 文件提供了 STL\/CLR 容器的概觀，例如容器項目的需求、您可以插入的容器項目的型別，以及容器中項目的擁有權發行。  其中提到原生標準樣板程式庫和 STL\/CLR 之間的差異。  
  
## 容器項目的需求  
 所有插入至 STL 容器的項目必須遵守某些方針。  如需詳細資訊，請參閱[STL\/CLR 容器項目的需求](../dotnet/requirements-for-stl-clr-container-elements.md)。  
  
## 有效的容器項目  
 STL\/CLR 容器可保留兩種型別之一的項目：  
  
-   參考型別的控制代碼。  
  
-   參考型別。  
  
-   Unboxed 實值型別。  
  
 您不能插入 Boxed 實值型別至任何 STL\/CLR 容器。  
  
### 參考型別的控制代碼。  
 您可以插入參考型別的控制代碼至 STL\/CLR 容器。  C\+\+ 中以 CLR 為目標的控制代碼是類似於原生 C\+\+ 的指標。  如需詳細資訊，請參閱[物件控制代碼運算子 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)。  
  
#### 範例  
 下列範例示範如何將 Employee 物件的控制代碼插入至 [cliext::set](../dotnet/set-stl-clr.md)。  
  
```  
// cliext_container_valid_reference_handle.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
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
  
### 參考類型  
 參考型別 \(而不是參考型別的控制代碼\) 也可以插入至 STL\/CLR 容器。  這裡的主要差異在於，當參考型別的容器被刪除時，會呼叫容器所有項目的解構函式。  在參考型別的控制代碼的容器，這些項目的解構函式將不會被呼叫。  
  
#### 範例  
 下列範例示範如何插入 Employee 物件至 `cliext::set` 內。  
  
```  
// cliext_container_valid_reference.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
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
  
### Unboxed 實值型別  
 您也可以插入 Unboxed 實值型別至 STL\/CLR 容器。  Unboxed 實值型別是尚未被 *boxed* 至參考型別的實值型別。  
  
 實值型別元素可以是其中一個標準實值型別，例如 `int`，也可以是使用者定義的實值型別，例如 `value class`。  如需詳細資訊，請參閱[Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
#### 範例  
 下列範例會修改第一個範例，將 Employee 類別改為實值型別。  這個實值型別接著會插入至 `cliext::set` ，就如第一個範例中所示。  
  
```  
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
  
 如果您嘗試插入實值型別的控制代碼到容器，會產生 [編譯器錯誤 C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md)。  
  
### 效能和記憶體含意  
 在決定使用參考型別的控制代碼或實值型別作為容器項目時，您必須考量許多因素。  如果您決定使用實值型別，請確定每次將項目插入至容器，產生這個項目的複本。  若為小型物件，這應該不會造成問題，但是如果插入物件很大，效能可能會減損。  此外，如果您使用實值型別，同時儲存一個項目在多個容器是不可能的，因為每個容器將會擁有其項目的複本。  
  
 如果您決定使用參考型別的控制代碼，效能可能會增加，因為在容器中插入時不需要製作項目的複本。  此外，不同於與實值型別，同一個項目可以存在於多個容器。  不過，如果您決定使用控制代碼，您必須小心確保控制代碼有效，並且它所參考的物件沒有在程式中的其他地方被刪除。  
  
## 容器的所有權限問題  
 STL\/CLR 的容器影響實值語意。  每當您插入項目至容器時，也會插入該項目的複本。  如果您要取得類似參考的語意，您可以插入物件的控制代碼物件而不是物件本身。  
  
 當您呼叫控制代碼物件的容器之清除或清理方法時，控制代碼所參考的物件不會從記憶體被釋放。  您必須明確地刪除物件，或者 \(因為這些物件在 Managed 堆積中\) 允許記憶體回收，以便一旦決定不再使用物件時，可以釋放記憶體。  
  
## 請參閱  
 [標準樣板程式庫](../misc/standard-template-library.md)