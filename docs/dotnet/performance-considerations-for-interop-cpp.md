---
title: "Interop （c + +） 的效能考量 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25d098ebb52809a36735f71eecedcc4c2a186225
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="performance-considerations-for-interop-c"></a>Interop 的效能考量 (C++)
本主題提供指導方針，以減少對執行階段效能的 managed/unmanaged interop 轉換效果。  
  
 Visual c + + 支援 Visual Basic 和 C# (P/Invoke)，例如其他.NET 語言的交互操作性機制相同，但它也會提供 interop 支援的特定 Visual c + + (c + + interop)。 效能關鍵應用程式，請務必了解每個 interop 技術的效能影響。  
  
 不論所使用的 interop 技巧，特殊的轉換順序呼叫 thunk，會需要每次 managed 函式呼叫 unmanaged 的函式，反之亦然。 Visual c + + 編譯器會自動插入這些 thunk，但請務必記住，累積，這些轉換可能會耗用大量的效能。  
  
## <a name="reducing-transitions"></a>減少轉換  
 若要避免或減少 interop thunk 成本的方法之一是重構所涉及的 managed/unmanaged 轉換降到最低的介面。 將目標設為多對話介面，是指涉及經常呼叫的 managed/unmanaged 的界限之間可大幅的效能改進。 Managed 函式呼叫 unmanaged 函式在緊密迴圈中，比方說，是絕佳候選重構。 如果迴圈本身會移至 unmanaged 端，或如果受管理的替代方式，來建立 unmanaged 的呼叫 （也許是在 managed 端佇列的資料，然後封送處理至 unmanaged 的 API 迴圈後一次） 的轉換數目可以降低登ificantly。  
  
## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs。C++ Interop  
 針對.NET 語言，例如 Visual Basic 和 C# 中，與原生元件相互操作的規定的方法是 P/Invoke。 因為.NET Framework 支援 P/Invoke，Visual c + + 也支援，但是 Visual c + + 也有提供自己的互通性支援，指 c + + Interop。 C + + Interop，透過 P/Invoke 因為 P/Invoke 不是類型安全。 如此一來，主要是在執行階段，報告錯誤，但 c + + Interop 也有透過 P/Invoke 的效能優點。  
  
 這兩種技術需要 managed 函式呼叫 unmanaged 函式時，就可能發生的幾件事：  
  
-   函式呼叫引數會以原生類型，封送處理從 CLR。  
  
-   執行 managed 至 unmanaged 的 thunk。  
  
-   Unmanaged 函式呼叫 （使用原生的版本引數）。  
  
-   執行 unmanaged--受管理的 thunk。  
  
-   傳回型別，以及任何 「 出 」 或 「 中，out 」 從原生 CLR 類型會封送處理引數。  
  
 Managed/unmanaged 的 thunk 所需的 interop 運作，但資料封送處理所需取決於相關的資料類型、 函式簽章，以及如何使用資料。  
  
 資料封送處理由 c + + Interop 是最簡單的可能形式： 參數只會複製的 managed/unmanaged 界限之間位元的方式;在不執行任何轉換。 若為 P/Invoke，則只有如果所有參數都是簡單的則為 true blittable 類型。 否則，P/Invoke 執行非常強大的步驟，將每個受管理的參數轉換成適當的原生類型，反之亦然如果引數會標示為"out"，或"中，out"。  
  
 換句話說，c + + Interop 封送處理資料，可能最快速的方法會使用而使用 P/Invoke 會使用最健全的方法。 這表示 c + + Interop (c + + 的典型方式） 根據預設，提供最佳的效能，而且程式設計人員負責定址，此行為不安全或適當的情況。  
  
 C + + Interop 因此需要封送處理資料必須明確提供，但的優點是程式設計人員就可以決定適當的資料本質以及它所使用的方式。 此外，雖然的 P/Invoke 資料封送處理行為可以修改在自訂到某個程度，c + + Interop 能以呼叫由呼叫基礎自訂封送處理的資料。 這是不可能使用 P/Invoke。  
  
 如需 c + + Interop 的詳細資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)