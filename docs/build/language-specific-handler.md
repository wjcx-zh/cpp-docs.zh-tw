---
title: "語言特定處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 語言特定處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

語言特定處理常式的相對位址，在每次設定 UNW\_FLAG\_EHANDLER 或 UNW\_FLAG\_UHANDLER 旗標時會在 UNWIND\_INFO 中提供。  如前一章節所述，會呼叫語言特定處理常式做為搜尋例外狀況處理常式 \(Exception Handler\) 或回溯的一部分。  此處理常式具有下列原型 \(Prototype\)：  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **ExceptionRecord** 提供例外狀況 \(Exception\) 記錄的指標 \(含有標準的 Win64 定義\)。  
  
 **EstablisherFrame** 是這個函式之固定堆疊配置 \(Stack Allocation\) 的基底位址。  
  
 **ContextRecord** 會指向引發例外狀況時的例外狀況內容 \(如果是例外處理常式\) 或目前的「回溯」內容 \(如果是終止處理常式\)。  
  
 **DispatcherContext** 會指向這個函式的發送器 \(Dispatcher\) 內容。  具有下列定義：  
  
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
  
 **ControlPc** 是這個函式中 RIP 的值。  值不是例外狀況位址就是控制項離開建立之函式的位址。  這是用來判斷控制是否在這個函式的某些受保護之建構中 \(例如，\_\_try\/\_\_except 或 \_\_try\/\_\_finally 的 \_\_try 區塊\) 的 RIP。  
  
 **ImageBase** 是包含這個函式之模組的影像基底 \(載入位址\)，會加到 32 位元的位移 \(Offset\)，此位移在函式進入點和回溯資訊中使用以記錄相對位址。  
  
 **FunctionEntry** 提供 RUNTIME\_FUNCTION 函式進入點的指標，此進入點會儲存函式以及這個函式的回溯資訊影像基底相對位址。  
  
 **EstablisherFrame** 是這個函式之固定堆疊配置 \(Stack Allocation\) 的基底位址。  
  
 **TargetIp** 提供選擇性的指示位址，指定回溯的接續位址。  如果未指定 **EstablisherFrame**，則會忽略這個位址。  
  
 **ContextRecord** 會指向例外狀況內容，由系統例外狀況分派\/回溯程式碼所使用。  
  
 **LanguageHandler** 會指向要呼叫的語言特定處理常式。  
  
 **HandlerData** 會指向這個函式的語言特定處理常式資料。  
  
## 請參閱  
 [例外狀況處理 \(x64\)](../build/exception-handling-x64.md)