---
title: "cl.exe 的傳回值 | Microsoft Docs"
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
helpviewer_keywords: 
  - "cl.exe 編譯器, 傳回值"
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cl.exe 的傳回值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe 傳回零，代表成功 \(沒有錯誤\)，否則即傳回非零。  
  
 如果您是從指令碼、powershell、.cmd 或 .bat 檔案進行編譯，cl.exe 的傳回值會很實用。  建議您擷取編譯器的輸出，萬一發生錯誤或警告，就可加以解決。  
  
 cl.exe 有太多可能的錯誤結束代碼，無法全部列出。  您可以在位於 %ProgramFiles\(x86\)%\\Windows Kits\\`version`\\Include\\shared\\ 目錄中，Windows Software Development Kit 隨附的 winerror.h 或 ntstatus.h 檔案中查詢錯誤碼。  以十進位格式傳回的錯誤碼必須轉換成十六進位才能進行搜尋。  例如，錯誤碼 \-1073741620 轉換為十六進位會是 0xC00000CC。  這個錯誤是在 ntstatus.h 中找到，對應的訊息為「遠端伺服器上找不到指定的共用名稱」\(The specified share name cannot be found on the remote server\)。如需可下載的 Windows 錯誤碼清單，請參閱 [&#91;MS\-ERREF&#93;: Windows Error Codes](http://msdn.microsoft.com/zh-tw/1bc92ddf-b79e-413c-bbaa-99a5281a6c90)。  
  
 您也可以使用 Visual Studio 中的錯誤查詢公用程式，找出編譯器錯誤訊息代表的意義。  在 Visual Studio 命令殼層中，輸入 **errlook.exe** 即可啟動公用程式，或是在 Visual Studio IDE 的功能表列上選擇 \[**工具**\]、\[**錯誤查詢**\]。  輸入錯誤值，就可以找到與錯誤相關聯的描述文字。  如需詳細資訊，請參閱[ERRLOOK 參考](../../build/reference/errlook-reference.md)。  
  
## 備註  
 以下範例 .bat 檔是使用 cl.exe 的傳回值。  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## 請參閱  
 [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)