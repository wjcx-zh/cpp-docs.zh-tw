---
title: "使用 CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "CObject 類別"
  - "衍生類別, 來自 CObject"
  - "範例 [MFC], CObject"
  - "MFC, 基底類別"
  - "MFC 的根基底類別"
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 使用 CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CObject](../mfc/reference/cobject-class.md) 是大部分的根基底類別 MFC 程式庫。  `CObject` 類別包含您可以合併到您的程式物件，包含序列化支援，執行階段類別資訊，並針對診斷輸出的許多有用的功能。  如果您從 `CObject`衍生您自己的類別，該類別可利用這些 `CObject` 功能。  
  
## 您想要執行甚麼工作？  
  
-   [從衍生自 CObject 的類別](../mfc/deriving-a-class-from-cobject.md)  
  
-   [加入對對於執行階段類別資訊、動態建立和序列化至我的衍生類別。](../mfc/specifying-levels-of-functionality.md)  
  
-   [存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)  
  
-   [動態建立物件](../mfc/dynamic-object-creation.md)  
  
-   [傾印物件的資料以供診斷之用。](http://msdn.microsoft.com/zh-tw/727855b1-5a83-44bd-9fe3-f1d535584b59)  
  
-   驗證物件的內部狀態 \(請參閱 [MFC ASSERT\_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/zh-tw/7654fb75-9e9a-499a-8165-0a96faf2d5e6)\)。  
  
-   [讓類別序列化至持續性儲存體。](../mfc/serialization-in-mfc.md)  
  
-   請參閱 [CObject 常見問題集](../mfc/cobject-class-frequently-asked-questions.md)清單  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CRuntimeClass Structure](../mfc/reference/cruntimeclass-structure.md)   
 [檔案](../mfc/files-in-mfc.md)   
 [序列化](../mfc/serialization-in-mfc.md)