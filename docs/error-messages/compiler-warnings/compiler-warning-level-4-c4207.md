---
title: "編譯器警告 (層級 4) C4207 | Microsoft Docs"
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
  - "C4207"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4207"
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4207
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：擴充形式的初始設定式  
  
 使用 Microsoft 擴充功能 \(\/Ze\)，您可以使用以大括號包夾的字串初始化 `char` 的可變大小陣列 \(Unsized Array\)。  
  
## 範例  
  
```  
// C4207.c  
// compile with: /W4  
char c[] = { 'a', 'b', "cdefg" }; // C4207  
  
int main()  
{  
}  
```  
  
 這樣的初始化設定在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。