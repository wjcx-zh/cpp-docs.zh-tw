---
title: "如何：從 .NET 集合轉換為 STL/CLR 容器 | Microsoft Docs"
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
  - "STL/CLR, 從 .NET 集合轉換"
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從 .NET 集合轉換為 STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明如何將 .NET 集合升級為對等的 STL\/CLR 容器。  範例會顯示如何轉換 .NET <xref:System.Collections.Generic.List%601> 到 STL\/CLR [向量](../dotnet/vector-stl-clr.md) 以及如何轉換 .NET <xref:System.Collections.Generic.Dictionary%602> 到 STL\/CLR [導覽](../dotnet/map-stl-clr.md)，不過，程序為所有集合和容器是類似的。  
  
### 會從集合的容器。  
  
1.  若要轉換整個集合，建立 STL\/CLR 容器並傳遞集合至建構函式。  
  
     第一個範例示範這個程序。  
  
 \-或\-  
  
1.  藉由建立 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md) 物件建立泛型 STL\/CLR 容器。  這個類別會使用 .NET 集合介面做為引數。  要驗證的介面支援，請參閱 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)。  
  
2.  複製 .NET 集合的內容加入至容器。  使用 STL\/CLR [演算法](../dotnet/algorithm-stl-clr.md)，這可以完成，或逐一查看 .NET 集合和插入每個項目複製到 STL\/CLR 容器。  
  
     第二個範例示範這個程序。  
  
## 範例  
 在此範例中，我們建立泛型 <xref:System.Collections.Generic.List%601> 並將 5 個項目。  然後，我們建立 `vector` 使用以 <xref:System.Collections.Generic.IEnumerable%601> 做為引數的建構函式。  
  
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
  
  **cliext::vector 的內容如下:**  
**2**  
**3**  
**5**  
**7**  
**11**   
## 範例  
 在此範例中，我們建立泛型 <xref:System.Collections.Generic.Dictionary%602> 並將 5 個項目。  然後，我們建立 `collection_adapter` 包裝 <xref:System.Collections.Generic.Dictionary%602> 做為簡單 STL\/CLR 容器。  最後，我們建立 `map` 和 <xref:System.Collections.Generic.Dictionary%602> 的內容複製至 `map` 逐一查看 `collection_adapter`。  您可以使用 `make_pair` 函式，在這個程序中，我們會建立新的工作，並插入新對直接傳入 `map`。  
  
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
  
  **cliext::map 的內容如下:**  
**機碼: 0.00 值: 0**  
**機碼: 13.00 值: 13**  
**機碼: 22.00 值: 22**  
**機碼: 42.00 值: 42**  
**機碼: 74.00 值: 74**   
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)   
 [adapter](../dotnet/adapter-stl-clr.md)   
 [如何：從 STL\/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)