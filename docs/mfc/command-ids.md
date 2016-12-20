---
title: "命令 ID | Microsoft Docs"
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
helpviewer_keywords: 
  - "命令 ID"
  - "命令 ID, MFC"
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令 ID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

完整命令是由個別其命令 ID 的說明 \(輸入在 **WM\_COMMAND** 訊息\)。  這個 ID 指派給使用者介面物件產生命令。  通常，它們指派的 ID 中名為對於使用者介面物件功能。  
  
 例如，清除編輯功能表上的所有項目都可以指派 ID \( **ID\_EDIT\_CLEAR\_ALL**。  類別庫預先定義一些 ID，特別是架構處理本身的命令，例如 **ID\_EDIT\_CLEAR\_ALL** 或 `ID_FILE_OPEN`。  您將建立其他命令 ID。  
  
 當您建立可在 Visual C\+\+ 的功能表編輯器中的功能表，最好還是遵循類別庫的命名慣例如所說明的是 `ID_FILE_OPEN`。  [標準命令](../mfc/standard-commands.md) 說明類別庫中定義的標準命令。  
  
## 請參閱  
 [使用者介面物件和命令 ID](../mfc/user-interface-objects-and-command-ids.md)