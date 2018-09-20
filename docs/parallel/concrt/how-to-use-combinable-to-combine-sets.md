---
title: 如何： 使用 combinable 結合集合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69f48ed099fe033ba1847a3414ed8e5c5ce88f71
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433669"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用可組合的類別結合集合

本主題說明如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別來計算一組質數。

## <a name="example"></a>範例

下列範例會計算一組質數的兩倍。 每個計算儲存的結果[std::bitset](../../standard-library/bitset-class.md)物件。 此範例先計算循序集合，然後再計算以平行方式設定。 這個範例也會將執行這兩項計算所需的時間列印到主控台。

這個範例會使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法，`combinable`物件來產生執行緒區域集合。 然後它會使用[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)結合成最終集合的執行緒區域集合的方法。

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`parallel-combine-primes.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行結合 primes.cpp**

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 類別](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable:: combine_each 方法](reference/combinable-class.md#combine_each)

