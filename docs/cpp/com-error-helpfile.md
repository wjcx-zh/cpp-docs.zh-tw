---
title: "_com_error::HelpFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "HelpFile"
  - "_com_error::HelpFile"
  - "_com_error.HelpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpFile 方法"
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::HelpFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 呼叫 **IErrorInfo::GetHelpFile** 函式。  
  
## 語法  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## 傳回值  
 傳回 `_com_error` 物件中所記錄之 **IErrorInfo** 物件的 **IErrorInfo::GetHelpFile** 結果。  產生的 BSTR 會封裝在 `_bstr_t` 物件內。  如果未記錄 **IErrorInfo** 物件，則傳回一個空的 `_bstr_t`。  
  
## 備註  
 忽略呼叫 **IErrorInfo::GetHelpFile** 方法時發生的任何失敗。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)