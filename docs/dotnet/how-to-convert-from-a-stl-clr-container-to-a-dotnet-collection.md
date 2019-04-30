---
title: HOW TO：從 STL/CLR 容器轉換為.NET 集合
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: cf67e362751dd164916cc94cd644d55110d88a5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387522"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>HOW TO：從 STL/CLR 容器轉換為.NET 集合

本主題說明如何將 STL/CLR 容器轉換成其對等的.NET 集合。 舉例來說，我們會示範如何將 STL/CLR[向量](../dotnet/vector-stl-clr.md).net<xref:System.Collections.Generic.ICollection%601>以及如何轉換 STL/CLR[地圖](../dotnet/map-stl-clr.md).net <xref:System.Collections.Generic.IDictionary%602>，但此程序類似於所有集合和容器。

### <a name="to-create-a-collection-from-a-container"></a>若要從容器中建立集合

1. 使用下列方法之一：

   - 若要將轉換為容器的一部分，請呼叫[make_collection](../dotnet/make-collection-stl-clr.md)函式，並傳遞要複製到.NET 集合的開始迭代器和 STL/CLR 容器的結尾迭代器。 這個範本函式會採用 STL/CLR 迭代器作為範本引數。 第一個範例會示範這個方法。

   - 若要轉換的整個容器，轉型至適當的.NET 集合介面或介面的集合容器。 第二個範例會示範這個方法。

## <a name="example"></a>範例

在此範例中，我們會建立 STL/CLR`vector`並為其新增 5 個元素。 然後，我們藉由呼叫，會在建立.NET 集合時`make_collection`函式。 最後，我們會顯示新建立的集合的內容。

```
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

## <a name="example"></a>範例

在此範例中，我們會建立 STL/CLR`map`並為其新增 5 個元素。 接著，我們建立一個.NET<xref:System.Collections.Generic.IDictionary%602>並指派`map`直接。 最後，我們會顯示新建立的集合的內容。

```
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
