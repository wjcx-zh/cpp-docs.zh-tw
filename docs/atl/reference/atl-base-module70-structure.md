---
title: "_ATL_BASE_MODULE70 Structure | Microsoft Docs"
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
  - "ATL::_ATL_BASE_MODULE70"
  - "ATL._ATL_BASE_MODULE70"
  - "_ATL_BASE_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_BASE_MODULE70 structure"
  - "ATL_BASE_MODULE70 structure"
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_BASE_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用由使用 ATL 的任何專案。  
  
## 語法  
  
```  
  
      struct _ATL_BASE_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInst;  
   HINSTANCE m_hInstResource;  
   bool m_bNT5orWin98;  
   DWORD dwAtlBuildVer;  
   GUID* pguidVer;  
   CRITICAL_SECTION m_csResource;  
   CSimpleArray<HINSTANCE> m_rgResourceInstance;  
};  
```  
  
## Members  
 `cbSize`  
 結構的大小，使用提供版本。  
  
 `m_hInst`  
 這個模組的 **hInstance** \(exe 或 dll\)。  
  
 `m_hInstResource`  
 預設執行個體資源控制代碼。  
  
 **m\_bNT5orWin98**  
 作業系統版本資訊。  在內部使用 ATL。  
  
 **dwAtlBuildVer**  
 儲存的 ATL 版本。  目前 0x0700。  
  
 **pguidVer**  
 ATL 的內部 GUID。  
  
 **m\_csResource**  
 用來同步處理對 **m\_rgResourceInstance** 陣列的存取。  在內部使用 ATL。  
  
 **m\_rgResourceInstance**  
 用於的陣列搜尋在 ATL 知道的任何資源執行個體的資源。  在內部使用 ATL。  
  
## 備註  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md) 定義為 `_ATL_BASE_MODULE70`typedef。  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)