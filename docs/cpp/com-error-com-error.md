---
title: "_com_error::_com_error | Microsoft Docs"
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
  - "_com_error._com_error"
  - "_com_error::_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error 方法"
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::_com_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 建構 `_com_error` 物件。  
  
## 語法  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### 參數  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 **IErrorInfo** 物件。  
  
 **bool fAddRef\=false**  
 導致建構函式在某個非 Null 的 **IErrorInfo** 介面上呼叫 AddRef。  如此可在將介面的擁有權傳入 `_com_error` 物件的一般情況下，提供正確的參考計數，例如：  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 如果您不想讓程式碼將擁有權傳送至 `_com_error` 物件，而在 `_com_error` 解構函式中需要使用 `AddRef` 來位移 **Release**，請依下列方式建構物件：  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 現有的 `_com_error` 物件。  
  
## 備註  
 第一個建構函式會建立新的物件，其中會指定 `HRESULT` 和並選擇性指定 **IErrorInfo** 物件。  第二個方法會建立現有 `_com_error` 物件的複本。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)