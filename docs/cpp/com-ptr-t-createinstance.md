---
title: "_com_ptr_t::CreateInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::CreateInstance"
  - "_com_ptr_t.CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance 方法"
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_ptr_t::CreateInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 建立已指定 **CLSID** 或 **ProgID** 之物件的新執行個體。  
  
## 語法  
  
```  
  
      HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### 參數  
 `rclsid`  
 物件的 **CLSID**。  
  
 `clsidString`  
 保留 **CLSID** \(以 "**{**" 為開頭\) 或 **ProgID** 的 Unicode 字串。  
  
 `clsidStringA`  
 保留 **CLSID** \(以 "**{**" 為開頭\) 或 **ProgID** 的多位元組字串 \(使用 ANSI 字碼頁\)。  
  
 `dwClsContext`  
 執行中的可執行程式碼內容。  
  
 `pOuter`  
 [彙總](../atl/aggregation.md)的外部未知。  
  
## 備註  
 這些成員函式會呼叫 `CoCreateInstance` 建立新的 COM 物件，然後查詢這個智慧型指標的介面類型。  然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。  此時會呼叫 **Release** 讓先前封裝之指標的參考計數遞減。  這個常式會傳回 `HRESULT`，表示成功或失敗。  
  
-   **CreateInstance\(**  `rclsid` **,**  `dwClsContext`  **\)**：建立已指定 **CLSID** 之物件的執行中新執行個體。  
  
-   **CreateInstance\(**  `clsidString` **,**  `dwClsContext`  **\)**：建立已指定保存 **CLSID** \(開頭為 "**{**"\) 或 **ProgID** 的 Unicode 字串之物件的執行中新執行個體。  
  
-   **CreateInstance\(**  `clsidStringA` **,**  `dwClsContext`  **\)**：建立已指定保存 **CLSID** \(開頭為 "**{**"\) 或 **ProgID** 的多位元組字串之物件的執行中新執行個體。  呼叫 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)