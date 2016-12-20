---
title: "錯誤: 無法將專案 &#39;project&#39; 中的相依性 &#39;file&#39; 複製至執行目錄，因為它會和相依性 &#39;file&#39; 衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 錯誤: 無法將專案 &#39;project&#39; 中的相依性 &#39;file&#39; 複製至執行目錄，因為它會和相依性 &#39;file&#39; 衝突
參考之間發生衝突；正在將多個同名的相異相依性複製到 bin 目錄，以執行應用程式。 由於沒有相依性是主要參考，因此執行目錄無法解決衝突。  
  
 此錯誤會導致建置失敗。  
  
 按兩下此工作清單項目，可前往發生衝突之專案的參考節點。  
  
 **更正這個錯誤**  
  
-   將其中一個組件設為專案的直接參考。 這個方法的可能缺點是，不保證您選擇的組件可以搭配需要其他版本參考組件的組件使用。  
  
     \-或\-  
  
-   確定組件的兩個複本都是以強式名稱的方式命名，並且位於全域組件快取中。 如此一來便不需要將組件複製到 bin 目錄。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [全域組件快取](../Topic/Global%20Assembly%20Cache.md)   
 [強式名稱的組件](../Topic/Strong-Named%20Assemblies.md)   
 [組件版本控制](../Topic/Assembly%20Versioning.md)   
 [如何：建立和移除專案相依性](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)