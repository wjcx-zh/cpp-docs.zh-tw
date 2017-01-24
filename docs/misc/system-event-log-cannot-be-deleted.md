---
title: "無法刪除系統事件記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法刪除系統事件記錄檔
嘗試刪除無法刪除的系統事件記錄檔。 系統記錄檔可追蹤系統事件 \(例如系統啟動和硬體故障\)。  
  
### 更正這個錯誤  
  
-   請考慮讓應用程式寫入至應用程式或自訂記錄檔，而不是系統事件記錄檔。  
  
-   請不要嘗試刪除系統事件記錄檔。  
  
## 請參閱  
 [Administering Event Logs](http://msdn.microsoft.com/zh-tw/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/zh-tw/af9b7da0-80c7-46ac-b7f7-897063ddd503)