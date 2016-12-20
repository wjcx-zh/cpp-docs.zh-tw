---
title: "內部連結 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "內部連結"
  - "連結 [C++], internal"
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 內部連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果某物件或函式的檔案範圍識別項宣告包含 *storage\-class\-specifier* **static**，則該識別項具有內部連結。  否則，該識別項會具有外部連結。  如需 *storage\-class\-specifier* 非終端項的討論，請參閱[儲存類別](../c-language/c-storage-classes.md)。  
  
 在一個轉譯單位中，具有內部連結之識別項的每個執行個體表示相同的識別項或函式。  內部連結的識別項在轉譯單位中是唯一的。  
  
## 請參閱  
 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)