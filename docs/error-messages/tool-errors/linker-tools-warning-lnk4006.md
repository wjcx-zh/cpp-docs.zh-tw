---
title: "連結器工具警告 LNK4006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4006"
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具警告 LNK4006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

symbol 已經定義於 object；忽略第二個定義  
  
 指定的 `symbol` \(以裝飾形式顯示\) 已有個多個定義。  當您遇見這個警告時，表示已將 `symbol` 加入了兩次，但只有第一次加入的會被採用。  
  
 如果您嘗試將兩個匯入程式庫合併為一個，就會發生這個警告。  
  
 如果您是要重建 C 執行階段程式庫，請忽略這個訊息。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  指定的 `symbol` 可能是以 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 編譯建立的封裝函式 \(Packaged Function\)。  這個符號包含於多個檔案中，但在編譯時被變更。  請重新編譯包含此 `symbol` 的所有檔案。  
  
2.  指定的 `symbol` 在不同程式庫中可能有不同的定義。  
  
3.  同一絕對值可能被定義了兩次，且每次的定義值都不同。  
  
4.  如果在合併程式庫時收到錯誤訊息，表示 `symbol` 已存在於將要加入的程式庫中。