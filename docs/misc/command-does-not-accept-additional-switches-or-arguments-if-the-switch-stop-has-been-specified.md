---
title: "Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00CD"
  - "vs.message.VS_E_NOTVALIDWITHSTOP"
ms.assetid: 1dea2450-034e-4a7f-b959-2060811329b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified.
當 `/stop` 參數與 \[檔案中尋找\] 或 \[檔案中取代\] 命令的其他參數同時輸入時，通常會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
1.  如果要停止目前 \[檔案中尋找\] 作業，請輸入：  
  
    ```  
    Edit.FindinFiles /stop.  
    ```  
  
2.  如果要停止目前 \[檔案中取代\] 作業，請輸入：  
  
    ```  
    Edit.ReplaceinFiles /stop  
    ```  
  
3.  如果要開始新的 \[檔案中尋找\] 或 \[檔案中取代\] 作業，請重新輸入命令並省略 `/stop`。  
  
## 請參閱  
 [檔案中取代命令](../Topic/Replace%20In%20Files%20Command.md)   
 [檔案中尋找命令](../Topic/Find%20in%20Files%20Command.md)   
 [Visual Studio 命令](../Topic/Visual%20Studio%20Commands.md)