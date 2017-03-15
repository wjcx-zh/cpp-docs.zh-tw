---
title: "/Ob (內嵌函式展開) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion"
  - "VC.Project.VCCLCompilerTool.InlineFunctionExpansion"
  - "/ob"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob 編譯器選項 [C++]"
  - "/Ob0 編譯器選項 [C++]"
  - "/Ob1 編譯器選項 [C++]"
  - "/Ob2 編譯器選項 [C++]"
  - "任何適合的編譯器選項 [C++]"
  - "disable 編譯器選項 [C++]"
  - "內嵌展開, 編譯器選項"
  - "內嵌函式, function expansion 編譯器選項 [C++]"
  - "Ob 編譯器選項 [C++]"
  - "-Ob 編譯器選項 [C++]"
  - "Ob0 編譯器選項 [C++]"
  - "-Ob0 編譯器選項 [C++]"
  - "Ob1 編譯器選項 [C++]"
  - "-Ob1 編譯器選項 [C++]"
  - "Ob2 編譯器選項 [C++]"
  - "-Ob2 編譯器選項 [C++]"
  - "only __inline 編譯器選項 [C++]"
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ob (內嵌函式展開)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制函式的內嵌展開。  
  
## 語法  
  
```  
/Ob{0|1|2}  
```  
  
## 引數  
 **0**  
 停用內嵌展開。  根據預設，所有函式上的展開都是由編譯器決定，通常稱為*「自動內嵌」*\(Auto\-Inlining\)。  
  
 **1**  
 只能展開標記為 [inline](../../misc/inline-inline-forceinline.md)、[\_\_inline](../../misc/inline-inline-forceinline.md) 或 [\_\_forceinline](../../misc/inline-inline-forceinline.md) 的函式，或是類別宣告中所定義之 C\+\+ 成員函式中的函式。  
  
 **2**  
 預設值。  可展開標記為 `inline`、`__inline` 或 `__forceinline` 的函式，以及編譯器所選擇的其他任何函式。  
  
 **\/Ob2** 會在使用 [\/O1、\/O2 \(最小大小、最快速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 [\/Ox \(完全最佳化\)](../../build/reference/ox-full-optimization.md) 時生效。  
  
 這個選項需要您使用 **\/O1**、**\/O2**、**\/Ox** 或 **\/Og** 啟用最佳化。  
  
## 備註  
 編譯器會將內嵌展開選項和關鍵字視為建議，  而不會保證以內嵌方式展開所有函式。  您可以停用內嵌展開，但無法強制編譯器內嵌特定函式，即使是使用 `__forceinline` 關鍵字亦然。  
  
 您可以使用 `#pragma` [auto\_inline](../../preprocessor/auto-inline.md) 指示詞，將函式從內嵌展開的候選考量中排除。  另請參閱 `#pragma` [intrinsic](../../preprocessor/intrinsic.md) 指示詞。  
  
> [!NOTE]
>  從分析測試回合所收集的資訊會覆寫最佳化，這個最佳化在指定 **\/Ob**、**\/Os** 或 **\/Ot** 時才會生效。  如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  依序展開 \[**組態屬性**\] 和 \[**C\/C\+\+**\]，然後選取 \[**最佳化**\]。  
  
3.  修改 \[**內嵌函式展開**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)