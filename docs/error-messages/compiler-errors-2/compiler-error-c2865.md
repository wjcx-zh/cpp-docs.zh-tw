---
title: "編譯器錯誤 C2865 | Microsoft Docs"
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
  - "C2865"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2865"
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2865
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 對 handle\_or\_pointer 不合法的比較  
  
 您只能對 [Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md) 或 [\_\_gc](../../misc/gc.md) 型別的參考進行相等性比較，查看它們是參考相同的物件 \(\=\=\) 或不同的物件 \(\!\=\)。  
  
 您不能比較它們的順序，因為 .NET Runtime 可能會於任何時間移動 Managed 物件，變更測試的結果。