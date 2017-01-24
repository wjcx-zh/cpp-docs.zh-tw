---
title: "_U_STRINGorID Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL._U_STRINGorID"
  - "ATL::_U_STRINGorID"
  - "_U_STRINGorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_STRINGorID class"
  - "U_STRINGorID class"
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _U_STRINGorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個引數配接器類別允許資源名稱 \(`LPCTSTR`\) 或資源 ID \(**UINT**\) 使用 **MAKEINTRESOURCE** 巨集，會傳遞至函式，而不要求呼叫端轉換 ID 加入至字串。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class _U_STRINGorID  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[\_U\_STRINGorID::\_U\_STRINGorID](../Topic/_U_STRINGorID::_U_STRINGorID.md)|建構函式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[\_U\_STRINGorID::m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md)|資源識別項。|  
  
## 備註  
 這個類別會實作與 Windows 資源管理 API 的包裝函式 \(例如設計 [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042)、 [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)和 [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) 函式，會接受 `LPCTSTR` 引數可能是資源的名稱或其 ID.  
  
 類別會定義兩個建構函式多載:一個接受 `LPCTSTR` 引數，另一 **UINT** 接受引數。  **UINT** 引數轉換為資源類型與 Windows 資源管理功能相容用於類別的唯一資料成員和結果儲存 **MAKEINTRESOURCE** 巨集， [m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md)。  `LPCTSTR` 至建構函式的引數直接儲存，而無法轉換。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)