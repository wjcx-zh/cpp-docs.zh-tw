---
title: 如何： 使用排程群組來影響執行順序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55417f1d72d6bd3e111a89f4b28f783543101b6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415872"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用排程群組來影響執行順序

並行執行階段，工作會排程的順序是不具決定性的。 不過，您可以使用排程的原則來影響執行工作順序。 本主題說明如何使用排程群組，並搭配[concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)排程器原則來影響執行工作順序。

此範例會執行一組工作兩次，各有不同的排程原則。 這兩個原則限制為兩個處理資源的數目上限。 第一次執行會使用`EnhanceScheduleGroupLocality`原則，這是預設值，以及第二次執行使用`EnhanceForwardProgress`原則。 在下`EnhanceScheduleGroupLocality`原則，排程器的所有工作排程在群組中執行每項工作完成，或會產生之前。 在下`EnhanceForwardProgress`原則，排程器將移至下一個排程群組以循環配置資源方式只是一項工作完成或產生之後。

當每個排程群組包含相關的工作，`EnhanceScheduleGroupLocality`原則通常會導致更佳的效能因為快取位置會保留在工作之間。 `EnhanceForwardProgress`原則可讓工作繼續進行，並當您需要跨排程群組的排程，公平性時非常有用。

## <a name="example"></a>範例

這個範例會定義`work_yield_agent`類別，衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `work_yield_agent`類別執行的工作單位、 產生目前的內容，和接著執行另一個工作單位。 代理程式會使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)以合作方式產生目前的內容，以便在其他內容中執行的函式。

這個範例會建立四個`work_yield_agent`物件。 若要說明如何設定排程器原則來影響執行代理程式的順序，，範例會將前兩個代理程式與一個排程群組和其他兩個代理程式與另一個排程群組。 此範例會使用[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法來建立[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。 這個範例會執行所有的四個代理程式兩次，每次都有不同的排程原則。

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

此範例會產生下列輸出。

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

這兩項原則會產生相同的事件順序。 不過，此原則，會使用`EnhanceScheduleGroupLocality`啟動這兩個代理程式之前啟動的代理程式是第二個群組的一部分，會第一個排程群組的一部分。 使用原則`EnhanceForwardProgress`從第一個群組開始一個代理程式，然後啟動 第二個群組中的 第一個代理程式。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`scheduling-protocol.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 排程-protocol.cpp**

## <a name="see-also"></a>另請參閱

[排程群組](../../parallel/concrt/schedule-groups.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

