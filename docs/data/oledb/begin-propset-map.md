---
title: "BEGIN_PROPSET_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_PROPSET_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROPSET_MAP 巨集"
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_PROPSET_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記屬性集對應項目的開頭。  
  
## 語法  
  
```  
  
BEGIN_PROPSET_MAP(  
Class   
)  
  
```  
  
#### 參數  
 *類別*  
 \[的這個屬性中所指定的類別。  屬性在下列 OLE DB 物件可指定:  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="75bbb794f21139fcd243c18fff6050d2" class\="tgtSentence"\>資料來源物件\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="e423b0fba10fc83bd76e01e3eee2fd69" class\="tgtSentence"\>工作階段物件\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="5f6bc08c46cee6f21bfcdd08aff6e8aa" class\="tgtSentence"\>命令\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## 範例  
 這個範例屬性集對應:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/CPP/begin-propset-map_1.h)]  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)