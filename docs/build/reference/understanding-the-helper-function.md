---
title: "了解 Helper 函式 | Microsoft Docs"
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
  - "__delayLoadHelper 函式"
  - "__delayLoadHelper2 函式"
  - "DLL 的延遲載入, helper 函式"
  - "delayhlp.cpp"
  - "delayimp.h"
  - "delayimp.lib"
  - "Helper 函式"
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 了解 Helper 函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

連結器支援的延遲載入 Helper 函式是在執行階段實際載入 DLL 的函式。  您可以撰寫自己的函式，並將它與您的程式連結，而不使用 Delayimp.lib 提供的 Helper 函式，來修改 Helper 函式以自訂其行為。  由一個 Helper 函式負責服務所有延遲載入的 DLL。  
  
 如果您希望根據 DLL 或匯入的名稱執行特定的處理，可以提供您自己的 Helper 函式版本。  
  
 Helper 函式執行下列動作：  
  
-   檢查程式庫中儲存的控制代碼，以確認是否已經載入  
  
-   呼叫 **LoadLibrary** 以試著載入 DLL  
  
-   呼叫 **GetProcAddress** 以試著取得程序的位址  
  
-   傳回延遲匯入載入 Thunk，以便呼叫目前已載入的進入點  
  
 Helper 函式可以在執行下列每一動作後，回呼程式中的告知攔截：  
  
-   在 Helper 函式啟動後  
  
-   在 Helper 函式呼叫 **LoadLibrary** 前  
  
-   在 Helper 函式呼叫 **GetProcAddress** 前  
  
-   在 Helper 函式呼叫 **LoadLibrary** 失敗時  
  
-   在 Helper 函式呼叫 **GetProcAddress** 失敗時  
  
-   在 Helper 函式處理完畢後  
  
 其中每一個攔截點都可以傳回將以某些方式改變 Helper 常式正常處理行為的值，除了傳回延遲匯入載入 Thunk 外。  
  
 在 Delayhlp.cpp 和 Delayimp.h \(vc\\include 之下\) 中可以找到預設的 Helper 程式碼，並在 Delayimp.lib \(vc\\lib 之下\) 中編譯。  除非您撰寫了自己的 Helper 函式，否則在您的編譯 \(Compilation\) 中必須包含這個程式庫。  
  
 下列主題說明 Helper 函式：  
  
-   [Visual C\+\+ 6.0 之後 DLL 延遲載入 Helper 函式的變更](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [呼叫慣例、參數和傳回型別](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [結構和常數定義](../../build/reference/structure-and-constant-definitions.md)  
  
-   [計算需要的值](../../build/reference/calculating-necessary-values.md)  
  
-   [卸載延遲載入的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)