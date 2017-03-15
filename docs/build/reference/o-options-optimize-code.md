---
title: "/O 選項 (最佳化程式碼) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.Optimization"
  - "/o"
  - "VC.Project.VCCLWCECompilerTool.Optimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 效能"
  - "效能, cle.exe 編譯器"
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /O 選項 (最佳化程式碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/O** 選項會控制協助您以最快速度或最小大小建立程式碼的各種最佳化。  
  
-   [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 會以最小大小為目標，對程式碼進行最佳化。  
  
-   [\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 會以最快速度為目標，對程式碼進行最佳化。  
  
-   [\/Ob](../../build/reference/ob-inline-function-expansion.md) 會控制內嵌函式的展開。  
  
-   [\/Od](../../build/reference/od-disable-debug.md) 會停用最佳化，以加速編譯並簡化偵錯。  
  
-   [\/Og](../../build/reference/og-global-optimizations.md) 會啟用全域最佳化。  
  
-   [\/Oi](../../build/reference/oi-generate-intrinsic-functions.md) 對適當的函式呼叫產生內建函式 \(Intrinsic Function\)。  
  
-   [\/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) 指示編譯器，大小最佳化要優先於速度最佳化。  
  
-   [\/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) \(預設設定\) 指示編譯器，速度最佳化要優先於大小最佳化。  
  
-   [\/Ox](../../build/reference/ox-full-optimization.md) 會選取完整最佳化。  
  
-   [\/Oy](../../build/reference/oy-frame-pointer-omission.md) 會在呼叫堆疊上隱藏框架指標的建立，讓函式呼叫更快速進行。  
  
## 備註  
 您也可以將多個 **\/O** 選項合併成單一選項陳述式。  例如，`/Odi` 和 `/Od /Oi` 相同。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)