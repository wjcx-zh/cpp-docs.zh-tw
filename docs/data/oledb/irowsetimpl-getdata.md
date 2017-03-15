---
title: "IRowsetImpl::GetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.GetData"
  - "ATL::IRowsetImpl::GetData"
  - "IRowsetImpl::GetData"
  - "IRowsetImpl.GetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetData 方法 [OLE DB]"
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::GetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料列集的資料列複本擷取資料。  
  
## 語法  
  
```  
  
      STDMETHOD( GetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) 。  
  
 有些參數對應至 *OLE DB* 不同的程式設計人員的參考參數，在 **IRowset::GetData**中說明:  
  
|OLE DB 樣板參數|*OLE DB 程式設計人員的傳址參數*|  
|-----------------|--------------------------|  
|*pDstData*|`pData`|  
  
## 備註  
 使用 OLE DB 資料轉換 DLL，因此處理資料轉換。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)