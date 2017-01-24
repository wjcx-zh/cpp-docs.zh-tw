---
title: "編譯器警告 (層級 3) CS0414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0414"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0414"
ms.assetid: 6a0a80be-799b-4d9c-a7e0-6b91e9ce7be0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0414
已指派私用欄位 'field'，但從未使用過其值  
  
 此警告可能發生在下列若干案例中，其中編譯器可確認永遠不會參考某個變數：  
  
-   私用欄位已指派常數值，但絕不會接著讀取。 不必要的指派可能會影響效能。 請考慮移除欄位。  
  
-   只在初始設定式中，才為私用或內部靜態欄位指派常數值。 請考慮將欄位變更為常數。  
  
-   私用或內部欄位已指派常數值，而且只用於 \#ifdef 指示詞排除的區塊。 請考慮將欄位放到 \#ifdef 區塊內。  
  
-   私用或內部欄位的多個位置中已指派常數值，但卻無法存取。 如果您不需要欄位，請考慮將它移除。 否則，請以適當的方式來使用欄位。  
  
 若為其他情況或不接受建議之因應措施的情況下，請使用 \#pragma 0414。  
  
 下列範例顯示會產生 CS0414 的其中一種情況：  
  
```  
// CS0414 // compile with: /W3 class C { private int i = 1;  // CS0414 public static void Main() { } }  
```  
  
 **注意**：如果變數 `i` 宣告為 `protected or public`，則由於編譯器無法確定是否衍生的類別會使用它，或其他用戶端程式碼是否會具現化相關類別並參考相關變數，因此不會產生任何錯誤  
  
## 請參閱  
 [C\# Compiler Errors](../Topic/C%23%20Compiler%20Errors.md)   
 [C\# Compiler Options](../Topic/C%23%20Compiler%20Options.md)