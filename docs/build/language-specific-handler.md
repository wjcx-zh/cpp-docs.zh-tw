---
title: 語言特定處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 678f5695523751ebc1ef3c5dba2b63154b21833c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714944"
---
# <a name="language-specific-handler"></a>語言特定處理常式

每當設定旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER UNWIND_INFO 中有語言特定處理常式的相對位址。 上一節所述，語言特定處理常式稱為例外狀況處理常式中搜尋的一部分，或做為回溯的一部分。 它有下列原型：

```
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**Exception_record**提供例外狀況記錄，其具有標準 Win64 定義的指標。

**EstablisherFrame**是固定的堆疊配置，此函式的基底的位址。

**ContextRecord**點，以在引發例外狀況 （例外狀況處理常式案例中） 的時間或目前的例外狀況內容的 「 回溯 」 （在終止處理常式案例中） 的內容。

**DispatcherContext**指向此函式的發送器內容。 它有下列定義：

```
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** RIP 內此函式的值。 這是例外狀況的地址或處控制保留建立的函式的位址。 這是將用來判斷控制項是否在某些受防護的建構，這個函式內的 RIP (例如 __try 區塊\__finally /\__except 或\__finally /\___identifier)。

**將 ImageBase**是映像基底 （載入位址） 的模組，其中包含此函式，新增至函式項目中所使用的 32 位元位移並回溯記錄相對位址的資訊。

**FunctionEntry**供應器的指標 RUNTIME_FUNCTION 函式保留函式的項目，並回溯此函式的資訊映像基底相對位址。

**EstablisherFrame**是固定的堆疊配置，此函式的基底的位址。

**TargetIp**提供選擇性的指令位址會指定回溯的接續位址。 如果，則會忽略這個地址**EstablisherFrame**未指定。

**ContextRecord**指向例外狀況的內容，以供系統例外狀況分派/回溯程式碼。

**LanguageHandler**指向特定語言的語言處理常式呼叫。

**HandlerData**指向此函式的語言特有的處理常式資料。

## <a name="see-also"></a>另請參閱

[例外狀況處理 (x64)](../build/exception-handling-x64.md)