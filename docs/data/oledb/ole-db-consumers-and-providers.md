---
title: "OLE DB 消費者和提供者 | Microsoft Docs"
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
  - "OLE DB 消費者"
  - "OLE DB 消費者, OLE DB 資料架構"
  - "OLE DB 提供者"
  - "OLE DB 提供者, OLE DB 資料架構"
  - "OLE DB, 資料模型"
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 消費者和提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 架構使用消費者和提供者模型。  消費者提出資料的要求。  提供者會以表格的格式放置資料，並將其傳回給消費者，做為這些要求的回應。  消費者提出的所有呼叫必須實作在提供者中。  
  
 就技術定義來說，消費者是任一個透過 OLE DB 介面存取資料的系統或應用程式碼 \(不一定是 OLE DB 元件\)。  而介面實作於提供者上。  因此，提供者是實作 OLE DB 介面的軟體元件，它會將資料的存取封裝起來並將其公開給其他物件 \(也就是消費者\)。  
  
 以角色來說，消費者呼叫 OLE DB 介面上的方法，而 OLE DB 提供者實作所需的 OLE DB 介面。  
  
 OLE DB 會避免用戶端和伺服器的詞彙，因為這些角色並不是一直合理的，尤其是在多層式架構 \(N\-Tier\) 的情況下。  因為消費者這個元件可能是位於服務其他元件的層上的元件，所以稱它為用戶端元件可能會造成混淆。  而且，有時候提供者的動作比較像是資料庫驅動程式而不像是伺服器。  
  
## 請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)