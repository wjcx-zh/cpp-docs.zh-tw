---
title: "com::ptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "com::ptr"
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# com::ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以當做 CLR 類別成員的 COM 物件的包裝函式。  在呼叫其解構函式時，包裝函式自動化 COM 物件的存留期管理，釋出物件的擁有的參考。  類似於 [CComPtr Class](../atl/reference/ccomptr-class.md)。  
  
## 語法  
  
```  
#include <msclr\com\ptr.h>  
```  
  
## 備註  
 [com::ptr 類別](../dotnet/com-ptr-class.md) 在 msclr \<\\ com 定義\\ ptr.h 檔案\> 。  
  
## 請參閱  
 [C\+\+ 支援程式庫](../dotnet/cpp-support-library.md)