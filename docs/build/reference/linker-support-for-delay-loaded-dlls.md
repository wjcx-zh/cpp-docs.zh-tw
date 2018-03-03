---
title: "延遲載入 Dll 的連結器支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83e75df963889730e4514c38d0551af241a788fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-support-for-delay-loaded-dlls"></a>延遲載入 DLL 的連結器支援
Visual c + + 連結器現在支援 Dll 的延遲的載入。 這讓您使用 Windows SDK 函式需要**LoadLibrary**和**GetProcAddress**來實作延遲載入 DLL。  
  
 在 Visual c + + 6.0 之前, 在執行階段載入 DLL 的唯一方式是使用**LoadLibrary**和**GetProcAddress**; 系統會載入 DLL 時可執行檔或 DLL 使用載入它。  
  
 從 Visual c + + 6.0 中，以靜態方式連結的 DLL 時，連結器會提供選項，以延遲載入 DLL，直到程式該 DLL 中呼叫的函式。  
  
 應用程式可能會延遲載入 DLL 使用[/DELAYLOAD （延遲載入匯入）](../../build/reference/delayload-delay-load-import.md) helper 函式 （Visual c + + 所提供的預設實作） 使用的連結器選項。 Helper 函式會藉由呼叫在執行階段中載入的 DLL **LoadLibrary**和**GetProcAddress**您。  
  
 您應該考慮延遲載入 DLL:  
  
-   您的程式可能不會在 DLL 中呼叫函式。  
  
-   在 DLL 中的函式不可以在程式執行的呼叫。  
  
 可以在組建中的其中一個指定 DLL 的延遲的載入。EXE 或。DLL 的專案。 A。DLL 專案的延遲載入的一個或多個 Dll 不應該本身呼叫的延遲載入的進入點位在 Dllmain 中。  
  
 下列主題將描述延遲載入 Dll:  
  
-   [指定要延遲載入的 DLL](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [明確卸載延遲載入的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [載入延遲載入 DLL 的所有匯入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [繫結匯入](../../build/reference/binding-imports.md)  
  
-   [錯誤處理和通知](../../build/reference/error-handling-and-notification.md)  
  
-   [傾印延遲載入的匯入](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [延遲載入 DLL 的條件約束](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [了解協助協助程式函式](understanding-the-helper-function.md)  
  
-   [開發您自己的協助程式函式](../../build/reference/developing-your-own-helper-function.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual c + + 中的 Dll](../../build/dlls-in-visual-cpp.md)   
 [連結](../../build/reference/linking.md)