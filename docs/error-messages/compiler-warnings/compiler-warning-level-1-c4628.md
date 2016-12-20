---
title: "編譯器警告 (層級 1) C4628 | Microsoft Docs"
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
  - "C4628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4628"
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支援使用 \-Ze 的雙拼詞。字元順序 'digraph' 沒有解譯為 'char' 的替代語彙基元 \(Token\)  
  
 在 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 下，不支援雙拼詞。  這個警告後將會出現錯誤訊息。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4628：  
  
```  
// C4628.cpp  
// compile with: /WX  
#pragma warning(default : 4628)  
int main()  
<%   // C4628 <% digraph for {  
}  
```