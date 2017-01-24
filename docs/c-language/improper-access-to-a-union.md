---
title: "不適當的等位存取 | Microsoft Docs"
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
  - "C"
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 不適當的等位存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3.2.3**：使用不同類型的成員存取等位物件的成員  
  
 如果宣告了兩種類型的等位並且儲存一個值，但等位是以另一種類型存取，則結果不可靠。  
  
 例如，宣告了 **float** 和 `int` 的等位。  儲存了 **float** 值，但是程式之後將值當做 `int` 存取。  在這種情況下，值會取決於 **float** 值的內部儲存區。  整數值會變得不可靠。  
  
## 請參閱  
 [結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)