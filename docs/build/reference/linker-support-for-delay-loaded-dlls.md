---
title: "延遲載入 DLL 的連結器支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL 的延遲載入, 連結器支援"
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 延遲載入 DLL 的連結器支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 連結器現在能夠支援延遲載入 DLL，  這讓您不需再使用 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 的函式 **LoadLibrary** 和 **GetProcAddress** 來實作 DLL 的延遲載入。  
  
 在 Visual C\+\+ 6.0 以前，要於執行階段載入 DLL 的唯一方法就是使用 **LoadLibrary** 和 **GetProcAddress**；在載入使用 DLL 的可執行檔或 DLL 時，作業系統就會載入該 DLL。  
  
 從 Visual C\+\+ 6.0 開始，靜態連結 DLL 時，連結器會提供延遲載入 DLL 的選項，直到程式呼叫該 DLL 中的函式為止。  
  
 應用程式可以使用 [\/DELAYLOAD \(延遲載入匯入\)](../../build/reference/delayload-delay-load-import.md) 的連結器選項和 Helper 函式 \(Visual C\+\+ 所提供的預設實作環境\) 延遲載入 DLL。  Helper 函式將在執行階段時呼叫 **LoadLibrary** 和 **GetProcAddress** 來載入 DLL。  
  
 下列情形時，您應該考慮延遲載入 DLL：  
  
-   程式可能不會呼叫在 DLL 中的函式  
  
-   可能要等到程式執行的後期才會呼叫 DLL 中的函式  
  
 建置 .EXE 或 .DLL 專案時，可以指定延遲載入 DLL。  延遲載入一或多個 DLL 的 .DLL 專案不應該自己呼叫 DllMain 中的延遲載入進入點 \(Entry Point\)。  
  
 下列主題說明延遲載入 DLL：  
  
-   [指定要延遲載入的 DLL](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [明確卸載延遲載入的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [載入延遲載入 DLL 的所有匯入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [繫結匯入](../../build/reference/binding-imports.md)  
  
-   [錯誤處理和告知](../../build/reference/error-handling-and-notification.md)  
  
-   [傾印延遲載入的匯入](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [延遲載入 DLL 的條件約束](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [了解 Helper 函式](http://msdn.microsoft.com/zh-tw/6279c12c-d908-4967-b0b3-cabfc3e91d3d)  
  
-   [開發您自己的 Helper 函式](../../build/reference/developing-your-own-helper-function.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)   
 [連結](../../build/reference/linking.md)