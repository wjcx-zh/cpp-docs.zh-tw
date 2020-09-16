---
title: 如何：從 STL/CLR 容器轉換為 .NET 集合
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f5e289c330c83ac0c630a5b1f8f97b8c65fc7efb
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686440"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>如何：從 STL/CLR 容器轉換為 .NET 集合

本主題說明如何將 STL/CLR 容器轉換成其對等的 .NET 集合。 舉例而言，我們會示範如何將 STL/CLR [向量](../dotnet/vector-stl-clr.md) 轉換成 .net， <xref:System.Collections.Generic.ICollection%601> 以及如何將 stl/clr [對應](../dotnet/map-stl-clr.md) 轉換成 .net <xref:System.Collections.Generic.IDictionary%602> ，但是所有集合和容器的程式都很類似。

### <a name="to-create-a-collection-from-a-container"></a>從容器建立集合

1. 請使用下列其中一個方法：

   - 若要轉換容器的部分，請呼叫 [make_collection](../dotnet/make-collection-stl-clr.md) 函式，並傳遞 STL/CLR 容器的 begin iterator 和 end 反覆運算器，以複製到 .net 集合中。 此範本函式會採用 STL/CLR iterator 作為樣板引數。 第一個範例會示範這個方法。

   - 若要轉換整個容器，請將容器轉換成適當的 .NET 集合介面或介面集合。 第二個範例會示範這個方法。

## <a name="examples"></a>範例

在此範例中，我們會建立 STL/CLR `vector` ，並在其中加入5個元素。 然後，我們會藉由呼叫函數來建立 .NET 集合 `make_collection` 。 最後，我們會顯示新建立之集合的內容。

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

在此範例中，我們會建立 STL/CLR `map` ，並在其中加入5個元素。 接著，我們會建立 .NET <xref:System.Collections.Generic.IDictionary%602> 並直接指派給 `map` 它。 最後，我們會顯示新建立之集合的內容。

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>另請參閱

[STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)<br/>
[如何：從 .NET 集合轉換為 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
