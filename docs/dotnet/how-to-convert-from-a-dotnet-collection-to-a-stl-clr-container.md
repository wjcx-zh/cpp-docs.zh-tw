---
title: 如何： 從.NET 集合轉換為 STL/CLR 容器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8b6469c035a1f0daca5c789525778aab1119c9f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>如何：從 .NET 集合轉換為 STL/CLR 容器
本主題說明如何將.NET 集合轉換成其對等的 STL/CLR 容器。 我們可以做為範例示範如何將轉換.NET<xref:System.Collections.Generic.List%601>至 STL/CLR[向量](../dotnet/vector-stl-clr.md)以及如何轉換為.NET<xref:System.Collections.Generic.Dictionary%602>至 STL/CLR[對應](../dotnet/map-stl-clr.md)，但程序是類似的所有集合和容器.  
  
### <a name="to-create-a-container-from-a-collection"></a>若要從集合中建立容器  
  
1.  若要將整個集合，建立 STL/CLR 容器並傳遞給建構函式的集合。  
  
     第一個範例示範此程序。  
  
 -或-  
  
1.  藉由建立建立泛型 STL/CLR 容器[collection_adapter](../dotnet/collection-adapter-stl-clr.md)物件。 此樣板類別做為引數，採用.NET 集合介面。 若要確認支援的介面，請參閱[collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)。  
  
2.  將.NET 集合的內容複製到容器。 這可以經由使用 STL/CLR[演算法](../dotnet/algorithm-stl-clr.md)，或由反覆查看.NET 集合並將插入 STL/CLR 容器中的每個項目的複本。  
  
     第二個範例示範此程序。  
  
## <a name="example"></a>範例  
 在此範例中，我們會建立一般<xref:System.Collections.Generic.List%601>和 5 的項目加入。 接著，我們建立`vector`使用的建構函式<xref:System.Collections.Generic.IEnumerable%601>做為引數。  
  
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
 在此範例中，我們會建立一般<xref:System.Collections.Generic.Dictionary%602>和 5 的項目加入。 接著，我們建立`collection_adapter`包裝<xref:System.Collections.Generic.Dictionary%602>為簡單的 STL/CLR 容器。 最後，我們建立`map`複製的內容和<xref:System.Collections.Generic.Dictionary%602>至`map`重複`collection_adapter`。 在此過程中，建立新的組使用`make_pair`函式，並插入直接將新的組`map`。  
  
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
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)   
 [配接器 (STL/CLR)](../dotnet/adapter-stl-clr.md)   
 [如何：從 STL/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)