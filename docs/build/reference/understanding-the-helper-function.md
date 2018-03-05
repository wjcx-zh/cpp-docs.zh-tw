---
title: "了解 Helper 函式 |Microsoft 文件"
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
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>了解 Helper 函式
連結器支援延遲載入 helper 函式是什麼實際上會在執行階段載入 DLL。 您可以修改透過撰寫自己的函式，並將它連結至您的程式，而不是使用 Delayimp.lib 中提供的 helper 函式來自訂其行為的 helper 函式。 一個 helper 函式是所有的延遲載入 Dll。  
  
 如果您想要執行特定 DLL 或匯入的名稱為基礎的處理，您可以提供您自己的 helper 函式版本。  
  
 Helper 函式會執行下列動作：  
  
-   檢查儲存的控制代碼，以檢查是否已載入文件庫  
  
-   呼叫**LoadLibrary**嘗試載入的 dll  
  
-   呼叫**GetProcAddress**嘗試取得程序的位址  
  
-   傳回延遲匯入載入至呼叫目前已載入的進入點 thunk  
  
 Helper 函式可以呼叫回您的程式中的告知攔截之後每個下列動作：  
  
-   Helper 函式啟動時  
  
-   之前**LoadLibrary** helper 函式中呼叫  
  
-   之前**GetProcAddress** helper 函式中呼叫  
  
-   如果呼叫**LoadLibrary** helper 函式中失敗  
  
-   如果呼叫**GetProcAddress** helper 函式中失敗  
  
-   之後的 helper 函式，完成處理  
  
 每一種攔截點可以傳回值，會改變以某種方式除了延遲匯入負載 thunk 傳回 helper 常式的正常處理。  
  
 預設的協助程式程式碼可以在中找到 Delayhlp.cpp 和 Delayimp.h （vc\include)，並在 Delayimp.lib 中 （在 vc\lib) 編譯。 您必須在編譯中包含此程式庫，除非您撰寫您自己的 helper 函式。  
  
 下列主題將描述 helper 函式：  
  
-   [Visual C++ 6.0 之後 DLL 延遲載入協助程式函式的變更](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [呼叫慣例、參數和傳回型別](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [結構和常數定義](../../build/reference/structure-and-constant-definitions.md)  
  
-   [計算需要的值](../../build/reference/calculating-necessary-values.md)  
  
-   [卸載延遲載入的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)