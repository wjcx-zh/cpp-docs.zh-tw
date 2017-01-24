---
title: "內部層級宣告的儲存類別規範 | Microsoft Docs"
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
  - "內部連結, 儲存類別規範"
  - "儲存類別規範, internal"
ms.assetid: feca8ab5-23df-4b6c-921a-4d51f9be35d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 內部層級宣告的儲存類別規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您只能在內部層級使用四個 *storage\-class\-specifier* 終端當中的任何一個進行變數宣告。  如果您省略此類宣告中的 *storage\-class\-specifier*，預設儲存類別會是 **auto**。  因此，C 程式很少使用 **auto** 關鍵字。  
  
## 請參閱  
 [C 儲存類別](../c-language/c-storage-classes.md)