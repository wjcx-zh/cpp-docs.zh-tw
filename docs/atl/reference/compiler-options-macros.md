---
title: "Compiler Options Macros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "編譯器選項, 巨集"
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compiler Options Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些巨集管理特定的編譯器功能。  
  
|||  
|-|-|  
|[\_ATL\_ALL\_WARNINGS](../Topic/_ATL_ALL_WARNINGS.md)|啟用專案的錯誤的符號 ATL 舊版呈現。|  
|[\_ATL\_APARTMENT\_THREADED](../Topic/_ATL_APARTMENT_THREADED.md)|如果第一個或更多的物件使用 Apartment 執行緒，請定義。|  
|[\_ATL\_CSTRING\_EXPLICIT\_CONSTRUCTORS](../Topic/_ATL_CSTRING_EXPLICIT_CONSTRUCTORS.md)|判斷 `CString` 建構函式明確，防止所有不預期的轉換。|  
|[\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)|定義這個巨集就能使用符合 C\+\+ 標準的語法， C4867 產生編譯器錯誤，而非標準語法是用來初始化成員指標函式時。|  
|[\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md)|如果第一個或更多的物件使用中性或無限制執行緒，請定義。|  
|[\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)|表示專案中的符號將會被標記為和的物件，選擇性或中性。  應該使用巨集 [\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md) 。|  
|[\_ATL\_NO\_AUTOMATIC\_NAMESPACE](../Topic/_ATL_NO_AUTOMATIC_NAMESPACE.md)|防止對命名空間的預設會使用為 ATL 的符號。|  
|[\_ATL\_NO\_COM\_SUPPORT](../Topic/_ATL_NO_COM_SUPPORT.md)|防止 COM 相關程式碼編譯專案的符號。|  
|[ATL\_NO\_VTABLE](../Topic/ATL_NO_VTABLE.md)|在類別的建構函式和解構函式 \(Destructor\) 避免 vtable 指標初始化的符號。|  
|[ATL\_NOINLINE](../Topic/ATL_NOINLINE.md)|表示函式的符號不應該內嵌。|  
|[\_ATL\_SINGLE\_THREADED](../Topic/_ATL_SINGLE_THREADED.md)|如果您所有的物件使用單一執行緒模型，請定義。|  
  
## 請參閱  
 [Macros](../../atl/reference/atl-macros.md)