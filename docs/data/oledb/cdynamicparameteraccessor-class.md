---
title: "CDynamicParameterAccessor 類別 | Microsoft Docs"
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
  - "ATL.CDynamicParameterAccessor"
  - "ATL::CDynamicParameterAccessor"
  - "CDynamicParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicParameterAccessor 類別"
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類似於 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，但藉由呼叫 [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) 介面取得要設定的參數資訊。  
  
## 語法  
  
```  
class CDynamicParameterAccessor : public CDynamicAccessor  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|建構函式。|  
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|從緩衝區擷取參數資料。|  
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|擷取存取子中的參數數目。|  
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|判斷指定的參數為輸入或輸出參數。|  
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|擷取儲存在緩衝區中的指定參數的長度。|  
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|擷取指定的參數名稱。|  
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|擷取儲存在緩衝區中的指定參數的狀態。|  
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|擷取儲存在緩衝區中的指定參數的字串資料。|  
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|擷取指定參數的資料類型。|  
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|設定使用參數資料的緩衝區。|  
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|設定儲存在緩衝區中的指定參數的長度。|  
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|設定儲存在緩衝區中的指定參數的狀態。|  
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|設定儲存在緩衝區中的指定參數的字串資料。|  
  
## 備註  
 提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。  
  
 參數資訊會儲存在這個類別建立和管理的緩衝區中。 使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md) 從緩衝區取得參數資料。  
  
 如需如何使用這個類別執行 SQL Server 預存程序並取得輸出參數值的範例示範，請參閱知識庫文章 Q058860＜如何：使用 CDynamicParameterAccessor 執行預存程序＞。 知識庫文件可在 MSDN Library 的 Visual Studio 文件或在 [http:\/\/support.microsoft.com\/](http://support.microsoft.com) 中取得。  
  
## 需求  
 **標頭檔**：atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)