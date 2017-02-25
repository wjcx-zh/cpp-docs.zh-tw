---
title: "_com_ptr_t::GetActiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t.GetActiveObject"
  - "_com_ptr_t::GetActiveObject"
  - "GetActiveObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActiveObject 方法"
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _com_ptr_t::GetActiveObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 附加至已指定 **CLSID** 或 **ProgID** 之物件現有的執行個體。  
  
## 語法  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### 參數  
 `rclsid`  
 物件的 **CLSID**。  
  
 `clsidString`  
 保留 **CLSID** \(以 "**{**" 為開頭\) 或 **ProgID** 的 Unicode 字串。  
  
 `clsidStringA`  
 保留 **CLSID** \(以 "**{**" 為開頭\) 或 **ProgID** 的多位元組字串 \(使用 ANSI 字碼頁\)。  
  
## 備註  
 這些成員函式會呼叫 `GetActiveObject` 擷取指向已向 OLE 註冊之執行中物件的指標，然後查詢這個智慧型指標的介面類型。  然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。  此時會呼叫 **Release** 讓先前封裝之指標的參考計數遞減。  這個常式會傳回 `HRESULT`，表示成功或失敗。  
  
-   **GetActiveObject\(**  `rclsid`  **\)**：附加至已指定 **CLSID** 之物件現有的執行個體。  
  
-   **GetActiveObject\(**  `clsidString`  **\)**：附加至已指定保存 **CLSID** \(開頭為 "**{**"\) 或 **ProgID** 之 Unicode 字串的物件現有的執行個體。  
  
-   **GetActiveObject\(**  `clsidStringA`  **\)**：附加至已指定保存 **CLSID** \(開頭為 "**{**"\) 或 **ProgID** 之多位元組字元字串的物件現有的執行個體。  呼叫 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)