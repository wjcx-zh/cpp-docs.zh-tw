---
title: HOW TO：使用取消來中斷平行迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 08f33a75bc5c5391333a2d9368d4ed6563e117c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346258"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>HOW TO：使用取消來中斷平行迴圈

這個範例將示範如何使用取消來實作基本的平行搜尋演算法。

## <a name="example"></a>範例

下列範例會使用取消來搜尋陣列中的項目。 `parallel_find_any`函式會使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法以及[concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函式來搜尋的位置，其中包含指定的值。 當平行迴圈找到值時，它會呼叫[concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel)方法來取消後續工作。

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法會並行運作。 因此，它不會執行作業以預先決定的順序。 如果陣列包含多個執行個體，結果可以是值的任一其位置。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`parallel-array-search.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行陣列 search.cpp**

## <a name="see-also"></a>另請參閱

[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)
