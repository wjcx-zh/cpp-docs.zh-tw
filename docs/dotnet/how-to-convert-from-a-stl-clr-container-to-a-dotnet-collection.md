---
title: "如何：從 STL/CLR 容器轉換為 .NET 集合 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STL/CLR 容器 [STL/CLR]"
  - "STL/CLR, 轉換為 .NET 集合"
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從 STL/CLR 容器轉換為 .NET 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題顯示如何轉換 STL\/CLR 容器升級為對等的 .NET 集合。  例如，我們示範如何轉換 STL\/CLR [vector](../dotnet/vector-stl-clr.md) 至 .NET <xref:System.Collections.Generic.ICollection%601> 以及如何轉換 STL\/CLR [map](../dotnet/map-stl-clr.md) 至 .NET，<xref:System.Collections.Generic.IDictionary%602>，但是程序為所有集合和容器是類似的。  
  
### 建立從容器的集合  
  
1.  請使用下列一種方法：  
  
    -   若要轉換一部分的容器，請呼叫 [make\_collection](../dotnet/make-collection-stl-clr.md) 函式來啟動 Iterator 和結尾將複製的 STL\/CLR 容器的 Iterator 為 .NET 集合。  這個樣板函式會採用 STL\/CLR Iterator 當做樣板引數使用。  第一個範例示範這個方法。  
  
    -   若要轉換整個容器，請轉換容器包含適當的 .NET 集合介面或介面集合。  第二個範例示範這個方法。  
  
## 範例  
 在此範例中，我們建立 STL\/CLR `vector` 並將 5 個項目加入其中。  然後，會呼叫 `make_collection` 函式建立 .NET 集合。  最後，會顯示新建立之集合的內容。  
  
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
  
  **System::Collections::Generic::ICollection 的內容如下:**  
**3**  
**5**  
**7**   
## 範例  
 在此範例中，我們建立 STL\/CLR `map` 並將 5 個項目加入其中。  然後，我們建立 .NET <xref:System.Collections.Generic.IDictionary%602> 並且將 `map` 直接指派給它。  最後，會顯示新建立之集合的內容。  
  
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
  
  **IDictionary 的內容如下:**  
**機碼: 0.00 值: 0**  
**機碼: 13.00 值: 13**  
**機碼: 22.00 值: 22**  
**機碼: 42.00 值: 42**  
**機碼: 74.00 值: 74**   
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)   
 [如何：從 .NET 集合轉換為 STL\/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)