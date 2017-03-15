---
title: "STL/CLR 程式庫參考 | Microsoft Docs"
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
  - "cliext 目錄"
  - "STL/CLR 程式庫"
  - "STL/CLR, 轉散發"
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# STL/CLR 程式庫參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 程式庫是「標準樣板程式庫」\( Standard Template Library，STL\)，也就是 Standard C\+\+ 程式庫之子集的封裝，可以搭配 C\+\+ 與 .NET Framework Common Language Runtime \(CLR\) 使用。  有了 STL\/CLR，您就可以在 Managed 環境中使用 STL 的所有容器、Iterator 及演算法。  
  
 若要使用 STL\/CLR：  
  
-   包含來自 **cliext** 包含子目錄的標頭，而不是一般 Standard C\+\+ 程式庫的對應項。  
  
-   用來限定程式庫名稱的是 `cliext::` 而不是 `std::`。  
  
 STL\/CLR 會公開其在 .NET 組件 **Microsoft.VisualC.STLCLR.dll** 中用於跨組件情節的泛型類型和介面。  這個 DLL 是包含在 .NET Framework 3.5 中。  如果您要轉散發使用 STL\/CLR 的應用程式，您需要將 .NET Framework 3.5 以及專案使用的任何其他 Visual C\+\+ 程式庫包含在安裝專案的相依性區段中。  
  
## 在本節中  
 [cliext 命名空間](../dotnet/cliext-namespace.md)  
 討論包含 STL\/CLR 程式庫的所有類型的命名空間。  
  
 [STL\/CLR 容器](../dotnet/stl-clr-containers.md)  
 提供 Standard C\+\+ 程式庫內含之容器的概觀，包括容器項目需求、可插入之項目的類型以及擁有權問題。  
  
 [STL\/CLR 容器項目的需求](../dotnet/requirements-for-stl-clr-container-elements.md)  
 描述插入 STL 容器的所有參考類型的最低需求。  
  
 [如何：從 .NET 集合轉換為 STL\/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 描述如何將 .NET 集合轉換為 STL\/CLR 容器。  
  
 [如何：從 STL\/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 描述如何將 STL\/CLR 容器轉換為 .NET 集合。  
  
 [如何：從組件公開 STL\/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 說明如何在顯示數個以 C\+\+ 組件撰寫之 STL\/CLR 容器的項目。  
  
 此外，本節也會說明下列 STL\/CLR 元件：  
  
|||  
|-|-|  
|[adapter](../dotnet/adapter-stl-clr.md)|[algorithm](../dotnet/algorithm-stl-clr.md)|  
|[deque](../dotnet/deque-stl-clr.md)|[for each、in](../dotnet/for-each-in.md)|  
|[functional](../dotnet/functional-stl-clr.md)|[hash\_map](../dotnet/hash-map-stl-clr.md)|  
|[hash\_multimap](../dotnet/hash-multimap-stl-clr.md)|[hash\_multiset](../dotnet/hash-multiset-stl-clr.md)|  
|[hash\_set](../dotnet/hash-set-stl-clr.md)|[list](../dotnet/list-stl-clr.md)|  
|[map](../dotnet/map-stl-clr.md)|[multimap](../dotnet/multimap-stl-clr.md)|  
|[multiset](../dotnet/multiset-stl-clr.md)|[數值](../dotnet/numeric-stl-clr.md)|  
|[priority\_queue](../dotnet/priority-queue-stl-clr.md)|[queue](../dotnet/queue-stl-clr.md)|  
|[set](../dotnet/set-stl-clr.md)|[堆疊](../dotnet/stack-stl-clr.md)|  
|[utility](../dotnet/utility-stl-clr.md)|[向量](../dotnet/vector-stl-clr.md)|  
  
## 請參閱  
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)