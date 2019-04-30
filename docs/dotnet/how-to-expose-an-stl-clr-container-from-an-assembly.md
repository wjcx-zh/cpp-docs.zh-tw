---
title: HOW TO：公開 STL/CLR 容器從組件
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: 206a95cbaa808f54d7ae0e500b5a2bea272d974b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387327"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>HOW TO：公開 STL/CLR 容器從組件

STL/CLR 容器，例如`list`和`map`會實作為樣板 ref 類別。 因為C++範本會在編譯時期具現化，有完全相同的簽章，但位於不同的組件的兩個範本類別其實是不同類型。 這表示範本類別，不可跨組件界限使用。

若要進行跨組件共用，STL/CLR 容器會實作泛型介面<xref:System.Collections.Generic.ICollection%601>。 利用這個泛型介面，所有語言的都支援泛型，包括C++， C#，和 Visual Basic 中，可以存取 STL/CLR 容器。

本主題說明如何顯示數個以撰寫的 STL/CLR 容器項目C++名為組件`StlClrClassLibrary`。 我們顯示兩個組件存取`StlClrClassLibrary`。 第一個組件以C++，並在第二個C#。

如果兩個組件以C++，您可以使用來存取容器的泛型介面及其`generic_container`typedef。 例如，如果您有容器的型別`cliext::vector<int>`，則其泛型介面是： `cliext::vector<int>::generic_container`。 同樣地，使用泛型介面取得迭代器`generic_iterator`typedef，如下所示： `cliext::vector<int>::generic_iterator`。

因為這些 typedef 宣告中C++標頭檔，以其他語言撰寫的組件無法使用它們。 因此，若要存取的泛型介面`cliext::vector<int>`在 C# 或任何其他.NET 語言中，使用`System.Collections.Generic.ICollection<int>`。 若要逐一查看這個集合，使用`foreach`迴圈。

下表列出每一個 STL/CLR 容器會實作泛型介面：

|STL/CLR 容器|泛型介面|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> 因為`queue`， `priority_queue`，和`stack`容器不支援迭代器，它們不會實作泛型介面，並不能存取的跨組件。

## <a name="example-1"></a>範例 1

### <a name="description"></a>描述

在此範例中，我們宣告C++類別，其中包含私用的 STL/CLR 成員資料。 然後，我們會宣告授與存取權的私用集合類別的公用方法。 我們是採用兩種不同的方式，一個用於C++用戶端，另一個用於其他.NET 用戶端。

### <a name="code"></a>程式碼

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>範例 2

### <a name="description"></a>描述

在此範例中，我們會實作範例 1 中所宣告的類別。 為了讓用戶端使用此類別庫，我們會使用資訊清單工具**mt.exe**在 DLL 中內嵌資訊清單檔案。 如需詳細資訊，請參閱程式碼註解。

如需有關的資訊清單工具和並排顯示組件的詳細資訊，請參閱 <<c0> [ 建置 C /C++隔離的應用程式和並排顯示組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。</c0>

### <a name="code"></a>程式碼

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>範例 3

### <a name="description"></a>描述

在此範例中，我們會建立C++會使用範例 1 和 2 中建立的類別程式庫的用戶端。 此用戶端會使用`generic_container`逐一查看的容器，並顯示其內容的 STL/CLR 容器的 typedef。

### <a name="code"></a>程式碼

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>範例 4

### <a name="description"></a>描述

在此範例中，我們會建立使用範例 1 和 2 中建立的類別程式庫的 C# 用戶端。 此用戶端會使用<xref:System.Collections.Generic.ICollection%601>STL/CLR 容器來逐一查看的容器，並顯示其內容的方法。

### <a name="code"></a>程式碼

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>另請參閱

[STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)
