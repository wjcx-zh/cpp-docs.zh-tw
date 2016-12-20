---
title: "嚴重錯誤 C1047 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1047"
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

物件或程式庫檔案 'file' 是使用比其他物件更舊的編譯器建立的，請重建舊物件和程式庫  
  
 如果由 **\/LTCG** 所建置的目的檔或程式庫連結在一起，但這些目的檔或程式庫是使用不同版本的 Visual C\+\+ 工具組所建置，則會造成 C1047。  
  
 如果您開始使用新版本的編譯器，但不會執行現有目的檔或程式庫的全新重建，則可能會發生這種情況。  
  
 若要解決 C1047，請重建所有目的檔或程式庫。