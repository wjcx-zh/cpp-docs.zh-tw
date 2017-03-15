---
title: "編譯器警告 (層級 1) C4067 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4067"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4067"
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4067
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的語彙基元，接著前置處理器指示詞 \- 必須是新行  
  
 編譯器找到並忽略前置處理器指示詞之後額外的字元。  這項警告僅出現在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 中。  
  
```  
// C4067a.cpp  
// compile with: /DX /Za /W1  
#pragma warning(default:4067)  
#if defined(X)  
#else  
#endif v   // C4067  
int main()  
{  
}  
```  
  
### 若要解決這個警告，請嘗試下列步驟：  
  
1.  使用 **\/Ze** 編譯。  
  
2.  使用註解分隔符號 \(Comment Delimiter\)：  
  
```  
// C4067b.cpp  
// compile with: /DX /Za /W1  
#if defined(X)  
#else  
#endif  
int main()  
{  
}  
```