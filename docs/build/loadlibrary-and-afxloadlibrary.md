---
title: "LoadLibrary 和 AfxLoadLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LoadLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxLoadLibrary 方法"
  - "DLL [C++], AfxLoadLibrary"
  - "DLL [C++], LoadLibrary"
  - "明確連結 [C++]"
  - "LoadLibrary 方法"
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LoadLibrary 和 AfxLoadLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

處理序會呼叫 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) \(或 [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)\) 來明確連結至 DLL。  如果函式成功，就會將指定的 DLL 對應到呼叫處理序的位址空間，並將控制代碼傳回給其他明確連結的函式 \(例如 `GetProcAddress` 和 `FreeLibrary`\) 所使用到的 DLL。  
  
 `LoadLibrary` 會嘗試依照和隱含連結所用的相同搜尋順序來找出 DLL。  如果系統無法找出 DLL 或者如果進入點函式傳回 FALSE，`LoadLibrary` 就會傳回 NULL。  如果對 `LoadLibrary` 的呼叫指定已經對應到呼叫處理序位址空間中的 DLL 模組，則函式只會傳回 DLL 的控制代碼，並遞增模組的參考計數。  
  
 作業系統會在 DLL 擁有進入點函式時，呼叫執行緒內容中名為 `LoadLibrary` 的函式。  如果 DLL 已經連結至處理序，就不會呼叫進入點函式，因為先前對 `LoadLibrary` 的呼叫並沒有包含 `FreeLibrary` 函式的對應呼叫。  
  
 對於會載入擴充 DLL 的 MFC 應用程式，我們建議您使用 `AfxLoadLibrary` 而不要使用 `LoadLibrary`。  `AfxLoadLibrary` 可在您呼叫 `LoadLibrary` 之前處理執行緒同步處理。  `AfxLoadLibrary` 的介面 \(函式原型\) 與 `LoadLibrary` 相同。  
  
 如果 Windows 無法載入 DLL，處理序可以嘗試從錯誤復原。  例如，處理序將錯誤告知使用者，並且要求使用者指定 DLL 的另一個路徑。  
  
> [!IMPORTANT]
>  如果程式碼要在 Windows NT 4、Windows 2000 或 Windows XP \(SP1 以前的版本\) 下執行，請務必指定所有 DLL 的完整路徑。  在這些作業系統上，載入檔案時會先搜尋目前的目錄。  如果您不限定檔案的路徑，則可能會載入非預期的檔案。  
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)