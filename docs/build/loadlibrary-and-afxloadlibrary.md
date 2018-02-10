---
title: "LoadLibrary 和 AfxLoadLibrary |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LoadLibrary
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd24f125398cab606ca835094727a4a2819fb17e
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary
處理呼叫[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) (或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) 明確地連結到 DLL。 如果函式成功，它對應指定的 DLL 呼叫處理序的位址空間，並將控制代碼傳回至可與其他函式中明確連結的 DLL — 比方說，`GetProcAddress`和`FreeLibrary`。  
  
 `LoadLibrary`嘗試找出使用相同的搜尋順序用於隱含連結的 DLL。 如果系統找不到 DLL 或進入點函式會傳回 FALSE，`LoadLibrary`傳回 NULL。 如果呼叫`LoadLibrary`指定 DLL 模組已對應至呼叫的處理序的位址空間，此函數會傳回 DLL 並遞增的控制代碼之模組的參考計數。  
  
 如果 DLL 進入點函式，作業系統會呼叫此函式呼叫的執行緒內容中`LoadLibrary`。 如果 DLL 已附加至處理序因為先前呼叫的進入點函式不會呼叫`LoadLibrary`具有對應呼叫`FreeLibrary`函式。  
  
 載入 MFC 擴充 Dll 的 MFC 應用程式，我們建議您使用`AfxLoadLibrary`而不是`LoadLibrary`。 `AfxLoadLibrary`處理執行緒的同步處理，才能呼叫`LoadLibrary`。 介面 （函式原型） 來`AfxLoadLibrary`相同`LoadLibrary`。  
  
 如果 Windows 無法載入 DLL，處理程序可以嘗試從錯誤中復原。 例如，處理程序無法通知錯誤的使用者，並要求使用者指定的 DLL 的另一個路徑。  
  
> [!IMPORTANT]
>  請確定指定的任何 Dll 的完整路徑。 載入檔案時，會先搜尋目前的目錄。 如果不符合檔案的路徑，可能會載入並不是預期的檔案。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [如何以隱含方式連結到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [決定要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [可由 Windows 來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)