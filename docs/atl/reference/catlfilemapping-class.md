---
title: "CAtlFileMapping Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlFileMapping<T>"
  - "ATL.CAtlFileMapping"
  - "ATL::CAtlFileMapping"
  - "CAtlFileMapping"
  - "ATL.CAtlFileMapping<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFileMapping class"
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAtlFileMapping Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示記憶體對應檔案，將轉型運算子套用至 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
typename T= char  
>  
class CAtlFileMapping :  
public CAtlFileMappingBase  
```  
  
#### 參數  
 `T`  
 使用轉型運算子的資料型別。  
  
## Members  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAtlFileMapping::operator T\*](../Topic/CAtlFileMapping::operator%20T*.md)|允許 `CAtlFileMapping` 物件隱含轉換為 `T`**\***的。|  
  
## 備註  
 這個類別會將單一轉型運算子可讓 `CAtlFileMapping` 物件隱含轉換為 `T`**\***的。  基底類別 \(Base Class\) 提供其他成員， [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
## 繼承階層架構  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## 需求  
 **Header:** atlfile.h  
  
## 請參閱  
 [CAtlFileMappingBase Class](../../atl/reference/catlfilemappingbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)