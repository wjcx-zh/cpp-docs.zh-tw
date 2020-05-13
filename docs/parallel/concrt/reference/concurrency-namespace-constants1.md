---
title: 併發命名空間常量
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::AgentEventGuid
- concrt/concurrency::COOPERATIVE_TIMEOUT_INFINITE
- concrt/concurrency::COOPERATIVE_WAIT_TIMEOUT
- concrt/concurrency::ConcRTEventGuid
- concrt/concurrency::ConcRT_ProviderGuid
- concrt/concurrency::INHERIT_THREAD_PRIORITY
- concrt/concurrency::LockEventGuid
- concrt/concurrency::PPLParallelForEventGuid
- concrt/concurrency::PPLParallelForeachEventGuid
- concrt/concurrency::ResourceManagerEventGuid
- concrt/concurrency::ScheduleGroupEventGuid
- concrt/concurrency::VirtualProcessorEventGuid
ms.assetid: 6f81fc4c-b10c-479e-8717-9c292360d5a0
ms.openlocfilehash: 8e9254e966f480538d80721bcfd86d301fac8d09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372739"
---
# <a name="concurrency-namespace-constants"></a>併發命名空間常量

||||
|-|-|-|
|[代理事件](#agenteventguid)|[CONCRT_RM_VERSION_1](#concrt_rm_version_1)|[COOPERATIVE_TIMEOUT_INFINITE](#cooperative_timeout_infinite)|
|[COOPERATIVE_WAIT_TIMEOUT](#cooperative_wait_timeout)|[喬雷埃文吉德](#choreeventguid)|[康克RT事件吉德](#concrteventguid)|
|[ConcRT_ProviderGuid](#concrt_providerguid)|[內容文事件吉德](#contexteventguid)|[INHERIT_THREAD_PRIORITY](#inherit_thread_priority)|
|[洛克·埃金吉](#lockeventguid)|[最大執行資源](#maxexecutionresources)|[PPLParallelforEventGuid](#pplparallelforeventguid)|
|[PPLParallelforeach 事件](#pplparallelforeacheventguid)|[PPLParallelInvokeEventGuid](#pplparallelinvokeeventguid)|[資源經理](#resourcemanagereventguid)|
|[排程群組事件](#schedulegroupeventguid)|[排程活動](#schedulereventguid)|[虛擬處理器事件](#virtualprocessoreventguid)|

## <a name="agenteventguid"></a><a name="agenteventguid"></a>代理事件

分類 GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07})，描述在並行執行階段由代理程式程式庫引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID AgentEventGuid = {0xb9b5b78c, 0x713, 0x4898, { 0xa2, 0x1a, 0xc6, 0x79, 0x49, 0xdc, 0xed, 0x7 } };
```

## <a name="choreeventguid"></a><a name="choreeventguid"></a>喬雷埃文吉德

分類 GUID，描述直接與工作相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID ChoreEventGuid =
    { 0x7E854EC7, 0xCDC4, 0x405a, { 0xB5, 0xB2, 0xAA, 0xF7, 0xC9, 0xE7, 0xD4, 0x0C } };
```

### <a name="remarks"></a>備註

此類別的事件當前不由併發運行時觸發。

## <a name="concrt_providerguid"></a><a name="concrt_providerguid"></a>ConcRT_ProviderGuid

目前執行階段的 ETW 提供者 GUID。

```cpp
const __declspec(selectany) GUID ConcRT_ProviderGuid =
    { 0xF7B697A3, 0x4DB5, 0x4d3b, { 0xBE, 0x71, 0xC4, 0xD2, 0x84, 0xE6, 0x59, 0x2F } };
```

## <a name="concrt_rm_version_1"></a><a name="concrt_rm_version_1"></a>CONCRT_RM_VERSION_1

指出支援 Visual Studio 2010 中定義的資源管理員介面。

```cpp
const unsigned int CONCRT_RM_VERSION_1 = 0x00010000;
```

## <a name="concrteventguid"></a><a name="concrteventguid"></a>康克RT事件吉德

分類 GUID，描述其他分類未特定描述之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID ConcRTEventGuid =
    { 0x72B14A7D, 0x704C, 0x423e, { 0x92, 0xF8, 0x7E, 0x6D, 0x64, 0xBC, 0xB9, 0x2A } };
```

### <a name="remarks"></a>備註

此類別的事件當前不由併發運行時觸發。

## <a name="cooperative_timeout_infinite"></a><a name="cooperative_timeout_infinite"></a>COOPERATIVE_TIMEOUT_INFINITE

值，表示等候應該永遠不會逾時。

```cpp
const unsigned int COOPERATIVE_TIMEOUT_INFINITE = (unsigned int)-1;
```

## <a name="cooperative_wait_timeout"></a><a name="cooperative_wait_timeout"></a>COOPERATIVE_WAIT_TIMEOUT

值，表示等候已逾時。

```cpp
const size_t COOPERATIVE_WAIT_TIMEOUT = SIZE_MAX;
```

## <a name="contexteventguid"></a><a name="contexteventguid"></a>內容文事件吉德

分類 GUID，描述直接與內容相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID ContextEventGuid =
    { 0x5727A00F, 0x50BE, 0x4519, { 0x82, 0x56, 0xF7, 0x69, 0x98, 0x71, 0xFE, 0xCB } };
```

## <a name="inherit_thread_priority"></a><a name="inherit_thread_priority"></a>INHERIT_THREAD_PRIORITY

原則機碼 `ContextPriority` 的特殊值，代表排程器中所有內容的執行緒優先順序應該與建立排程器之執行緒的優先順序相同。

```cpp
const unsigned int INHERIT_THREAD_PRIORITY = 0x0000F000;
```

## <a name="lockeventguid"></a><a name="lockeventguid"></a>洛克·埃金吉

分類 GUID，描述直接與鎖定相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID LockEventGuid =
    { 0x79A60DC6, 0x5FC8, 0x4952, { 0xA4, 0x1C, 0x11, 0x63, 0xAE, 0xEC, 0x5E, 0xB8 } };
```

### <a name="remarks"></a>備註

此類別的事件當前不由併發運行時觸發。

## <a name="maxexecutionresources"></a><a name="maxexecutionresources"></a>最大執行資源

原則機碼 `MinConcurrency` 和 `MaxConcurrency` 的特殊值。 預設值是在沒有其他條件約束的情況下，電腦上的硬體執行緒數目。

```cpp
const unsigned int MaxExecutionResources = 0xFFFFFFFF;
```

## <a name="pplparallelforeventguid"></a><a name="pplparallelforeventguid"></a>PPLParallelforEventGuid

分類 GUID，描述直接與 `parallel_for` 函式使用方式相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelForEventGuid =
    { 0x31c8da6b, 0x6165, 0x4042, { 0x8b, 0x92, 0x94, 0x9e, 0x31, 0x5f, 0x4d, 0x84 } };
```

## <a name="pplparallelforeacheventguid"></a><a name="pplparallelforeacheventguid"></a>PPLParallelforeach 事件

分類 GUID，描述直接與 `parallel_for_each` 函式使用方式相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelForeachEventGuid =
    { 0x5cb7d785, 0x9d66, 0x465d, { 0xba, 0xe1, 0x46, 0x11, 0x6, 0x1b, 0x54, 0x34 } };
```

## <a name="pplparallelinvokeeventguid"></a><a name="pplparallelinvokeeventguid"></a>PPLParallelInvokeEventGuid

分類 GUID，描述直接與 `parallel_invoke` 函式使用方式相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelInvokeEventGuid =
    { 0xd1b5b133, 0xec3d, 0x49f4, { 0x98, 0xa3, 0x46, 0x4d, 0x1a, 0x9e, 0x46, 0x82 } };
```

## <a name="resourcemanagereventguid"></a><a name="resourcemanagereventguid"></a>資源經理

分類 GUID，描述直接與資源管理員相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID ResourceManagerEventGuid =
    { 0x2718D25B, 0x5BF5, 0x4479, { 0x8E, 0x88, 0xBA, 0xBC, 0x64, 0xBD, 0xBF, 0xCA } };
```

### <a name="remarks"></a>備註

此類別的事件當前不由併發運行時觸發。

## <a name="schedulegroupeventguid"></a><a name="schedulegroupeventguid"></a>排程群組事件

分類 GUID，描述直接與排程群組相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID ScheduleGroupEventGuid =
    { 0xE8A3BF1F, 0xA86B, 0x4390, { 0x9C, 0x60, 0x53, 0x90, 0xB9, 0x69, 0xD2, 0x2C } };
```

### <a name="remarks"></a>備註

此類別的事件當前不由併發運行時觸發。

## <a name="schedulereventguid"></a><a name="schedulereventguid"></a>排程活動

分類 GUID，描述直接與排程器活動相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID SchedulerEventGuid =
    { 0xE2091F8A, 0x1E0A, 0x4731, { 0x84, 0xA2, 0x0D, 0xD5, 0x7C, 0x8A, 0x52, 0x61 } };
```

## <a name="virtualprocessoreventguid"></a><a name="virtualprocessoreventguid"></a>虛擬處理器事件

分類 GUID，描述直接與虛擬處理器相關之並行執行階段引發的 ETW 事件。

```cpp
const __declspec(selectany) GUID VirtualProcessorEventGuid =
    { 0x2f27805f, 0x1676, 0x4ecc, { 0x96, 0xfa, 0x7e, 0xb0, 0x9d, 0x44, 0x30, 0x2f } };
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
