---
title: "_com_error::GUID | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GUID"
  - "_com_error.GUID"
  - "_com_error::GUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID 方法"
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::GUID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 呼叫 **IErrorInfo::GetGUID** 函式。  
  
## 語法  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## 傳回值  
 傳回 `_com_error` 物件中所記錄之 **IErrorInfo** 物件的 **IErrorInfo::GetGUID** 結果。  如果未記錄 **IErrorInfo** 物件，會傳回 `GUID_NULL`。  
  
## 備註  
 呼叫 **IErrorInfo::GetGUID** 方法時的任何失敗皆會予以忽略。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)