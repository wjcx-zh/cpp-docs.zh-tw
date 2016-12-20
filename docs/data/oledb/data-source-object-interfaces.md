---
title: "資料來源物件介面 | Microsoft Docs"
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
  - "資料來源物件 [C++]"
  - "資料來源物件 [C++], 介面"
  - "介面 [C++], 清單"
  - "介面 [C++], OLE DB"
  - "OLE DB [C++], 介面"
  - "OLE DB 提供者樣板 (C++), 物件介面"
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料來源物件介面
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表顯示 OLE DB 為某資料來源物件所定義的強制和選擇項介面。  
  
|介面|是否為必要項？|是否由 OLE DB 樣板實作？|  
|--------|-------------|----------------------|  
|`IDBCreateSession`|強制性|有|  
|`IDBInitialize`|強制性|有|  
|`IDBProperties`|強制性|有|  
|[\<caps:sentence id\="tgt14" sentenceid\="731a3344bc1c6b5f8f54d9de3524f18a" class\="tgtSentence"\>IPersist\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms688695)|強制性|有|  
|[\<caps:sentence id\="tgt17" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|選擇項|沒有|  
|`IDBDataSourceAdmin`|選擇項|沒有|  
|`IDBInfo`|選擇項|沒有|  
|[\<caps:sentence id\="tgt26" sentenceid\="7e6a12ecd4cb3b1bd45dccf9421ed567" class\="tgtSentence"\>IPersistFile\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms687223)|選擇項|沒有|  
|`ISupportErrorInfo`|選擇項|沒有|  
  
 資料來源物件將經由繼承實作 `IDBProperties`、`IDBInitialize` 和 `IDBCreateSession` 介面。  您可選擇繼承或不從這些實作類別之一繼承，來支援其他的功能。  如果您要支援 `IDBDataSourceAdmin` 介面，則必須自 `IDBDataSourceAdminImpl` 類別繼承。  
  
## 請參閱  
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)