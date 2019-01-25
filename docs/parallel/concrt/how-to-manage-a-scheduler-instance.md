---
title: HOW TO：管理排程器執行個體
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: d8e79f7c132abd8e43f661f4dc7c7bb758cb2a6d
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893986"
---
# <a name="how-to-manage-a-scheduler-instance"></a>HOW TO：管理排程器執行個體

排程器執行個體可讓您關聯各種類型的工作負載的特定排程的原則。 本主題包含兩個基本的範例，示範如何建立和管理排程器執行個體。

範例會建立使用預設排程器原則的排程器。 如需建立排程器的範例會使用自訂原則，請參閱[How to:指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>若要管理您的應用程式中的排程器執行個體

1. 建立[schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)物件，其中包含原則值要使用的排程器。

1. 呼叫[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法或[scheduler](reference/scheduler-class.md#create)方法，以建立排程器執行個體。

   如果您使用`Scheduler::Create`方法中，呼叫[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法時您必須將與目前內容關聯的排程器。

1. 呼叫[CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa)函式來建立未收到信號、 自動重設事件物件的控制代碼。

1. 將控制代碼傳遞至您剛才建立的事件物件[concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 這會註冊事件時終結排程器設定。

1. 執行您想要排程的目前排程器工作。

1. 呼叫[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)卸離目前的排程器，並還原先前的排程器與目前的方法。

   如果您使用`Scheduler::Create`方法中，呼叫[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法，以遞減參考計數的`Scheduler`物件。

1. 將控制代碼傳遞至事件，以[WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)等待關閉的排程器的函式。

1. 呼叫[CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle)函式來關閉事件物件的控制代碼。

## <a name="example"></a>範例

下列程式碼示範兩種方式管理排程器執行個體。 第一次，每個範例會使用預設排程器來執行會印出目前的排程器的唯一識別碼的工作。 每個範例則使用排程器執行個體再次執行相同的工作。 最後，每個範例會還原為目前的預設排程器，並執行一次的工作。

第一個範例會使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別來建立排程器執行個體，並將它與目前內容產生關聯。 第二個範例會使用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)類別來執行相同的工作。 一般而言，`CurrentScheduler`類別用來處理目前的排程器。 第二個範例中，它會使用`Scheduler`類別中，當您想要控制當排程器是與目前內容相關聯，或當您想要特定排程器相關聯的特定工作時非常有用。

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

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`scheduler-instance.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 排程器 instance.cpp**

## <a name="see-also"></a>另請參閱

[排程器執行個體](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

