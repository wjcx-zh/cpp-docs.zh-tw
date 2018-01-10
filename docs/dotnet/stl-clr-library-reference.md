---
title: "STL/CLR 程式庫參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aecb7c509fc1b072086a8772c3430c43b67350be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stlclr-library-reference"></a>STL/CLR 程式庫參考
STL/CLR 程式庫是子集的 c + + 標準程式庫與 c + + 和.NET Framework common language runtime (CLR) 搭配使用的封裝。 STL/CLR，您可以使用所有的容器、 迭代器和受管理的環境中的標準程式庫的演算法。  
  
 若要使用 STL/CLR:  
  
-   包含標頭從**cliext**包含子目錄，而不是一般的 c + + 標準程式庫對等項目。  
  
-   程式庫以限定名稱`cliext::`而不是`std::`。  
  
 它會使用跨組件的.NET 組件的案例中的泛型類型和介面，公開 STL/CLR **Microsoft.VisualC.STLCLR.dll**。 這個 DLL 隨附於.NET Framework 3.5。 如果您轉散發使用 STL/CLR 的應用程式，您必須在包含.NET Framework 3.5，以及使用您的專案，安裝專案的相依性區段中的任何其他 Visual c + + 程式庫。  
  
## <a name="in-this-section"></a>本節內容  
 [cliext 命名空間](../dotnet/cliext-namespace.md)  
 討論包含所有類型的 STL/CLR 程式庫的命名空間。  
  
 [STL/CLR 容器](../dotnet/stl-clr-containers.md)  
 提供 c + + 標準程式庫，包括容器項目、 可以插入的項目類型和擁有權問題需求中找到的容器的概觀。  
  
 [STL/CLR 容器項目的需求](../dotnet/requirements-for-stl-clr-container-elements.md)  
 描述 c + + 標準程式庫容器所插入的所有參考類型的最低需求。  
  
 [如何：從 .NET 集合轉換為 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 描述如何將.NET 集合轉換為 STL/CLR 容器。  
  
 [如何：從 STL/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 描述如何將 STL/CLR 容器轉換為.NET 集合。  
  
 [如何：從組件公開 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 示範如何顯示 c + + 組件中撰寫的數個 STL/CLR 容器項目。  
  
 此外，本節也說明 STL/CLR 的下列元件：  
  
|||  
|-|-|  
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|  
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|  
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|  
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|  
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|  
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|  
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|  
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|  
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|  
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)