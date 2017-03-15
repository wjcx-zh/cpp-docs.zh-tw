---
title: "編譯器警告 (層級 1) C4182 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4182"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4182"
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4182
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#include 具有 'number' 層的巢狀層次，可能會造成無限遞迴  
  
 編譯器已用完堆積上的空間，因為巢狀 Include 檔數目太多。 當從另一個 Include 檔包含 Include 檔時即為巢狀 Include 檔。  
  
 這個訊息僅供參考，而且前面出現錯誤 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)。