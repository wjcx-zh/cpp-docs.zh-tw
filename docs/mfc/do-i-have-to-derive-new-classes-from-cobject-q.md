---
title: "我必須從 CObject 衍生新類別嗎？ | Microsoft Docs"
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
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 類別, 使用時機"
  - "衍生類別, 來自 CObject"
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 我必須從 CObject 衍生新類別嗎？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不，你不會。  
  
 從 [CObject](../mfc/reference/cobject-class.md) 衍生它提供的類別，當您需要功能時，例如序列化或動態創造。  許多資料類別需要序列化至檔案，因此通常是很好的作法是從 `CObject`取得它們。  如需從 `CObject`衍生之類別的範例，請參閱 [Scribble 範例](../top/visual-cpp-samples.md)。  
  
## 請參閱  
 [CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)