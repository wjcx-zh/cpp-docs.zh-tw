---
title: STL/CLR 程式庫參考
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: e6804dab814eca4ecc5fd23c74cbbb21eac3be77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839695"
---
# <a name="stlclr-library-reference"></a>STL/CLR 程式庫參考

STL/CLR 程式庫提供的介面類別似于 c + + 標準程式庫容器，可搭配 c + + 和 .NET Framework common language runtime (CLR) 使用。 STL/CLR 和 c + + 標準程式庫的 Microsoft 執行完全不同。 STL/CLR 會針對舊版支援進行維護，但不會以 c + + 標準保持最新狀態。 我們強烈建議盡可能使用原生 [c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md) 容器，而不是 STL/CLR。

若要使用 STL/CLR：

- 包含 **cliext** 包含子目錄中的標頭，而不是一般的 c + + 標準程式庫對應專案。

- 限定程式庫名稱， `cliext::` 而不是 `std::` 。

STL/CLR 程式庫提供類似 STL 的介面，可搭配 c + + 和 .NET Framework common language runtime (CLR) 使用。 此程式庫會針對舊版支援進行維護，但不會與 c + + 標準保持最新狀態。 我們強烈建議使用原生 [c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md) 容器，而不是 STL/CLR。

## <a name="in-this-section"></a>本節內容

[cliext 命名空間](../dotnet/cliext-namespace.md)<br/>
討論包含所有 STL/CLR 程式庫類型的命名空間。

[STL/CLR 容器](../dotnet/stl-clr-containers.md)<br/>
提供在 c + + 標準程式庫中找到之容器的總覽，包括容器元素的需求、可插入的元素類型，以及擁有權問題。

[STL/CLR 容器專案的需求](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
描述插入 c + + 標準程式庫容器的所有參考型別的最低需求。

[如何：從 .NET 集合轉換為 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
描述如何將 .NET 集合轉換為 STL/CLR 容器。

[如何：從 STL/CLR 容器轉換為 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
描述如何將 STL/CLR 容器轉換為 .NET 集合。

[如何：從元件公開 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
示範如何顯示以 c + + 元件撰寫的數個 STL/CLR 容器的元素。

此外，本節也描述 STL/CLR 的下列元件：

:::row:::
   :::column span="":::
      [`adapter` (STL/CLR) ](../dotnet/adapter-stl-clr.md)\
      [`algorithm` (STL/CLR) ](../dotnet/algorithm-stl-clr.md)\
      [`deque` (STL/CLR) ](../dotnet/deque-stl-clr.md)\
      [`for each`, `in`](../dotnet/for-each-in.md)\
      [`functional` (STL/CLR) ](../dotnet/functional-stl-clr.md)\
      [`hash_map` (STL/CLR) ](../dotnet/hash-map-stl-clr.md)\
      [`hash_multimap` (STL/CLR) ](../dotnet/hash-multimap-stl-clr.md)\
      [`hash_multiset` (STL/CLR) ](../dotnet/hash-multiset-stl-clr.md)\
      [`hash_set` (STL/CLR) ](../dotnet/hash-set-stl-clr.md)\
      [`list` (STL/CLR) ](../dotnet/list-stl-clr.md)\
   :::column-end:::
   :::column span="":::
      [`map` (STL/CLR) ](../dotnet/map-stl-clr.md)\
      [`multimap` (STL/CLR) ](../dotnet/multimap-stl-clr.md)\
      [`multiset` (STL/CLR) ](../dotnet/multiset-stl-clr.md)\
      [`numeric` (STL/CLR) ](../dotnet/numeric-stl-clr.md)\
      [`priority_queue` (STL/CLR) ](../dotnet/priority-queue-stl-clr.md)\
      [`queue` (STL/CLR) ](../dotnet/queue-stl-clr.md)\
      [`set` (STL/CLR) ](../dotnet/set-stl-clr.md)\
      [`stack` (STL/CLR) ](../dotnet/stack-stl-clr.md)\
      [`utility` (STL/CLR) ](../dotnet/utility-stl-clr.md)\
      [`vector` (STL/CLR) ](../dotnet/vector-stl-clr.md)\
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
