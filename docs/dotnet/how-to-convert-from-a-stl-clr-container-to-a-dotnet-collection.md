---
title: "如何： 從 STL/CLR 容器轉換為.NET 集合 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aa58c8db46d1443ca5b39449222cc22e31eafb5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>如何：從 STL/CLR 容器轉換為 .NET 集合
本主題示範如何將 STL/CLR 容器轉換成其對等的.NET 集合。 例如，我們會示範如何將轉換 STL/CLR[向量](../dotnet/vector-stl-clr.md)的.net<xref:System.Collections.Generic.ICollection%601>以及如何轉換 STL/CLR[對應](../dotnet/map-stl-clr.md)的.net <xref:System.Collections.Generic.IDictionary%602>，但程序是類似的所有集合和容器。  
  
### <a name="to-create-a-collection-from-a-container"></a>若要從容器中建立集合  
  
1.  使用下列方法之一：  
  
    -   若要將容器的一部分，呼叫[make_collection](../dotnet/make-collection-stl-clr.md)函式，並傳遞要複製到.NET 集合的迭代器，開始和結尾迭代器的 STL/CLR 容器。 這個範本函式會採用 STL/CLR 迭代器做為樣板引數。 第一個範例會示範這個方法。  
  
    -   若要轉換的整個容器，轉換到適當的.NET 集合介面或介面的集合容器。 第二個範例會示範這個方法。  
  
## <a name="example"></a>範例  
 在此範例中，我們會建立 STL/CLR`vector`和 5 的項目加入。 接著，我們建立為.NET 集合藉由呼叫`make_collection`函式。 最後，我們會顯示新建立的集合的內容。  
  
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
 在此範例中，我們會建立 STL/CLR`map`和 5 的項目加入。 接著，我們建立.NET<xref:System.Collections.Generic.IDictionary%602>並指派`map`直接。 最後，我們會顯示新建立的集合的內容。  
  
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
  
## <a name="see-also"></a>請參閱  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)   
 [如何： 從.NET 集合轉換為 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)