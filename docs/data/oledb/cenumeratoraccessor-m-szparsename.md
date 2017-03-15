---
title: "CEnumeratorAccessor::m_szParseName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CEnumeratorAccessor::m_szParseName"
  - "ATL::CEnumeratorAccessor::m_szParseName"
  - "m_szParseName"
  - "CEnumeratorAccessor.m_szParseName"
  - "ATL.CEnumeratorAccessor.m_szParseName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_szParseName"
ms.assetid: 32e826b6-0890-4db4-aa92-fc1ea3f528b2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumeratorAccessor::m_szParseName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用來傳遞給 [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) 的字串，可得到資料來源或列舉值的 Moniker。  
  
## 語法  
  
```  
  
WCHAR m_szParseName[129];  
  
```  
  
## 備註  
 請參閱 *OLE DB 程式設計人員參考資訊* 的 [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx) 以取得詳細資訊。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CEnumeratorAccessor 類別](../../data/oledb/cenumeratoraccessor-class.md)