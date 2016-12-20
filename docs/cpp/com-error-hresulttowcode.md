---
title: "_com_error::HRESULTToWCode | Microsoft Docs"
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
  - "HRESULTToWCode"
  - "_com_error.HRESULTToWCode"
  - "_com_error::HRESULTToWCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HRESULTToWCode 方法"
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::HRESULTToWCode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 32 位元的 `HRESULT` 對應至 16 位元的 `wCode`。  
  
## 語法  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### 參數  
 `hr`  
 要對應到 16 位元 `wCode` 的 32 位元 `HRESULT`。  
  
## 傳回值  
 從 32 位元 `HRESULT` 對應過來的 16 位元 `wCode`。  
  
## 備註  
 如需詳細資訊，請參閱 [\_com\_error::WCode](../cpp/com-error-wcode.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error::WCode](../cpp/com-error-wcode.md)   
 [\_com\_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [\_com\_error 類別](../cpp/com-error-class.md)