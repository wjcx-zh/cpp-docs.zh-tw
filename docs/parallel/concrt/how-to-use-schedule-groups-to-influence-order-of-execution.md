---
title: 如何： 使用排程群組來影響執行順序 |Microsoft 文件
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
ms.openlocfilehash: c41617f562a0abefdecf74d52e7a886ad6326f9e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691192"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用排程群組來影響執行順序
並行執行階段，工作都會排定的順序不具決定性。 不過，您可以使用排程的原則來影響執行工作順序。 本主題示範如何使用排程群組，並搭配[concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)排程器原則來影響執行工作順序。  

  
 此範例會執行一組工作兩次，各有不同的排程原則。 這兩個原則限制為兩個處理資源的最大數目。 第一個回合使用`EnhanceScheduleGroupLocality`原則，預設值，且第二個回合使用`EnhanceForwardProgress`原則。 在下`EnhanceScheduleGroupLocality`原則，排程器執行的所有工作排程群組中每個工作完成或直到。 在下`EnhanceForwardProgress`原則，排程器會移到下一個排程群組中循環配置資源方式在一個工作完成後，或者會產生。  
  
 當每個排程群組會包含相關的工作，`EnhanceScheduleGroupLocality`原則通常會導致更佳的效能因為快取位置會保留工作之間。 `EnhanceForwardProgress`原則允許往前進行的工作和您需要排程在排程群組之間的公平性時很有用。  
  
## <a name="example"></a>範例  
 這個範例會定義`work_yield_agent`類別，衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `work_yield_agent`類別執行的工作單位、 會產生目前的內容，和接著執行另一個工作單位。 代理程式會使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)合作方式產生目前內容，以便在其他內容中執行的函式。  
  
 這個範例會建立四個`work_yield_agent`物件。 為了說明如何設定排程器原則來影響代理程式執行的順序，範例會將前兩個代理程式與一個排程群組和其他兩個代理程式使用另一個排程群組。 此範例會使用[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法來建立[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。 範例會執行所有的四個代理程式兩次，每次都會使用不同的排程原則。  
  
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
  
 這兩項原則會產生相同的事件順序。 不過，此原則，會使用`EnhanceScheduleGroupLocality`啟動屬於第一個排程群組屬於第二個群組的代理程式啟動前兩個代理程式。 使用原則`EnhanceForwardProgress`啟動一個代理程式，從第一個群組，然後啟動第二個群組中的 第一個代理程式。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`scheduling-protocol.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 排程-protocol.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [排程群組](../../parallel/concrt/schedule-groups.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

