---
title: "編譯器錯誤 C3859 | Microsoft Docs"
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
  - "C3859"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3859"
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3859
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

超出 PCH 的虛擬記憶體範圍；請使用等於或大於 '\-Zmvalue' 的命令列選項重新編譯  
  
 先行編譯的標頭對編譯器正在嘗試放入其中的資料量而言太小。  使用 **\/Zm** 編譯器旗標，為先行編譯的標頭檔指定較大的值。  如需詳細資訊，請參閱 [\/Zm \(指定先行編譯標頭檔的記憶體配置上限\)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。