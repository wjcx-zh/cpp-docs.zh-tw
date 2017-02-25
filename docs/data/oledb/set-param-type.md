---
title: "SET_PARAM_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SET_PARAM_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SET_PARAM_TYPE 巨集"
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# SET_PARAM_TYPE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 `COLUMN_ENTRY` 巨集輸入、輸出或輸入\/輸出之後的 `SET_PARAM_TYPE` 巨集。  
  
## 語法  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### 參數  
 `type`  
 \[in\] 用來設定參數的類型。  
  
## 備註  
 提供者只支援基礎資料來源支援的參數輸入\/輸出類型。 此類型是一或多個 **DBPARAMIO** 值的組合 \(請參閱＜OLE DB 程式設計人員參考＞中的 [DBBINDING Structures](https://msdn.microsoft.com/en-us/library/ms716845.aspx) \(DBBINDING 結構\)\)：  
  
-   **DBPARAMIO\_NOTPARAM**：存取子沒有參數。 通常會在資料列存取子將 **eParamIO** 設定為此值，以提醒使用者參數被忽略。  
  
-   **DBPARAMIO\_INPUT**：輸入參數。  
  
-   **DBPARAMIO\_OUTPUT**：輸出參數。  
  
-   **DBPARAMIO\_INPUT &#124; DBPARAMIO\_OUTPUT**：參數同時是輸入和輸出參數。  
  
## 範例  
 [!CODE [NVC_OLEDB_Consumer#18](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#18)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)