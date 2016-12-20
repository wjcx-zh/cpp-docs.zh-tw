---
title: "編譯器警告 (層級 4) C4289 | Microsoft Docs"
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
  - "C4289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4289"
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：'var' : 在 for\-loop 範圍外使用 for\-loop 中所宣告的迴圈控制變數  
  
 利用 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 **\/Zc:forScope\-** 編譯時，在 **for** 迴圈範圍之後會使用於 [for](../../cpp/for-statement-cpp.md) 迴圈中宣告的變數。  
  
 如需關於如何在 **for** 迴圈中用 **\/Ze** 指定標準行為的詳細資訊，請參閱 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4289：  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```