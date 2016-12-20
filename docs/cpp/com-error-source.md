---
title: "_com_error::Source | Microsoft Docs"
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
  - "_com_error.Source"
  - "_com_error::Source"
  - "source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Source 方法"
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::Source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 呼叫 **IErrorInfo::GetSource** 函式。  
  
## 語法  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## 傳回值  
 傳回 `_com_error` 物件中所記錄之 **IErrorInfo** 物件的 **IErrorInfo::GetSource** 結果。  產生的 BSTR 會封裝在 `_bstr_t` 物件內。  如果未記錄 **IErrorInfo** 物件，則傳回一個空的 `_bstr_t`。  
  
## 備註  
 呼叫 **IErrorInfo::GetSource** 方法時的任何失敗皆會加以忽略。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)