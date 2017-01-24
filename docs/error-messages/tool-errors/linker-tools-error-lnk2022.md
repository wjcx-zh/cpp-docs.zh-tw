---
title: "連結器工具錯誤 LNK2022 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2022"
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

中繼資料作業失敗 \(HRESULT\)：error\_message  
  
 連結器合併中繼資料時偵測到錯誤。  中繼資料錯誤必須解決，才能連結成功。  
  
 診斷這個問題的其中一種方式是：在目的檔上執行 **ildasm –tokens**，以找出具有列在 `error_message` 中之語彙基元的型別，並尋找其差異。在中繼資料內，具有相同名稱的兩個不同型別無效，即使只有 LayoutType 屬性不同，也一樣無效。  
  
 造成 LNK2022 的其中一個原因是：當你以 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯時，型別 \(例如 struct\) 在多個編譯單位中有相同名稱，但定義不同而相衝突。在此情況下，請確定型別在所有編譯中都有完全相同的定義。型別名稱會列於 `error_message` 之中。  
  
 另一個可能造成 LNK2022 錯誤的原因是，連結器在不同於指定給編譯器 \(以 [\#using](../../preprocessor/hash-using-directive-cpp.md)\) 的位置找到中繼資料檔。  確保中繼資料\(.dll或 .netmodule\) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。  
  
 建置 ATL 應用程式時，只要其中一個編譯單位使用到 [\_ATL\_MIXED](../Topic/_ATL_MIXED.md)，則所有編譯單位都必須使用。  
  
## 範例  
 以下範例會定義空型別。  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## 範例  
 這個範例示範了您不能連結兩個包含相同名稱但不同定義之型別的原始程式碼。  
  
 下列範例會產生 LNK2022。  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```