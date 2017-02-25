---
title: "決定使用哪一種存取子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取子 [C++], 類型"
  - "資料列集 [C++], 資料類型"
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 決定使用哪一種存取子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以在編譯時間或執行階段決定資料列集的資料型別。  
  
 如果您需要在編譯時間決定資料型別，請使用靜態存取子 \(例如 `CAccessor`\)。  您可以手動地決定或使用 ATL OLE DB 消費者精靈以決定資料型別。  
  
 如果您需要在 Run Time 決定資料型別，您可能就要使用動態 \(`CDynamicAccessor` 或它的子代\) 或手動存取子 \(`CManualAccessor`\)。  在這些情況中，您可以在資料列集上呼叫 `GetColumnInfo`，傳回資料行繫結資訊，以便讓您決定型別。  
  
 下表列出了消費者樣板提供的存取子型別。  每個存取子都有其優缺點。  視您的情況而定，應該會有一種存取子符合您的需求。  
  
|存取子類別|繫結|參數|Comment|  
|-----------|--------|--------|-------------|  
|`CAccessor`|使用 `COLUMN_ENTRY` 巨集建立使用者資料錄。  巨集會將該資料錄的資料成員繫結至存取子。  當建立資料列集以後，便不能解除繫結資料行。|是，使用 **PARAM\_MAP** 巨集項目。  參數一旦完成繫結便不能解除。|因為擁有少量程式碼，所以是最快速的存取子。|  
|`CDynamicAccessor`|自動。|否。|在您不知道資料列集的資料型別時很有用。|  
|`CDynamicParameterAccessor`|自動，但是可以被[覆寫](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，如果提供者支援 `ICommandWithParameters`。  參數會自動繫結。|稍慢於 `CDynamicAccessor`，但是在呼叫泛用的預存程序時很有用。|  
|**CDynamicStringAccessor\[A,W\]**|自動。|否。|以字串資料方式擷取從資料存放區存取的資料。|  
|`CManualAccessor`|手動使用 `AddBindEntry`。|手動使用 `AddParameterEntry`。|非常快速；只繫結一次參數和資料行。  您可以決定要使用的資料型別\(如需範例說明，請參閱 [DBVIEWER](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832) 範例\)。比 `CDynamicAccessor` 或 `CAccessor` 需要更多的程式碼。  它比較像是直接呼叫 OLE DB。|  
|`CXMLAccessor`|自動。|否。|以字串資料方式擷取從資料存放區存取的資料，並將它格式化為 XML 標記資料。|  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)