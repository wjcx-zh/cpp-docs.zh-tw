---
title: "__getmainargs、__wgetmainargs | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wgetmainargs"
  - "__getmainargs"
apilocation: 
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __getmainargs、__wgetmainargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

叫用命令列剖析和以傳遞的指標複製引數到 `main()`。  
  
## 語法  
  
```cpp  
int __getmainargs(  
    int * _Argc,   
   char *** _Argv,   
   char *** _Env,   
   int _DoWildCard,  
_startupinfo * _StartInfo);  
  
 int __wgetmainargs (  
   int *_Argc,  
   wchar_t ***_Argv,  
   wchar_t ***_Env,  
   int _DoWildCard,  
   _startupinfo * _StartInfo)  
  
```  
  
#### 參數  
 `_Argc`  
 包含 `argv` 之後引數的數目。  `argc` 參數永遠會大於或等於 1。  
  
 `_Argv`  
 以 null 終止之字串的陣列，表示由程式的使用者所輸入的命令列引數。  依照慣例，`argv[0]` 是對程式叫用的命令，argv\[1\] 是第一個命令列引數，依此類推，直到 argv\[argc\]，其永遠為 NULL。  第一個命令列引數一定是 `argv[1]`，而最後一個會是 `argv[argc – 1]`。  
  
 `_Env`  
 它是一個字串的陣列，表示在使用者的環境中設定的變數。  這個陣列由 NULL 項目結尾。  
  
 `_DoWildCard`  
 若設定為 1 展開命令列引數的萬用字元，或者，如果集合則為 0 不做事的整數。  
  
 `_StartInfo`  
 將傳遞至 CRT DLL 的其他資訊。  
  
## 傳回值  
 如果成功，則為 0;如果未成功，則為負數值。  
  
## 備註  
 在非寬字元平台上使用 `__getmainargs` 和在寬字元 \(Unicode\) 平台上使用 `__wgetmainargs` 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_getmainargs|internal.h|  
|\_\_wgetmainargs|internal.h|