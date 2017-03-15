---
title: "Interop 的效能考量 (C++) | Microsoft Docs"
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
  - "/clr 編譯器選項 [C++], Interop 的效能考量"
  - "Interop [C++], 效能考量"
  - "互通性 [C++], 效能考量"
  - "混合的組件 [C++], 效能考量"
  - "平台叫用 [C++], 互通性"
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interop 的效能考量 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題提供能協助您降低 Managed\/Unmanaged Interop 轉換對執行階段效能之影響的方針。  
  
 Visual C\+\+ 支援與其他 .NET 語言相同的互通性 \(Interoperability\) 機制，例如 Visual Basic 和 C\# \(P\/Invoke\)，但是也提供 Visual C\+\+ 特有的 Interop 支援 \(C\+\+ Interop\)。  對於影響效能的關鍵應用程式，瞭解每個 Interop 技術對效能的影響是很重要的。  
  
 不管使用的 Interop 技術為何，每次 Managed 函式呼叫 Unmanaged 函式時，都會需要稱為 Thunk 之特殊的轉換順序，反之亦然。  Visual C\+\+ 編譯器會自動插入這些 Thunk，但是請務必注意，這些轉換累積起來，從效能的角度來看是高度耗費資源的。  
  
## 減少轉換  
 一個避免或減少 Interop Thunk 成本的方式，是重構使用到的介面，最小化 Managed\/Unmanaged 轉換。  針對繁冗的介面 \(頻繁地在 Managed\/Unmanaged 界限之間呼叫的介面\) 做修改，可以達成大幅度的效能改進。  例如在緊密迴圈中呼叫 Unmanaged 函式的 Managed 函式，就是重構的好目標。  如果迴圈本身移至 Unmanaged 端，或建立 Unmanaged 端呼叫的 Managed 端替代，比方在 Managed 端將資料貯列起來，於迴圈結束後全部一次封送處理 \(Marshaling\) 至 Unmanaged API，則轉換的次數可以大幅降低。  
  
## P\/Invoke 對 C\+\+ Interop  
 對於 .NET 語言 \(例如 Visual Basic 和 C\#\)，與原生元件互通的建議方法是 P\/Invoke。  因為 .NET Framework 支援 P\/Invoke，所以 Visual C\+\+ 也支援此方法，但是 Visual C\+\+ 也提供自己的互通性支援，稱為 C\+\+ Interop。  C\+\+ Interop 相對於 P\/Invoke 是較佳的方式，因為 P\/Invoke 不具型別安全。  雖然這樣會使錯誤集中在執行階段回報，但是 C\+\+ Interop 相對於 P\/Invoke 也有效能上的優勢。  
  
 每當 Managed 函式呼叫 Unmanaged 函式時，這兩種技術都需要數個動作同時進行：  
  
-   函式呼叫引數從 CLR 封裝處理為原生型別。  
  
-   執行 Managed 至 Unmanaged 的 Thunk。  
  
-   呼叫 Unmanaged 函式 \(使用原生版本的引數\)。  
  
-   執行 Unmanaged 至 Managed 的 Thunk。  
  
-   傳回型別和任何 "out" 或 "in,out" 引數，從原生型別封送處理至 CLR 型別。  
  
 Managed\/Unmanaged Thunk 是讓 Interop 運作的基本條件，但是所需的資料封送處理則取決於使用的資料型別、函式簽章以及資料使用的方式。  
  
 C\+\+ Interop 執行的資料封送處理是極簡形式：參數在 Managed\/Unmanaged 界限之間以位元為單位複製，完全不執行轉換。  對於 P\/Invoke，只有在全部的參數都是簡單的 Blittable 型別時才是如此。  否則 P\/Invoke 會執行非常完整的步驟，將每個 Managed 參數轉換為適當的原生型別。如果引數標記為 "out" 或 "in,out"，也會以相反方向執行此轉換動作。  
  
 換句話說，C\+\+ Interop 使用最快的資料封送處理方式，而 P\/Invoke 使用最完整的方式。  這表示 C\+\+ Interop \(C\+\+ 的典型方式\) 預設提供最佳效能，而程式設計人員則要負責處理這個行為不安全或不適當的地方。  
  
 因此 C\+\+ Interop 會要求資料封送處理必須是明確提供的，但是好處是程式設計人員可以根據資料的本質，自行決定適當的作法和使用方式。  此外，雖然 P\/Invoke 資料封送處理的行為某種程度上可以自訂修改，但是 C\+\+ Interop 讓資料封送處理可以在每次呼叫時自訂。  這是使用 P\/Invoke 時無法做到的。  
  
 如需 C\+\+ Interop 的詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)