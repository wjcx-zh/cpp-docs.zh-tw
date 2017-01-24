---
title: "Visual C++ 6.0 之後 DLL 延遲載入 Helper 函式的變更 | Microsoft Docs"
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
  - "__delayLoadHelper2 函式"
  - "DLL 的延遲載入, 已變更的內容"
  - "Helper 函式, 已變更的內容"
  - "PFromRva 方法"
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 6.0 之後 DLL 延遲載入 Helper 函式的變更
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您的電腦中有多個版本的 Visual C\+\+ 或是您定義了自己的 Helper 函式，則可能會受到 DLL 延遲載入 Helper 函式變更的影響。  例如：  
  
-   **\_\_delayLoadHelper** 現在變更為 **\_\_delayLoadHelper2**  
  
-   **\_\_pfnDliNotifyHook** 現在變更為 **\_\_pfnDliNotifyHook2**  
  
-   **\_\_pfnDliFailureHook** 現在變更為 **\_\_pfnDliFailureHook2**  
  
-   **\_\_FUnloadDelayLoadedDLL** 現在變更為 **\_\_FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  如果是使用預設的 Helper 函式，這些變更將不會影響您。  叫用連結器的方法也沒有改變。  
  
## 多個版本的 Visual C\+\+  
 如果您的電腦中有多個版本的 Visual C\+\+，請確定連結器與 delayimp.lib 相符。  如果不相符，將會發生連結器錯誤，回報 `___delayLoadHelper2@8` 或 `___delayLoadHelper@8` 為未解析的外部符號。  前者表示使用新版的連結器和舊版的 delayimp.lib，後者表示使用舊版的連結器和新版的 delayimp.lib。  
  
 如果取得無法解析的連結器錯誤，請對預期包含 Helper 函式的 delayimp.lib 執行 [dumpbin \/linkermember](../../build/reference/linkermember.md):1，以查看做為替代所定義的 Helper 函式為何。  也可在目的檔 \(Object File\) 中定義 Helper 函式；執行 [dumpbin \/symbols](../../build/reference/symbols.md) 並尋找 `delayLoadHelper(2)`。  
  
 如果您有 Visual C\+\+ 6.0 連結器，那麼：  
  
-   對延遲載入 Helper 的 .lib 或 .obj 檔案執行 dumpbin，以確定它是否定義了 **\_\_delayLoadHelper2**。  如果沒有定義，連結將會失敗。  
  
-   在延遲載入 Helper 的 .lib 或 .obj 檔案中定義 **\_\_delayLoadHelper**。  
  
## 使用者定義的 Helper 函式  
 如果您定義了自己的 Helper 函式，並使用最新版本的 Visual C\+\+，請執行下列動作：  
  
-   將 Helper 函式重新命名為 **\_\_delayLoadHelper2**。  
  
-   由於延遲描述項 \(delayimp.h 中的 ImgDelayDescr\) 的指標已經由絕對位址 \(VA\) 變更為相對位址 \(RVA\)，以便可以如預期地在 32 位元及 64 位元程式中使用，因此您必須將這些轉換回指標。  之前介紹過了一個新函式：delayhlp.cpp 中的 PFromRva。  您可以在描述項的每一個欄位上使用這個函式，將它們轉換回 32 或 64 位元指標。  預設的延遲載入 Helper 函式將繼續當做好樣板的範例使用。  
  
## 載入延遲載入 DLL 的所有匯入  
 連結器可以從您指定延遲載入的 DLL 載入所有匯入。  如需詳細資訊，請參閱[載入延遲載入 DLL 的所有匯入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)。  
  
## 請參閱  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-tw/6279c12c-d908-4967-b0b3-cabfc3e91d3d)