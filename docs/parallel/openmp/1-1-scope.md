---
title: "1.1 Scope | Microsoft Docs"
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
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.1 Scope
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這項規格涵蓋只使用者導向的平行，移位，其中使用者明確地指定要以平行方式執行的程式，編譯器和執行階段系統所採取的動作。  OpenMP c 和 C\+\+ 的實作系統就不一定要檢查相依性、 衝突、 死結、 競爭情形、 或其他問題，導致不正確的程式執行。  使用者要負責確保使用 OpenMP C 和 C\+\+ API 建構的應用程式正常執行。  這份文件中沒有涵蓋編譯器產生自動平行處理，並對編譯器指示詞，來協助這類的平行化。