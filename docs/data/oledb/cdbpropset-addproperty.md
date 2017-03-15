---
title: "CDBPropSet::AddProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropSet::AddProperty"
  - "CDBPropSet.AddProperty"
  - "AddProperty"
  - "ATL::CDBPropSet::AddProperty"
  - "ATL.CDBPropSet.AddProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty 方法"
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDBPropSet::AddProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將屬性加入至屬性集合。  
  
## 語法  
  
```  
  
      bool AddProperty(   
   DWORD dwPropertyID,   
   const VARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCSTR szValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCWSTR szValue,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   bool bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   BYTE bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   short nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   long nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   float fltValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   double dblValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   CY cyValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
```  
  
#### 參數  
 *dwPropertyID*  
 \[要加入之屬性的 ID。  用來初始化 `DBPROP` 結構的 **dwPropertyID** 加入至屬性集合。  
  
 `var`  
 \[用於的變數初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 `szValue`  
 \[用於的字串初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 `bValue`  
 \[用來 **BYTE** 或布林值初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 `nValue`  
 \[用於整數值初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 *fltValue*  
 \[用於的浮點值初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 `dblValue`  
 \[用於的雙精確度浮點值初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
 `cyValue`  
 \[A CY 用於貨幣值初始化 `DBPROP` 結構的屬性值加入至屬性集合。  
  
## 傳回值  
 **true** ，如果屬性已成功加入。  否則為 **false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBPropSet 類別](../../data/oledb/cdbpropset-class.md)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)