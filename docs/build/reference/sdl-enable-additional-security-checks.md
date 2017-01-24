---
title: "/sdl (啟用其他安全性檢查) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.SDLCheck"
dev_langs: 
  - "C++"
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /sdl (啟用其他安全性檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加入建議的安全性開發週期 \(SDL\) 檢查。  這些檢查包括額外的安全性相關警告 \(視為錯誤\)，以及其他安全程式碼產生功能。  
  
## 語法  
  
```  
/sdl[-]  
```  
  
## 備註  
 **\/sdl** 啟用 [\/GS](../../build/reference/gs-buffer-security-check.md) 提供的基準安全性檢查的超集，並覆寫 **\/GS\-**。  根據預設，**\/sdl** 為關閉。  **\/sdl\-** 停用其他安全性檢查。  
  
## 編譯時期檢查  
 **\/sdl** 可讓這些警告視為錯誤：  
  
|\/sdl 啟用的警告|對應的命令列參數|描述|  
|-----------------|--------------|--------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|\/we4146|一元減號運算子套用至不帶正負號的類型，產生不帶正負號的結果。|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|\/we4308|將負整數常數轉換為 unsigned 類型，產生一個可能無意義的結果。|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|\/we4532|在異常終止期間，於 `continue`\/`break` 區塊中使用 `goto`、`__finally` 或 `finally` 關鍵字有未定義的行為。|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|\/we4533|初始化變數的程式碼不會執行。|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|\/we4700|使用了未初始化的區域變數。|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|\/we4703|使用了可能未初始化的本機指標變數。|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|\/we4789|當使用特定 C 執行階段 \(CRT\) 函式時發生緩衝區滿溢。|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|\/we4995|使用了以 pragma [deprecated](../../preprocessor/deprecated-c-cpp.md) 標記的函式。|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|\/we4996|使用了標記為 [deprecated](../../cpp/deprecated-cpp.md) 的函式。|  
  
## 執行階段檢查  
 當 **\/sdl** 啟用時，編譯器會產生程式碼，在執行階段執行這些檢查：  
  
-   啟用 strict 模式 **\/GS** 執行階段緩衝區滿溢偵測，相當於使用 `#pragma strict_gs_check(push, on)` 編譯。  
  
-   執行有限的指標淨化。  在未涉及取值的運算式中和沒有使用者定義解構函式的類型中，指標參考在呼叫 `delete` 之後設定為非有效位址。  這有助於防止過時的指標參考重複使用。  
  
-   執行類別成員初始化。  在物件具現化 \(在建構函式執行之前\)，自動將所有類別成員初始化為零。  這有助於避免使用未初始化的資料 \(與建構函式未明確初始化的類別成員相關聯\)。  
  
## 備註  
 如需詳細資訊，請參閱[警告、\/sdl 和改善未初始化的變數偵測](http://go.microsoft.com/fwlink/p/?LinkId=331012)。  
  
#### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  在 \[**一般**\] 頁面中，從 \[**SDL 檢查**\] 下拉式清單中選取選項。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)