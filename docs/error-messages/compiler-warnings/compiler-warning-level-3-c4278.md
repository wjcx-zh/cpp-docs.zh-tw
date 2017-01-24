---
title: "編譯器警告 (層級 3) C4278 | Microsoft Docs"
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
  - "C4278"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4278"
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4278
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 型別程式庫 'tlb' 中的識別項已經是巨集; 使用 'rename' 限定詞  
  
 使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 時，您匯入的 Typelib 中的識別項正在嘗試宣告識別項 ***identifier***。  然而，它已經是有效的符號。  
  
 使用 `#import` **rename** 屬性指派別名給型別程式庫中的符號。