---
title: HOW TO：建立使用特定排程器原則的代理程式
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 5aac86801015549b5552b51c06a30f8398346a06
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257367"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>HOW TO：建立使用特定排程器原則的代理程式

代理程式是以非同步方式運作，與其他元件，以解決大型運算工作的應用程式元件。 代理程式通常會有設定的生命週期，並會維護狀態。

每個代理程式可以有唯一的應用程式的需求。 例如，代理程式，可讓使用者互動 （擷取輸入或顯示輸出） 可能需要更高的優先順序存取運算資源。 排程器原則可讓您控制管理工作時，會使用排程器的策略。 本主題示範如何建立使用特定排程器原則的代理程式。

如需使用自訂的排程器原則，以及非同步訊息區的基本範例，請參閱[How to:指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。

本主題會使用非同步代理程式庫，例如代理程式、 訊息區塊與訊息傳遞函式，從功能，來執行工作。 如需有關非同步代理程式程式庫的詳細資訊，請參閱[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)。

## <a name="example"></a>範例

下列範例會定義兩個類別衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md):`permutor`和`printer`。 `permutor`類別會計算指定輸入字串的所有排列。 `printer`類別進行將訊息列印至主控台。 `permutor`類別會執行密集運算作業，可能會使用所有可用的運算資源。 若要發揮作用，`printer`類別必須及時列印每個進度訊息。

若要提供`printer`類別的公平存取運算資源，此範例會使用所述的步驟[How to:管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)建立具有自訂原則的排程器執行個體。 自訂原則指定的執行緒優先順序最高的優先權類別。

為了說明使用自訂原則的排程器的優點，此範例會執行兩次整體的工作。 第一次，此範例會使用預設排程器來排定兩個工作。 然後此範例使用預設排程器來排程`permutor`物件，而排程器已排程的自訂原則`printer`物件。

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

雖然這兩組工作會產生相同的結果，會使用自訂原則的版本可讓`printer`執行提高權限的優先順序，讓它的行為更效果的物件。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`permute-strings.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc permute-strings.cpp**

## <a name="see-also"></a>另請參閱

[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)
