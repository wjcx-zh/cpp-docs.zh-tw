---
title: "Marshaling | Microsoft Docs"
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
  - "COM 介面, 封送處理"
  - "封送處理"
  - "封送處理, COM Interop"
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Marshaling
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

封送處理 COM 技術可以讓在其他處理序的處理序的物件所公開的介面。  在封送處理， COM 提供了程式碼 \(或介面實作器所提供的程式碼\) 會使用兩個包裝方法的參數傳遞至可跨處理序移動的格式 \(以及，跨負責對其他電腦\) 的處理序的連線及開啟這些參數從另一端。  同樣地， COM 物件必須實作中傳回的這些步驟從呼叫。  
  
> [!NOTE]
>  當物件所提供的介面是用來與物件相同的處理序時，封送處理通常不是必要的。  不過，封送處理可能需要在執行緒之間。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [Marshaling Details](http://msdn.microsoft.com/library/windows/desktop/ms692621)