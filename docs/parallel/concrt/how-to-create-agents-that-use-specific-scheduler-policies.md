---
title: 如何：建立使用特定排程器原則的代理程式
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141740"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>如何：建立使用特定排程器原則的代理程式

Agent 是應用程式元件，可與其他元件以非同步方式運作，以解決較大型的運算工作。 代理程式通常會有設定的生命週期並維持狀態。

每個代理程式都有獨特的應用程式需求。 例如，可讓使用者互動的代理程式（抓取輸入或顯示輸出）可能需要更高優先順序的運算資源存取權。 排程器原則可讓您控制排程器在管理工作時所使用的策略。 本主題示範如何建立使用特定排程器原則的代理程式。

如需使用自訂排程器原則搭配非同步訊息區塊的基本範例，請參閱[如何：指定特定](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)排程器原則。

本主題使用來自非同步代理程式程式庫的功能，例如代理程式、訊息區塊和訊息傳遞函式，來執行工作。 如需非同步代理程式程式庫的詳細資訊，請參閱[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫。

## <a name="example"></a>範例

下列範例會定義衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)： `permutor` 和 `printer`的兩個類別。 `permutor` 類別會計算指定輸入字串的所有排列。 `printer` 類別會將進度訊息列印到主控台。 `permutor` 類別會執行需要大量運算的作業，這可能會使用所有可用的計算資源。 `printer` 類別必須及時列印每個進度訊息，才能發揮效用。

為了提供 `printer` 類別公平存取運算資源，此範例使用[如何：管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)排程器實例中所述的步驟，來建立具有自訂原則的排程器實例。 自訂原則會將執行緒優先順序指定為最高優先順序的類別。

為了說明使用具有自訂原則之排程器的優點，此範例會執行兩次整體工作。 此範例會先使用預設排程器來排定這兩項工作。 然後，此範例會使用預設排程器來排定 `permutor` 物件，以及具有自訂原則的排程器來排定 `printer` 物件。

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

此範例會產生下列輸出。

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

雖然這兩組工作會產生相同的結果，但使用自訂原則的版本可讓 `printer` 物件以較高的優先權執行，使其行為更 responsively。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `permute-strings.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc permute-strings .cpp**

## <a name="see-also"></a>另請參閱

[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)
