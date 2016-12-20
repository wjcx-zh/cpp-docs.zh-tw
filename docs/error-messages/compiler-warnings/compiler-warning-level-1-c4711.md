---
title: "編譯器警告 (層級 1) C4711 | Microsoft Docs"
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
  - "C4711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4711"
ms.assetid: 270506ab-fead-4328-b714-2978113be238
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式 'function' 被指定為自動內嵌展開  
  
 編譯器對提供的函式進行內嵌，即使該函式並未標記為內嵌。  
  
 如果指定[\/Ob2](../../build/reference/ob-inline-function-expansion.md)，便會啟用 C4711。  
  
 編譯器會判斷是否進行內嵌。  這項警告僅供參考，  
  
 此警告在預設情況下為關閉的。  若要啟用警告，請使用 [\#pragma warning](../../preprocessor/warning.md)。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。