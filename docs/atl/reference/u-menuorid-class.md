---
title: "_U_MENUorID Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL._U_MENUorID"
  - "ATL::_U_MENUorID"
  - "_U_MENUorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_MENUorID class"
  - "U_MENUorID class"
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# _U_MENUorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 **CreateWindow** 和 **CreateWindowEx**提供包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class _U_MENUorID  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[\_U\_MENUorID::\_U\_MENUorID](../Topic/_U_MENUorID::_U_MENUorID.md)|建構函式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[\_U\_MENUorID::m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md)|為功能表的控制代碼。|  
  
## 備註  
 這個引數配接器類別允許 ID \(**UINT**\) 或功能表控制代碼 \(`HMENU`\) 會傳遞至函式，而不需要明確轉換 \(Cast\) 在呼叫端部分。  
  
 這個類別會實作特定 Windows API， [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) 和 [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) 函式的包裝函式設計，這兩者會接受 `HMENU` 引數可能是子視窗識別項 \(**UINT**\) 而不是功能表控制代碼。  例如，您可以看到這個類別會在使用中當做參數傳遞至 [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)。  
  
 類別會定義兩個建構函式多載:一個接受 **UINT** 引數，另一 `HMENU` 接受引數。  **UINT** 引數轉換成在類別的唯一資料成員和結果的 `HMENU` 儲存的建構函式， [m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md)。  `HMENU` 至建構函式的引數直接儲存，而無法轉換。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)