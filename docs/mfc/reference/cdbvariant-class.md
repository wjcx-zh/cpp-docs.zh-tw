---
title: "CDBVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDBVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBVariant 類別"
  - "Variant 資料型別, ODBC"
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示 MFC ODBC 類別的不同的資料型別。  
  
## 語法  
  
```  
class CDBVariant  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDBVariant::CDBVariant](../Topic/CDBVariant::CDBVariant.md)|建構 `CDBVariant` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDBVariant::Clear](../Topic/CDBVariant::Clear.md)|清除 `CDBVariant` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDBVariant::m\_dwType](../Topic/CDBVariant::m_dwType.md)|包含目前儲存值的資料型別。  輸入 `DWORD`。|  
  
### 公開等位成員  
  
|名稱|描述|  
|--------|--------|  
|[CDBVariant::m\_boolVal](../Topic/CDBVariant::m_boolVal.md)|包含型別 **BOOL**的值。|  
|[CDBVariant::m\_chVal](../Topic/CDBVariant::m_chVal.md)|包含型別 `unsigned char`的值。|  
|[CDBVariant::m\_dblVal](../Topic/CDBVariant::m_dblVal.md)|包含型別 **double**的值。|  
|[CDBVariant::m\_fltVal](../Topic/CDBVariant::m_fltVal.md)|包含型別 **浮動**的值。|  
|[CDBVariant::m\_iVal](../Topic/CDBVariant::m_iVal.md)|包含型別 **short**的值。|  
|[CDBVariant::m\_lVal](../Topic/CDBVariant::m_lVal.md)|包含型別 **long**的值。|  
|[CDBVariant::m\_pbinary](../Topic/CDBVariant::m_pbinary.md)|含有指向型別 `CLongBinary`物件。|  
|[CDBVariant::m\_pdate](../Topic/CDBVariant::m_pdate.md)|含有指向型別 **TIMESTAMP\_STRUCT**物件。|  
|[CDBVariant::m\_pstring](../Topic/CDBVariant::m_pstring.md)|含有指向型別 `CString`物件。|  
|[CDBVariant::m\_pstringA](../Topic/CDBVariant::m_pstringA.md)|儲存指標為 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) 物件。|  
|[CDBVariant::m\_pstringW](../Topic/CDBVariant::m_pstringW.md)|儲存指標的寬 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 物件。|  
  
## 備註  
 `CDBVariant` 不具有基底類別。  
  
 `CDBVariant` 類似 [COleVariant](../../mfc/reference/colevariant-class.md);不過， `CDBVariant` 不使用 OLE。  `CDBVariant` 允許您儲存值，而不用擔心值的資料型別。  `CDBVariant` 追蹤目前值的資料型別，在等位儲存。  
  
 類別 [CRecordset](../../mfc/reference/crecordset-class.md) 套用在三 \+ 成成員函式的 `CDBVariant` 物件: `GetFieldValue`、 `GetBookmark`和 `SetBookmark`。  例如， `GetFieldValue` 可讓您動態擷取資料行中的資料。  因為這個資料行的資料型別可能不知道在執行階段， `GetFieldValue` 使用 `CDBVariant` 物件儲存在資料行中的資料。  
  
## 繼承階層架構  
 `CDBVariant`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)   
 [CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)   
 [CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)