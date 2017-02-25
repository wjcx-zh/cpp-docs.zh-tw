---
title: "_com_error::ErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error::ErrorMessage"
  - "_com_error.ErrorMessage"
  - "ErrorMessage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorMessage 方法"
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::ErrorMessage
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擷取儲存在 `_com_error` 物件中之 `HRESULT` 的字串訊息。  
  
## 語法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## 傳回值  
 傳回記錄在 `_com_error` 物件中之 `HRESULT` 的字串訊息。  如果 `HRESULT` 是對應的 16 位元 [wCode](../cpp/com-error-wcode.md)，則會傳回一般訊息「`IDispatch error #<wCode>`」。  如果找不到訊息，則會傳回一般訊息「`Unknown error #<hresult>`」。  傳回的字串會是 Unicode 字串或多位元組字串，視 **\_UNICODE** 巨集的狀態而定。  
  
## 備註  
 擷取記錄在 `_com_error` 物件中之 `HRESULT` 的適當系統訊息文字。  該系統訊息文字是透過呼叫 Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) 函式取得。  傳回的字串會由 `FormatMessage` API 配置，並且在終結 `_com_error` 物件時釋放。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)