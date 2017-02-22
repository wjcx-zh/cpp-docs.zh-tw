---
title: "命令修飾詞 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令修飾詞"
  - "NMAKE 程式, 命令修飾詞"
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 命令修飾詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在命令之前指定一或多個命令修飾詞，由空格或定位字元選擇性的分隔開。  修飾詞在和命令一起時必須縮排。  
  
|修飾詞|用途|  
|---------|--------|  
|@*command*|防止顯示命令。  不隱藏命令所顯示的訊息。  根據預設，NMAKE 會回應所有執行的命令。  使用 \/S 隱藏顯示整個 Makefile，使用 **.SILENT** 隱藏顯示部分的 Makefile。|  
|**–**\[`number` \]*command*|關閉命令的錯誤檢查。  根據預設，當命令傳回非零的結束代碼時，NMAKE 會暫停。  如果使用–`number`，若結束代碼超過 `number`，NMAKE 就會停止。  空格或定位字元不能出現在破折號和號碼之間。至少一個空格或定位字元必須出現在 `number` 和 *command* 之間。  使用 \/I 關閉整個 Makefile 的錯誤檢查，使用 **.IGNORE** 關閉部分 Makefile 的錯誤檢查。|  
|**\!** *command*|如果命令使用 **$\*\*** \(在相依性中的所有相依檔案\) 或 **$?** \(在相依性中，具有比目標晚的時間戳記的所有相依檔案\)，就會執行每個相依檔案的命令。|  
  
## 請參閱  
 [Makefile 中的命令](../build/commands-in-a-makefile.md)