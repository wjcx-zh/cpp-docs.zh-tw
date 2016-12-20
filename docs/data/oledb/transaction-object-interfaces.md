---
title: "異動物件介面 | Microsoft Docs"
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
  - "介面, 清單"
  - "介面, OLE DB"
  - "OLE DB 提供者樣板, 物件介面"
  - "OLE DB 提供者, 異動支援"
  - "OLE DB, 介面"
  - "異動物件介面"
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 異動物件介面
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

交易物件定義資料來源內的原子單位，並決定這些工作單位彼此間的關係。  OLE DB 提供者樣板並不直接支援此物件 \(也就是您必須建立自己的物件\)。  
  
 下表顯示了 OLE DB 為某交易物件所定義的強制和選擇項介面。  
  
|介面|是否為必要項？|是否由 OLE DB 樣板實作？|  
|--------|-------------|----------------------|  
|[\<caps:sentence id\="tgt7" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|強制性|沒有|  
|[\<caps:sentence id\="tgt10" sentenceid\="f5097e646bb93cceb560c38e13953a89" class\="tgtSentence"\>ITransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|強制性|沒有|  
|[\<caps:sentence id\="tgt13" sentenceid\="130702210bcc45e1afd88b1f2aae1a0b" class\="tgtSentence"\>ISupportErrorInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|選擇項|沒有|  
  
## 請參閱  
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)