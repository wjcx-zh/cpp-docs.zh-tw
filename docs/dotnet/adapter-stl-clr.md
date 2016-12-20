---
title: "adapter (STL/CLR) | Microsoft Docs"
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
  - "<cliext/adapter>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<adapter> 標頭 [STL/CLR]"
  - "<cliext/adapter> 標頭 [STL/CLR]"
  - "配接器 [STL/CLR]"
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 標頭 `<cliext/adapter>` 指定兩個樣板類別 \(`collection_adapter` 和 `range_adapter`\) 和樣板函式 `make_collection`。  
  
## 語法  
  
```  
#include <cliext/adapter>  
```  
  
## 備註  
  
|類別|說明|  
|--------|--------|  
|[collection\_adapter](../dotnet/collection-adapter-stl-clr.md)|包裝基底類別程式庫 \(BCL\) 為範圍。|  
|[range\_adapter](../dotnet/range-adapter-stl-clr.md)|封裝範圍為 BCL 集合。|  
  
|功能|說明|  
|--------|--------|  
|[make\_collection](../dotnet/make-collection-stl-clr.md)|使用一個 Iterator，所建立範圍配接器。|  
  
## 需求  
 **標頭：** \<cliext\/adapter\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)