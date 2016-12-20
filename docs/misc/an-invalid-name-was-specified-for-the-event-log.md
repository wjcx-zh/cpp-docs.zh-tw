---
title: "指定給事件記錄檔的名稱無效 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 指定給事件記錄檔的名稱無效
指定給事件記錄檔的名稱無效。 這通常是名稱中有無效的字元、檔案名稱空白或檔案名稱太長的結果。  
  
### 更正這個錯誤  
  
-   如果指定的名稱超過八個字元，請確定該名稱未與其他事件記錄檔的名稱相衝突。 判斷此名稱是否唯一時，只會評估前八個字元。  
  
-   如果提供路徑，請確定已正確地剖析該路徑。  
  
-   檢查名稱中沒有無效的字元。 不能在檔案名稱中使用的字元包括 `<`、`>`、`:`、`"`、`/`、`\` 和 `|`。  
  
## 請參閱  
 [如何：剖析檔案路徑](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)   
 [How to: Rename a File](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/zh-tw/af9b7da0-80c7-46ac-b7f7-897063ddd503)