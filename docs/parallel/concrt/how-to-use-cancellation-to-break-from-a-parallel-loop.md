---
title: 如何：使用取消來中斷平行迴圈圈
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142139"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>如何：使用取消來中斷平行迴圈圈

這個範例將示範如何使用取消來實作基本的平行搜尋演算法。

## <a name="example"></a>範例

下列範例會使用取消來搜尋陣列中的元素。 `parallel_find_any` 函式會使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法和[concurrency：： run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函數來搜尋包含指定值的位置。 當平行迴圈找到值時，它會呼叫[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法來取消未來的工作。

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

平行存取[：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法會同時運作。 因此，它不會以預先決定的順序來執行作業。 如果陣列包含值的多個實例，則結果可以是它的任何一個位置。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `parallel-array-search.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-array-search.cpp .cpp**

## <a name="see-also"></a>另請參閱

[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)
