---
title: "編譯器警告 (層級 1) CS3013 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3013
加入的模組必須以 CLSCompliant 屬性標記，才能與這個組件相符  
  
 已使用 [\/addmodule](../Topic/-addmodule%20\(C%23%20Compiler%20Options\).md)，將使用 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 編譯器選項所編譯的模組加入編譯。 不過，模組與 Common Language Specification \(CLS\) 的符合性，與目前編譯的 CLS 狀態不一致。  
  
 CLS 相容性是使用模組屬性所表示。 例如，`[module:CLSCompliant(true)]` 表示模組符合 CLS 標準，而 `[module:CLSCompliant(false)]` 表示模組不符合 CLS 標準。 預設為 `[module:CLSCompliant(false)]`。 如需 CLS 的詳細資訊，請參閱[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。