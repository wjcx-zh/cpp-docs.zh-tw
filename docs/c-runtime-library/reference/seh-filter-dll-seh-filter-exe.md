---
title: "_seh_filter_dll、_seh_filter_exe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_XcptFilter"
  - "_seh_filter_dll"
  - "_seh_filter_exe"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "XcptFilter"
  - "_XcptFilter"
  - "_seh_filter_dll"
  - "_seh_filter_exe"
  - "corecrt_startup/_seh_filter_exe"
  - "corecrt_startup/_seh_filter_dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XcptFilter 函式"
  - "_XcptFilter 函式"
  - "_seh_filter_dll 函式"
  - "_seh_filter_exe 函式"
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _seh_filter_dll、_seh_filter_exe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

識別例外狀況及要採取的相關動作。  
  
## 語法  
  
```  
int __cdecl _seh_filter_dll(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
int __cdecl _seh_filter_exe(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
```  
  
#### 參數  
 \[in\] `_ExceptionNum`  
 例外狀況的識別項。  
  
 \[in\] `_ExceptionPtr`  
 例外狀況資訊的指標。  
  
## 傳回值  
 一個整數，表示根據例外狀況處理結果所要採取的動作。  
  
## 備註  
 這些方法會由 [try\-except 陳述式](../../cpp/try-except-statement.md) 的例外狀況篩選條件運算式呼叫。 此方法會參考常數內部資料表，以識別例外狀況並判斷適當的動作，如下所示。 例外狀況編號會在 winnt.h 中定義，而訊號編號會在 signal.h 中定義。  
  
|例外狀況編號 \(unsigned long\)|訊號編號|  
|------------------------------|----------|  
|STATUS\_ACCESS\_VIOLATION|SIGSEGV|  
|STATUS\_ILLEGAL\_INSTRUCTION|SIGILL|  
|STATUS\_PRIVILEGED\_INSTRUCTION|SIGILL|  
|STATUS\_FLOAT\_DENORMAL\_OPERAND|SIGFPE|  
|STATUS\_FLOAT\_DIVIDE\_BY\_ZERO|SIGFPE|  
|STATUS\_FLOAT\_INEXACT\_RESULT|SIGFPE|  
|STATUS\_FLOAT\_INVALID\_OPERATION|SIGFPE|  
|STATUS\_FLOAT\_OVERFLOW|SIGFPE|  
|STATUS\_FLOAT\_STACK\_CHECK|SIGFPE|  
|STATUS\_FLOAT\_UNDERFLOW|SIGFPE|  
  
## 需求  
 **標頭：**corecrt\_startup.h  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)