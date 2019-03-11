---
title: HOW TO：從.NET 集合轉換為 STL/CLR 容器
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 836623f6d539b7b28765763a3dc36d477f8c1499
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741693"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>HOW TO：從.NET 集合轉換為 STL/CLR 容器

本主題說明如何將.NET 集合轉換為其相等的 STL/CLR 容器。 做為範例中，我們示範如何將轉換.NET <xref:System.Collections.Generic.List%601> STL/clr[向量](../dotnet/vector-stl-clr.md)以及如何轉換.NET <xref:System.Collections.Generic.Dictionary%602> STL/clr[對應](../dotnet/map-stl-clr.md)，但此程序類似於所有的集合和容器.

### <a name="to-create-a-container-from-a-collection"></a>若要從集合中建立容器

1. 若要轉換的整個集合，建立 STL/CLR 容器，並將集合傳遞給建構函式。

   第一個範例示範此程序。

-或-

1. 藉由建立泛型的 STL/CLR 容器[collection_adapter](../dotnet/collection-adapter-stl-clr.md)物件。 此範本類別會做為引數的.NET 集合介面。 若要確認支援的介面，請參閱[collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)。

1. 將.NET 集合的內容複製到容器。 做法是使用 STL/CLR[演算法](../dotnet/algorithm-stl-clr.md)，或藉由反覆查看.NET 集合，並將複本的每個項目插入至 STL/CLR 容器。

   第二個範例示範此程序。

## <a name="example"></a>範例

在此範例中，我們會建立泛型<xref:System.Collections.Generic.List%601>並為其新增 5 個元素。 接著，我們建立`vector`使用的建構函式<xref:System.Collections.Generic.IEnumerable%601>做為引數。

```
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>範例

在此範例中，我們會建立泛型<xref:System.Collections.Generic.Dictionary%602>並為其新增 5 個元素。 接著，我們建立`collection_adapter`包裝<xref:System.Collections.Generic.Dictionary%602>作為簡單的 STL/CLR 容器。 最後，我們會建立`map`，並將複製的內容<xref:System.Collections.Generic.Dictionary%602>要`map`藉由反覆`collection_adapter`。 在此過程中，建立新的組使用`make_pair`函式，並插入新的組直接插入`map`。

```
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>另請參閱

[STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[如何：從 STL/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
