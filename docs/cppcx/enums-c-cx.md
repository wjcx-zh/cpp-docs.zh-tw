---
title: "列舉 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 14
---
# 列舉 (C++/CX)
[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 支援 `public enum class` 關鍵字，類似於標準 C\+\+ `scoped  enum`。 當您使用以 `public enum class` 關鍵字所宣告的列舉程式時，您必須使用列舉識別項來限定每一個列舉值的範圍。  
  
## 備註  
 不具有存取規範 \(例如 `public enum class`\) 的 `public` 視為標準 C\+\+ [限定範圍列舉](../Topic/Enumerations%20\(C++\).md)。  
  
 雖然 `public enum class`本身要求類型必須為 int32，或旗標列舉的 uint32，但 `public enum struct` 或 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 宣告可以具有任何整數類型的基礎類型。 下列語法描述 `public enum class` 或 `public enum struct` 的部分。 如需詳細資訊，請參閱[enum class](../Topic/enum%20class%20%20\(C++%20Component%20Extensions\).md)。  
  
 本範例示範如何定義公用列舉類別：  
  
 [!code-cpp[cx_enums#01](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#01)]  
  
 下一個範例示範如何使用該類別：  
  
 [!code-cpp[cx_enums#02](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#02)]  
  
## 範例  
 下面的範例示範如何宣告列舉，  
  
 [!code-cpp[cx_enums#03](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#03)]  
  
 下一個範例示範如何轉型為數值對應項及執行比較。 請注意，列舉程式 `One` 由 `Enum1` 列舉識別項界定使用範圍，列舉程式 `First` 由 `Enum2` 界定範圍。  
  
 [!code-cpp[cx_enums#04](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#04)]  
  
## 請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)