---
title: 語言特定處理常式 |Microsoft 文件
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
ms.openlocfilehash: c6cbfbe6a9b98828a63fb4a092717bfab583e9a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="language-specific-handler"></a>語言特定處理常式
每當設定旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER，語言特定處理常式的相對位址會出現在 UNWIND_INFO。 上一節所述，做為搜尋例外狀況處理常式的一部分，或是回溯的一部分呼叫語言特定處理常式。 它有下列的原型：  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **Exception_record**提供例外狀況記錄具有標準 Win64 定義的指標。  
  
 **EstablisherFrame**是固定的堆疊配置，這個函式的基底的位址。  
  
 **ContextRecord**例外狀況 （例外狀況處理常式案例中） 的時間或目前的例外狀況內容指向的 「 回溯 」 （在終止處理常式例中） 的內容。  
  
 **DispatcherContext**點發送器內容中，此函式。 它有下列定義：  
  
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
  
 **ControlPc** RIP 內此函式的值。 這是例外狀況位址或在其控制項離開建立之函式的位址。 這是將用來判斷控制項是否在這個函式內某些受保護建構 RIP (例如 __try 區塊\_或 /\__except 或\_或 /\___identifier)。  
  
 **將 ImageBase**是映像基底 （載入地址） 的模組包含此函式，新增到函式項目中使用之 32 位元位移與回溯程式以記錄相對位址的資訊。  
  
 **FunctionEntry**供應器的指標 RUNTIME_FUNCTION 函式項目持有函式，並回溯此函式的資訊映像基底相對位址。  
  
 **EstablisherFrame**是固定的堆疊配置，這個函式的基底的位址。  
  
 **TargetIp**提供指定回溯的接續位址選擇性的指令位址。 如果，則會忽略這個位址**EstablisherFrame**未指定。  
  
 **ContextRecord**指向例外狀況內容，以供系統例外狀況分派/回溯程式碼。  
  
 **LanguageHandler**指向特定語言的語言處理常式呼叫。  
  
 **HandlerData**指向這個函式將語言特定處理常式資料。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理 (x64)](../build/exception-handling-x64.md)