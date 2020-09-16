---
title: 如何：從 .NET 集合轉換為 STL/CLR 容器
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: a7b2ee94f02e663690287ecfa6bc8a7230830a95
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686453"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>如何：從 .NET 集合轉換為 STL/CLR 容器

本主題說明如何將 .NET 集合轉換成其對等的 STL/CLR 容器。 舉例來說，我們會示範如何將 .NET 轉換成 <xref:System.Collections.Generic.List%601> stl/clr [向量](../dotnet/vector-stl-clr.md) ，以及如何將 .NET 轉換成 <xref:System.Collections.Generic.Dictionary%602> stl/clr [map](../dotnet/map-stl-clr.md)，但是所有集合和容器的程式都很類似。

### <a name="to-create-a-container-from-a-collection"></a>從集合建立容器

1. 若要轉換整個集合，請建立 STL/CLR 容器，並將集合傳遞至該函式。

   第一個範例會示範此程式。

-或-

1. 藉由建立 [collection_adapter](../dotnet/collection-adapter-stl-clr.md) 物件，建立泛型 STL/CLR 容器。 此範本類別會將 .NET 集合介面視為引數。 若要確認支援的介面，請參閱 [collection_adapter (STL/CLR) ](../dotnet/collection-adapter-stl-clr.md)。

1. 將 .NET 集合的內容複寫到容器。 這可以藉由使用 STL/CLR [演算法](../dotnet/algorithm-stl-clr.md)來完成，或逐一查看 .net 集合，並將每個元素的複本插入 STL/clr 容器中。

   第二個範例會示範此程式。

## <a name="examples"></a>範例

在此範例中，我們會建立泛型 <xref:System.Collections.Generic.List%601> 並將5個元素加入其中。 然後，我們 `vector` 會使用接受 <xref:System.Collections.Generic.IEnumerable%601> 做為引數的函式來建立。

```cpp
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

在此範例中，我們會建立泛型 <xref:System.Collections.Generic.Dictionary%602> 並將5個元素加入其中。 接著，我們會建立， `collection_adapter` 以將 <xref:System.Collections.Generic.Dictionary%602> 當作簡單的 STL/CLR 容器來包裝。 最後，我們會建立，並逐一查看，將的 `map` 內容複寫 <xref:System.Collections.Generic.Dictionary%602> 到 `map` `collection_adapter` 。 在這個過程中，我們會使用函式來建立新的配對 `make_pair` ，並將新的配對直接插入至 `map` 。

```cpp
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
