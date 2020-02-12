---
title: 如何：管理排程器執行個體
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141718"
---
# <a name="how-to-manage-a-scheduler-instance"></a>如何：管理排程器執行個體

排程器實例可讓您將特定排程原則與各種類型的工作負載產生關聯。 本主題包含兩個基本範例，示範如何建立和管理排程器實例。

範例會建立使用預設排程器原則的排程器。 如需建立使用自訂原則之排程器的範例，請參閱[如何：指定特定](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)排程器原則。

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>在您的應用程式中管理排程器實例

1. 建立[concurrency：： SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)物件，其中包含要使用之排程器的原則值。

1. 呼叫[concurrency：： CurrentScheduler：： create](reference/currentscheduler-class.md#create)方法或[concurrency：：排程器：： create](reference/scheduler-class.md#create)方法來建立排程器實例。

   如果您使用 `Scheduler::Create` 方法，當您需要將排程器與目前內容建立關聯時，請呼叫[concurrency：：排程器：： Attach](reference/scheduler-class.md#attach)方法。

1. 呼叫[CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw)函式，以建立非信號、自動重設事件物件的控制碼。

1. 將控制碼傳遞至您剛才建立的事件物件，以[concurrency：： CurrentScheduler：： RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[concurrency：：排程器：： RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 這會在終結排程器時註冊要設定的事件。

1. 執行您想要目前排程器排定的工作。

1. 呼叫[concurrency：： CurrentScheduler：:D etach](reference/currentscheduler-class.md#detach)方法來卸離目前的排程器，並將先前的排程器還原為目前的排程器。

   如果您使用 `Scheduler::Create` 方法，請呼叫[concurrency：：排程器：： release](reference/scheduler-class.md#release)方法，以遞減 `Scheduler` 物件的參考計數。

1. 將事件的控制碼傳遞給[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)函式，以等候排程器關閉。

1. 呼叫[CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函數，關閉事件物件的控制碼。

## <a name="example"></a>範例

下列程式碼顯示兩種管理排程器實例的方式。 每個範例會先使用預設排程器來執行工作，以列印出目前排程器的唯一識別碼。 然後，每個範例都會使用排程器實例，再次執行相同的工作。 最後，每個範例都會將預設排程器還原為目前的排程器，然後再執行一次工作。

第一個範例使用[concurrency：： CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別來建立排程器實例，並將它與目前的內容產生關聯。 第二個範例使用[concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器類別來執行相同的工作。 一般來說，`CurrentScheduler` 類別是用來處理目前的排程器。 當您想要控制排程器與目前內容相關聯的時間，或是當您想要將特定排程器與特定工作建立關聯時，第二個使用 `Scheduler` 類別的範例會很有用。

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

此範例會產生下列輸出。

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `scheduler-instance.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc scheduler-instance .cpp**

## <a name="see-also"></a>另請參閱

[排程器執行個體](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
