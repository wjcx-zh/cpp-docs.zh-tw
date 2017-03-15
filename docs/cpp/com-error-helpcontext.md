---
title: "_com_error::HelpContext | Microsoft Docs"
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
  - "_com_error::HelpContext"
  - "HelpContext"
  - "_com_error.HelpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpContext 方法"
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::HelpContext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 呼叫 **IErrorInfo::GetHelpContext** 函式。  
  
## 語法  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## 傳回值  
 傳回 `_com_error` 物件中所記錄之 **IErrorInfo** 物件的 **IErrorInfo::GetHelpContext** 結果。  如果未記錄 **IErrorInfo** 物件，則傳回零。  
  
## 備註  
 呼叫 **IErrorInfo::GetHelpContext** 方法時的任何失敗皆會加以忽略。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)