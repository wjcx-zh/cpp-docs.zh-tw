---
title: "當使用以 /clr 建置的 COM 物件時防止 CLR 關閉之例外狀況 | Microsoft Docs"
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
  - "/clr 編譯器選項 [C++], CLR 關閉例外狀況"
  - "/clr 編譯器選項 [C++], COM 物件"
  - "CLR 關閉例外狀況 [C++]"
  - "Interop [C++], CLR 關閉例外狀況"
  - "互通性 [C++], CLR 關閉例外狀況"
  - "混合的組件 [C++], CLR 關閉例外狀況"
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 當使用以 /clr 建置的 COM 物件時防止 CLR 關閉之例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦 Common Language Runtime \(CLR\) 進入關閉模式，原生函式就會具備 CLR 服務的有限存取權。  當在以 **\/clr** 編譯的 COM 物件上嘗試呼叫 Release 時，CLR 會轉換至機器碼，然後轉換回 Managed 程式碼，以便服務 IUnknown::Release 呼叫 \(定義於 Managed 程式碼中\)。  由於 CLR 位於關閉模式，因此會避免呼叫回到 Managed 程式碼。  
  
 若要解決這個問題，請確定從 Release 方法呼叫的解構函式 \(Destructor\) 只包含機器碼。  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)