---
title: "命令物件介面 | Microsoft Docs"
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
  - "命令物件介面 [C++]"
  - "命令物件 [OLE DB]"
  - "OLE DB [C++], 命令物件介面"
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令物件介面
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此命令物件會使用 `IAccessor` 介面來指定參數繫結。  消費者將呼叫 `IAccessor::CreateAccessor`，並將 `DBBINDING` 結構陣列傳遞給它。  `DBBINDING` 包含了資料行繫結的資訊 \(例如型別和長度\)。  提供者會接收此結構，並判斷資料傳送方式以及是否需要轉換。  
  
 `ICommandText` 介面提供一種指定文字命令的方式。  `ICommandProperties` 介面可處理所有的命令屬性。  
  
## 請參閱  
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)