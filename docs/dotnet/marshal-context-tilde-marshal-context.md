---
title: "marshal_context::~marshal_context | Microsoft Docs"
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
  - "marshal_context::~marshal_context"
  - "msclr.interop.marshal_context.~marshal_context"
  - "marshal_context.~marshal_context"
  - "msclr::interop::marshal_context::~marshal_context"
  - "~marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 類別 [C++], 作業"
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context::~marshal_context
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

終結 `marshal_context` 物件。  
  
## 語法  
  
```  
~marshal_context();  
```  
  
## 備註  
 有些資料轉換需要封送處理內容。  如需何種轉譯需要內容，以及您的應用程式必須包含哪些封送處理檔案的詳細資訊，請參閱 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
 刪除 `marshal_context` 物件將會使該內容要轉換的資料失效。  如果您想要在終結 `marshal_context` 物件之後儲存資料，您必須手動複製資料至會保留的變數。  
  
## 需求  
 **標頭檔:** \<msclr\\marshal.h\>、\<msclr\\ marshal\_windows.h\>、\<msclr\\ marshal\_cppstd.h\> 或 \<msclr\\ marshal\_atl.h\>  
  
 **命名空間:** msclr::interop  
  
## 請參閱  
 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context 類別](../dotnet/marshal-context-class.md)