---
title: "_com_error::WCodeToHRESULT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error::WCodeToHRESULT"
  - "_com_error.WCodeToHRESULT"
  - "WCodeToHRESULT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCodeToHRESULT 方法"
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::WCodeToHRESULT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 16 位元的 `wCode` 對應至 32 位元的 `HRESULT`。  
  
## 語法  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### 參數  
 `wCode`  
 要對應到 32 位元 `HRESULT` 的 16 位元 `wCode`。  
  
## 傳回值  
 從 16 位元 `wCode` 對應過來的 32 位元 `HRESULT`。  
  
## 備註  
 請參閱 [WCode](../cpp/com-error-wcode.md) 成員函式。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error::WCode](../cpp/com-error-wcode.md)   
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error 類別](../cpp/com-error-class.md)