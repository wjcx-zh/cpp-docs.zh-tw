---
title: "Windows Sockets 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.net"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通訊端類別"
  - "Windows Sockets [C++], 類別"
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows Sockets 提供一個網路通訊協定獨立模式在這兩部電腦之間溝通。  這些通訊端可以是同步的 \(您的程式會等待直到完成通訊\) 或非同步 \(當通訊繼續，您的程式繼續執行\)。  
  
 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)  
 在精簡包裝函式中封裝 Windows Sockets API。  
  
 [CSocket](../mfc/reference/csocket-class.md)  
 從 `CAsyncSocket` 衍生的高階抽象。  它會同步地作業。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 提供 `CFile` 介面給 Windows Sockets。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)