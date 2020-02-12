---
title: 如何：使用可組合的類別結合集合
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142122"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用可組合的類別結合集合

本主題說明如何使用[concurrency：：組合](../../parallel/concrt/reference/combinable-class.md)類別來計算質數集合。

## <a name="example"></a>範例

下列範例會計算兩次質數的集合。 每個計算會將結果儲存在[std：： bitset](../../standard-library/bitset-class.md)物件中。 此範例會先依序計算集合，然後以平行方式計算集合。 這個範例也會將執行這兩項計算所需的時間列印到主控台。

這個範例會使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法和 `combinable` 物件來產生執行緒區域集合。 然後，它會使用[concurrency：：組合：： combine_each](reference/combinable-class.md#combine_each)方法，將執行緒區域集合結合成最終集合。

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `parallel-combine-primes.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-combine-primes.cpp .cpp**

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 類別](../../parallel/concrt/reference/combinable-class.md)<br/>
[組合：： combine_each 方法](reference/combinable-class.md#combine_each)
