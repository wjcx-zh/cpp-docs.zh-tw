---
title: "錯誤攔截 | Microsoft Docs"
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
  - "DLL 的延遲載入, 失敗攔截"
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 錯誤攔截
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

錯誤攔截以和[告知攔截](../../build/reference/notification-hooks.md)相同的方式啟用。  攔截常式需要傳回適當的值才能繼續處理 \(HINSTANCE 或是 FARPROC\)，或是傳回 0 以表示應擲回例外狀況。  
  
 參考使用者定義函式的指標變數為：  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo** 結構包含正確報告錯誤所需的所有相關資料，包括來自 `GetLastError` 的值。  
  
 如果告知是 **dliFailLoadLib**，攔截函式可傳回：  
  
-   無法處理錯誤時傳回 0  
  
-   如果錯誤攔截已修復問題，並自行載入程式庫則為 HMODULE  
  
 如果告知是 **dliFailGetProc**，攔截函式可傳回：  
  
-   無法處理錯誤時傳回 0  
  
-   如果錯誤攔截成功地取得位址則為有效程序位址 \(匯入函式位址\)  
  
## 請參閱  
 [錯誤處理和告知](../../build/reference/error-handling-and-notification.md)