---
title: "static 儲存類別規範 | Microsoft Docs"
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
  - "靜態儲存類別規範"
  - "靜態變數, 規範"
  - "儲存類別, static"
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# static 儲存類別規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在內部層級使用 **static** 儲存類別指定名稱宣告的變數具有全域存留期，但是只有在宣告該變數的區塊內才看得見。  若是常數字串，使用 **static** 會很有用，因為它可減輕經常呼叫的函式中經常需要初始化的額外負荷。  
  
## 備註  
 如果您未明確初始化 **static** 變數，該變數預設會初始化為 0。  在函式內，**static** 會配置儲存區並且做為定義。  內部靜態變數會提供只有單一函式可見的私用永久儲存區。  
  
## 請參閱  
 [Static](../misc/static-cpp.md)