---
title: 如何：指定特定排程器原則
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: 1334b8dcf8b6615120d4be8db8530af60df9d668
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520025"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>如何：指定特定排程器原則

排程器原則可讓您控制管理工作時，會使用排程器的策略。 本主題說明如何使用排程器原則，來增加的工作，會列印到主控台的進度列指示器的執行緒優先權。

如需使用自訂的排程器原則，以及非同步代理程式的範例，請參閱 <<c0> [ 如何： 建立代理程式，使用特定排程器原則](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。

## <a name="example"></a>範例

下列範例會以平行方式執行兩項工作。 第一個工作會計算 n<sup>th</sup> Fibonacci 數字。 第二項工作會列印到主控台的進度列指示器。

第一項工作會使用遞迴分解，計算 Fibonacci 數字。 也就是說，每個工作以遞迴方式建立子工作，來計算整體的結果。 使用遞迴分解的工作可能會使用所有可用的資源，因而佔用其他工作。 在此範例中，將進度列指示器的列印工作可能不會收到即時運算資源的存取。

若要提供列印進度訊息公平存取運算資源的工作，此範例會使用所述的步驟[如何： 管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)建立具有自訂原則的排程器執行個體。 自訂原則指定的執行緒優先順序最高的優先權類別。

這個範例會使用[concurrency:: call](../../parallel/concrt/reference/call-class.md)並[concurrency:: timer](../../parallel/concrt/reference/timer-class.md)類別來列印的進度列指示器。 這些類別都有參考其建構函式版本[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)排程它們的物件。 此範例會使用預設排程器來排程計算 Fibonacci 數字和排程可列印的進度列指示器的工作排程器執行個體的工作。

為了說明使用自訂原則的排程器的優點，此範例會執行兩次整體的工作。 第一次，此範例會使用預設排程器來排定兩個工作。 然後此範例會使用預設排程器來排定第一項工作，並具有自訂原則來排程第二項工作的排程器。

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

此範例會產生下列輸出。

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

雖然這兩組工作會產生相同的結果，會使用自訂原則的版本可讓列印進度列指示器，讓它更效果的行為，在更高的優先權執行的工作。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`scheduler-policy.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 排程器 policy.cpp**

## <a name="see-also"></a>另請參閱

[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

