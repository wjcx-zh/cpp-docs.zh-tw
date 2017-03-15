---
title: "載入延遲載入 DLL 的所有匯入 | Microsoft Docs"
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
  - "__HrLoadAllImportsForDll 連結器選項"
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 載入延遲載入 DLL 的所有匯入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 delayhlp.cpp 中定義的 **\_\_HrLoadAllImportsForDll** 函式會告訴連結器從以 [\/delayload](../../build/reference/delayload-delay-load-import.md) 連結器選項指定的 DLL 載入所有匯入。  
  
 載入所有匯入允許您將錯誤處理置於您程式碼中的一個地方，而不需要在實際呼叫匯入的附近使用例外狀況處理 \(Exception Handling\)。  它也避免了因為 Helper 程式碼載入匯入失敗，而造成應用程式在執行過程中部分失敗的情況。  
  
 呼叫 **\_\_HrLoadAllImportsForDll** 並不會改變攔截 \(Hook\) 的行為和錯誤處理；如需詳細資訊，請參閱[錯誤處理和告知](../../build/reference/error-handling-and-notification.md)。  
  
 傳遞給 **\_\_HrLoadAllImportsForDll** 的 DLL 名稱會與 DLL 本身內部儲存的名稱進行比較，並且區分大小寫。  
  
 下列範例顯示如何呼叫 **\_\_HrLoadAllImportsForDll**：  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)