---
title: "編譯器警告 (層級 4) C4211 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4211"
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：將 extern 重新定義為靜態  
  
 使用預設的 Microsoft 擴充功能 \(\/Ze\)，您可以將 `extern` 識別項重新定義為**靜態**。  
  
## 範例  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 這樣的重新定義在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。  
  
## 請參閱  
 [\(NOTINBUILD\)Static Storage\-Class Specifiers](http://msdn.microsoft.com/zh-tw/3ba9289a-a412-4a17-b319-ceb2c087df48)