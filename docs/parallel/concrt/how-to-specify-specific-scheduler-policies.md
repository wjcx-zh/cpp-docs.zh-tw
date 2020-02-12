---
title: 如何：指定特定排程器原則
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: bd5edfbdf6b0fda9c7e327dab9538bbf6b5e4b12
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142443"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>如何：指定特定排程器原則

排程器原則可讓您控制排程器在管理工作時所使用的策略。 本主題說明如何使用排程器原則，增加將進度指示器列印到主控台之工作的執行緒優先順序。

如需搭配使用自訂排程器原則與非同步代理程式的範例，請參閱[如何：建立使用特定排程器原則的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)程式。

## <a name="example"></a>範例

下列範例會平行執行兩項工作。 第一個工作會計算第<sup>n 個</sup>的斐波上數位。 第二個工作會將進度指示器列印到主控台。

第一個工作會使用遞迴分解來計算斐波時數。 也就是說，每個工作會以遞迴方式建立子工作來計算整體結果。 使用遞迴分解的工作可能會使用所有可用的資源，進而使其他工作。 在此範例中，列印進度指示器的工作可能無法及時收到運算資源的存取權。

為了提供列印進度訊息公平存取運算資源的工作，此範例會使用[如何：管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)排程器實例中所述的步驟，來建立具有自訂原則的排程器實例。 自訂原則會將執行緒優先順序指定為最高優先順序的類別。

這個範例使用[concurrency：： call](../../parallel/concrt/reference/call-class.md)和[concurrency：： timer](../../parallel/concrt/reference/timer-class.md)類別來列印進度指示器。 這些類別具有其程式的版本，這些函式會參考會排程它們的[concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器物件。 此範例會使用預設排程器，排定計算斐波和排程器實例的工作，以排定列印進度指示器的工作。

為了說明使用具有自訂原則之排程器的優點，此範例會執行兩次整體工作。 此範例會先使用預設排程器來排定這兩項工作。 然後，此範例會使用預設排程器排定第一個工作，以及具有自訂原則的排程器來排定第二個工作。

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

此範例會產生下列輸出。

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

雖然這兩組工作會產生相同的結果，但使用自訂原則的版本可讓列印進度指示器的工作，以提升的優先權執行，使其行為更 responsively。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `scheduler-policy.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc scheduler-policy .cpp**

## <a name="see-also"></a>另請參閱

[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
