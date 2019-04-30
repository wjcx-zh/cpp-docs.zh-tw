---
title: STL/CLR 程式庫參考
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: b3c25a40fdb5bade02e112b13d16420b248a177f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384630"
---
# <a name="stlclr-library-reference"></a>STL/CLR 程式庫參考

STL/CLR 程式庫提供介面類似於C++搭配使用的標準程式庫容器C++和 .NET Framework common language runtime (CLR)。 STL/CLR 是完全分開的 Microsoft 實作C++標準程式庫。 STL/CLR 維護舊版支援，但不是會保持在最新的C++標準。 我們強烈建議使用原生[C++標準程式庫](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR，盡可能的容器。

若要使用 STL/CLR:

- 包含標頭**cliext**包含子目錄，而非平常C++標準程式庫對等項目。

- 程式庫以限定名稱`cliext::`而不是`std::`。

STL/CLR 程式庫提供的 STL 型介面與搭配使用C++和.NET Framework common language runtime (CLR)。 此程式庫會保留舊的支援，但不是會保持在最新的C++標準。 我們強烈建議使用原生[C++標準程式庫](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR 容器。

## <a name="in-this-section"></a>本節內容

[cliext 命名空間](../dotnet/cliext-namespace.md)<br/>
討論包含 STL/CLR 程式庫的所有類型的命名空間。

[STL/CLR 容器](../dotnet/stl-clr-containers.md)<br/>
提供位於容器的概觀C++標準程式庫，包括容器項目、 可插入的項目類型和擁有權問題的需求。

[STL/CLR 容器項目的需求](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
描述的所有參考型別插入的最低需求C++標準程式庫容器。

[如何：從 .NET 集合轉換為 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
描述如何將.NET 集合轉換為 STL/CLR 容器。

[如何：從 STL/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
描述如何將 STL/CLR 容器轉換為.NET 集合。

[如何：從組件公開 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
示範如何顯示數個以撰寫的 STL/CLR 容器項目C++組件。

此外，本節也會說明下列 STL/CLR 元件：

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

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
