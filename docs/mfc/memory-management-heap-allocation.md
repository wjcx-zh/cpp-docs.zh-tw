---
title: "記憶體管理：堆積配置 | Microsoft Docs"
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
  - "delete 運算子, 與偵錯 MFC 一起使用"
  - "偵測記憶體流失"
  - "堆積配置"
  - "堆積配置, 說明"
  - "記憶體配置, 堆積記憶體"
  - "記憶體遺漏, 偵測"
  - "記憶體, 偵測流失"
  - "new 運算子, 與偵錯 MFC 一起使用"
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 記憶體管理：堆積配置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

堆積為程式的記憶體配置需要而保留。  這是程式碼和堆疊之外的區域。  典型的 C 程式使用函式 `malloc` 和 **free** 配置和解除配置堆積記憶體。  MFC 偵錯版本提供 C\+\+ 內建運算子 **new** 和 **delete** 的修改版本以配置和解除配置在堆積記憶體的物件。  
  
 當您使用 **new** 和 **delete** 而非 `malloc` 和 **free**時，您可以使用類別庫的記憶體管理偵錯加強功能，可用於偵測記憶體遺漏。  當您以 MFC 發行版本建構程式， **new** 和 **delete** 運算子的標準版本提供高效的配置和解除配置記憶體方法 \(MFC 發行版本不提供這些運算子修改版本\)。  
  
 請注意堆積上物件配置的總大小由您系統上可用的虛擬記憶體限制。  
  
## 請參閱  
 [記憶體管理](../mfc/memory-management.md)