---
title: "編譯器警告 (層級 4) C4710 | Microsoft Docs"
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
  - "C4710"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4710"
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4710
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 未內嵌函式  
  
 已選取提供的函式進行內嵌擴充，但編譯器未進行內嵌。  
  
 編譯器會判斷是否進行內嵌。  **inline** 關鍵字正如 **register** 關鍵字一般是給編譯器的提示。  編譯器會使用 Heuristic 來決定當針對速度編譯時，是否應該內嵌特定的函式以加快程式碼，或是當針對空間編譯時，是否應該內嵌特定的函式以使程式碼更小。  當編譯器針對空間編譯時，只會內嵌非常小的函式。  
  
 在某些情況下，編譯器因為技術方面的因素而不會內嵌特定的函式。  如需了解編譯器不會內嵌函式的因素，請參閱 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。