---
title: "內建和內嵌組譯 | Microsoft Docs"
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
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 內建和內嵌組譯
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 編譯器的其中一項限制就是沒有內嵌組合語言 \(Inline Assembler\) 的支援。  這表示無法用 C 或 C\+\+ 撰寫的函式必須撰寫為編譯器支援的副程式或內建函式。  某些函式並不注重效能，但是其他的則會。  注重效能的函式應該要實作為內建函式。  
  
 編譯器所支援的內建函式，會在[編譯器內建函式](../intrinsics/compiler-intrinsics.md)中說明。  
  
## 請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)