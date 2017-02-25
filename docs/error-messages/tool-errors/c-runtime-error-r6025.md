---
title: "C 執行階段錯誤 R6025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6025"
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# C 執行階段錯誤 R6025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

純虛擬函式呼叫  
  
 沒有將任何物件執行個體化來處理純虛擬函式 \(Pure Virtual Function\) 呼叫。  
  
 如果您在應用程式中看到這個錯誤，請連絡應用程式的技術支援部門。  
  
 此錯誤會發生，是因為使用指向衍生類別的指標 \(透過型別轉換建立\) 來呼叫抽象基底類別中的虛擬函式 \(Virtual Function\)，但是該指標實際上是指向基底類別的指標。  當 **void\*** 是在基底類別的建構過程中所建立，並且將 **void\*** 轉換為指向類別的指標時就會發生此錯誤。  
  
 如需詳細資訊，請參閱 [Microsoft 支援](http://go.microsoft.com/fwlink/?LinkId=75220)網站。