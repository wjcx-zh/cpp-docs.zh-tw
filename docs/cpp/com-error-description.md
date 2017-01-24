---
title: "_com_error::Description | Microsoft Docs"
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
  - "_com_error.Description"
  - "_com_error::Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Description 方法"
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::Description
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 呼叫 **IErrorInfo::GetDescription** 函式。  
  
## 語法  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## 傳回值  
 傳回 `_com_error` 物件中所記錄之 **IErrorInfo** 物件的 **IErrorInfo::GetDescription** 結果。  產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。  如果未記錄 **IErrorInfo** 物件，則傳回一個空的 `_bstr_t`。  
  
## 備註  
 呼叫 **IErrorInfo::GetDescription** 函式，並擷取 `_com_error` 物件中記錄的 **IErrorInfo** 物件。  呼叫 **IErrorInfo::GetDescription** 方法時的任何失敗都會加以忽略。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)