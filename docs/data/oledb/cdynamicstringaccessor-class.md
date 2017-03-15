---
title: "CDynamicStringAccessor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessor 類別"
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDynamicStringAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓您能在不知道資料庫結構描述 \(資料庫的基礎結構\) 的情況下，存取資料來源。  
  
## 語法  
  
```  
  
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|擷取指定資料行的資料做為字串。|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|設定指定資料行的資料做為字串。|  
  
## 備註  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 要求資料必須是提供者報告時的原型格式，而 `CDynamicStringAccessor` 則要求提供者以字串資料方式擷取從資料存放區存取的所有資料。  這個對於不需要計算資料存放區值的簡單工作 \(例如，顯示或列印資料存放區的內容\) 來說相當有用。  
  
 資料行資料的原生型別在資料存放區不重要;只要提供者可以支援資料轉換，它會提供資料格式的資料。  如果提供者不支援從原生資料型別轉換為字串\(不常見\) ，要求的呼叫將傳回成功值 **DB\_S\_ERRORSOCCURED**，和對應的資料列的狀態會指出一個轉譯問題與 **DBSTATUS\_E\_CANTCONVERTVALUE**。  
  
 使用 `CDynamicStringAccessor` 方法取得資料行資訊。  您可以在執行階段使用這些資料行資訊，動態地建立存取子。  
  
 資料行資訊是儲存在這個類別所建立和管理的暫存區中。  使用 [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) 從緩衝區取得這份資料，或使用 [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md) 將它儲存在緩衝區中。  
  
 如需使用動態存取子類別的詳細資訊和範例，請參閱 [使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。  
  
## 需求  
 **標頭**：atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)