---
title: "應用程式定義域和 Visual C++ | Microsoft Docs"
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
  - "/clr 編譯器選項 [C++], 應用程式定義域"
  - "應用程式定義域 [C++], C++"
  - "Interop [C++], 應用程式定義域"
  - "互通性 [C++], 應用程式定義域"
  - "混合的組件 [C++], 應用程式定義域"
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式定義域和 Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您具備 `__clrcall` 虛擬函式，則 vtable 會針對每個應用程式定義域 \(appdomain\) 而存在。  如果您在某個 appdomain 中建立物件，就只能在那個 appdomain 中呼叫虛擬函式。  在 **\/clr:pure** 編譯單位中定義的所有函式都會使用 `__clrcall` 呼叫慣例 \(Calling Convention\)。  因此，在 **\/clr:pure** 編譯單位中定義的所有 vtable 都是針對每個 appdomain 而存在。  在混合模式 \(**\/clr**\) 中，如果型別缺少 `__clrcall` 虛擬函式，您就會擁有每個處理序的 vtable。  
  
 如需詳細資訊，請參閱  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [\_\_clrcall](../cpp/clrcall.md)  
  
-   [如何：移轉至 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [處理序](../cpp/process.md)  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)