---
title: 如何：使用排程群組來影響執行順序
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 84829664603999893f32caab39af250059bf9788
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141922"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用排程群組來影響執行順序

在並行執行階段中，排程工作的順序不具決定性。 不過，您可以使用排程原則來影響工作執行的順序。 本主題說明如何搭配使用 schedule 群組與[concurrency：： SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)排程器原則，以影響工作執行的順序。

此範例會執行一組工作兩次，每個工作都有不同的排程原則。 這兩個原則會將處理資源的最大數目限制為兩個。 第一次執行會使用 `EnhanceScheduleGroupLocality` 的原則，這是預設值，而第二次執行則使用 `EnhanceForwardProgress` 原則。 在 `EnhanceScheduleGroupLocality` 原則下，排程器會在每個工作完成或產生之前，執行一個排程群組中的所有工作。 在 `EnhanceForwardProgress` 原則下，排程器會在一項工作完成或產生之後，以迴圈配置資源的方式移至下一個排程群組。

當每個排程群組包含相關的工作時，`EnhanceScheduleGroupLocality` 原則通常會導致效能提升，因為工作之間會保留快取位置。 `EnhanceForwardProgress` 原則可讓工作繼續進行，而且當您需要跨排程群組排定公平時，這會很有用。

## <a name="example"></a>範例

這個範例會定義衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)的 `work_yield_agent` 類別。 `work_yield_agent` 類別會執行工作單位、產生目前的內容，然後執行另一個工作單位。 代理程式會使用[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函式，以合作方式產生目前的內容，讓其他內容可以執行。

這個範例會建立四個 `work_yield_agent` 物件。 為了說明如何設定排程器原則來影響代理程式的執行順序，此範例會將前兩個代理程式與一個排程群組建立關聯，並將其他兩個代理程式與另一個排程群組產生關聯。 此範例使用[concurrency：： CurrentScheduler：： CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法來建立[Concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。 此範例會執行這四個代理程式兩次，每次都使用不同的排程原則。

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

這兩種原則都會產生相同的事件序列。 不過，使用 `EnhanceScheduleGroupLocality` 的原則，會在啟動屬於第二個群組的代理程式之前，先啟動屬於第一個排程群組的代理程式。 使用 `EnhanceForwardProgress` 的原則會從第一個群組啟動一個代理程式，然後啟動第二個群組中的第一個代理程式。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `scheduling-protocol.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc scheduling-protocol .cpp**

## <a name="see-also"></a>另請參閱

[排程群組](../../parallel/concrt/schedule-groups.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)
