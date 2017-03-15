---
title: "_com_error::ErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error::ErrorInfo"
  - "ErrorInfo"
  - "_com_error.ErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorInfo 方法"
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::ErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擷取傳遞至建構函式的 **IErrorInfo** 物件。  
  
## 語法  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## 傳回值  
 傳入建構函式的原始 **IErrorInfo** 項目。  
  
## 備註  
 如果未記錄 **IErrorInfo** 項目，則擷取 `_com_error` 物件中的已封裝 **IErrorInfo** 項目，否則為 **NULL**。  呼叫端必須在使用完成時呼叫所傳回之物件的 **Release**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)