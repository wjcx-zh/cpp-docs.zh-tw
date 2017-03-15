---
title: "_open_osfhandle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_open_osfhandle"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_open_osfhandle"
  - "open_osfhandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "open_osfhandle 函式"
  - "檔案控制代碼 [C++], 關聯"
  - "_open_osfhandle 函式"
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _open_osfhandle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將現有作業系統檔案處理常式與 C 執行階段檔案作關聯。  
  
## 語法  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### 參數  
 `osfhandle`  
 作業系統檔案控制代碼。  
  
 `flags`  
 允許的運算型別。  
  
## 傳回值  
 如果成功，則 `_open_osfhandle` 會傳回 . C 執行階段的檔案描述項。  否則，會傳回 –1。  
  
## 備註  
 `_open_osfhandle` 函式配置 C 執行階段檔案描述項，並將它與 `osfhandle` 指定的作業系統檔案處理常式關聯。  `flags` 引數是在 Fcntl.h 定義的一或多個格式的整數運算式資訊清單常數。  當兩個以上的資訊清單常數用來形成 `flags` 引數時，常數結合位元 OR 運算子 \(  **&#124;** \).  
  
 Fcntl.h 定義下列資訊清單常數。  
  
 **\_O\_APPEND**  
 每次寫入運算時將檔案指標放置於檔案的結尾。  
  
 **\_O\_RDONLY**  
 開啟唯讀的檔案。  
  
 **\_O\_TEXT**  
 以文字模式 \(已轉譯\) 開啟檔案。  
  
 **\_O\_WTEXT**  
 以 Unicode \(已轉譯 UTF\-16\) 模式開啟檔案。  
  
 若要關閉以 `_open_osfhandle` 開啟的檔案，請呼叫 `_close` 。  底下的處理常式也會透過呼叫 `_close` 被關閉，所以不需要呼叫 Win32 函式 `CloseHandle` 來關閉原本的處理常式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_open_osfhandle`|\<io.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)