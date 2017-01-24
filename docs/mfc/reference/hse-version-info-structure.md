---
title: "HSE_VERSION_INFO 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HSE_VERSION_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HSE_VERSION_INFO 結構"
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HSE_VERSION_INFO 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個結構指向在 `CHttpServer::GetExtensionVersion` 成員函式的 `pVer` 參數。  它提供 ISA 版本號碼和 ISA 的文字描述。  
  
## 語法  
  
```  
  
      typedef struct _HSE_VERSION_INFO {  
   DWORD dwExtensionVersion;  
   CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### 參數  
 *dwExtensionVersion*  
 ISA 的版本號碼。  
  
 *lpszExtensionDesc*  
 ISA 的文字描述。  預設實作會提供預留位置文字;覆寫將描述的 `CHttpServer::GetExtensionVersion` 。  
  
## 需求  
 **Header:** httpext.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)