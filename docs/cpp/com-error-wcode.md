---
title: "_com_error::WCode | Microsoft Docs"
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
  - "_com_error.WCode"
  - "_com_error::WCode"
  - "WCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCode 方法"
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::WCode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擷取對應至封裝的 `HRESULT` 的 16 位元錯誤碼。  
  
## 語法  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## 傳回值  
 如果 `HRESULT` 在 0x80040200 到 0x8004FFFF 的範圍內，**WCode** 方法會傳回 `HRESULT` 減 0x80040200；否則會傳回零。  
  
## 備註  
 **WCode** 方法用於復原 COM 支援程式碼中發生的對應。  **dispinterface** 屬性或方法的包裝函式會呼叫封裝引數並呼叫 **IDispatch::Invoke** 的支援常式。  傳回時，如果傳回 `DISP_E_EXCEPTION` 的失敗 `HRESULT`，會從傳遞至 **IDispatch::Invoke** 的 **EXCEPINFO** 結構擷取錯誤資訊。  錯誤碼可能是 16 位元值 \(儲存在 **EXCEPINFO** 結構的 `wCode` 成員中\) 或是完整的 32 位元值 \(在 **EXCEPINFO** 結構的 **scode** 成員中\)。  如果傳回 16 位元 `wCode`，必須先對應至 32 位元失敗 `HRESULT`。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [\_com\_error 類別](../cpp/com-error-class.md)