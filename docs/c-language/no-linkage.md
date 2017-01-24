---
title: "無連結 | Microsoft Docs"
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
  - "連結 [C++], 無"
  - "無連結"
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 無連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果區塊中某個識別項的宣告並未包含 `extern` 儲存類別指定名稱，則不會連結識別項，且該識別項在函式中是唯一的。  
  
 下列識別項不會進行連結：  
  
-   除了物件或函式之外，可項識別項宣告為任何項目  
  
-   宣告為函式參數的識別項  
  
-   已宣告不含 `extern` 儲存類別指定名稱之物件的區塊範圍識別項  
  
 如果識別項未連結，則在相同範圍層級中再次宣告相同名稱 \(在宣告子或類型指定名稱中\) 會產生符號重新定義錯誤。  
  
## 請參閱  
 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)