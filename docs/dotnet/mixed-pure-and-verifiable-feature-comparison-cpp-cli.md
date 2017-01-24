---
title: "混合的、純粹的和可驗證的功能比較 (C++/CLI) | Microsoft Docs"
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
  - "混合的組件 [C++]"
  - "混合的組件 [C++], 與純的比較"
  - "混合的組件 [C++], 與安全的比較"
  - "純的組件 [C++]"
  - "純的 MSIL [C++]"
  - "純的 MSIL [C++], 與混合的和安全的比較"
  - "純的 MSIL [C++], 與混合的比較"
  - "純的 MSIL [C++], 與安全的比較"
  - "安全的組件 [C++]"
  - "安全的組件 [C++], 與混合的比較"
  - "安全的組件 [C++], 與純的比較"
  - "可驗證的組件 [C++]"
  - "可驗證的組件 [C++], 與混合的比較"
  - "可驗證的組件 [C++], 與純的比較"
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合的、純粹的和可驗證的功能比較 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題會比較不同 **\/clr** 編譯模式的功能。  如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 功能比較  
  
|功能|混合 \(\/clr\)|純粹 \(\/clr:pure\)|安全 \(\/clr:safe\)|相關資訊|  
|--------|------------------|-----------------------|-----------------------|----------|  
|CRT 程式庫|支援|支援||[依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC\/ATL|支援|||[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md) &#124; [Class Overview](../atl/atl-class-overview.md)|  
|Unmanaged 函式|支援|||[混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Unmanaged 資料|支援|支援||[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|可以從 Unmanaged 函式呼叫|支援|||[如何：移轉至 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|支援呼叫 Unmanaged 函式|支援|僅限 C\-Style 函式|僅限 P\/Invoke|[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|支援反映|僅限 DLL|支援|支援|[反映](../dotnet/reflection-cpp-cli.md)|  
  
## 請參閱  
 [純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)