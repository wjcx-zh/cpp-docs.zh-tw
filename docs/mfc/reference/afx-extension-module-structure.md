---
title: "AFX_EXTENSION_MODULE 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AFX_EXTENSION_MODULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXTENSION_MODULE 結構"
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# AFX_EXTENSION_MODULE 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`AFX_EXTENSION_MODULE` 在 MFC 擴充 DLL 時所用的初始化保存擴充 DLL 模組狀態。  
  
## 語法  
  
```  
  
      struct AFX_EXTENSION_MODULE  
{  
   BOOL bInitialized;  
   HMODULE hModule;  
   HMODULE hResource;  
   CRuntimeClass* pFirstSharedClass;  
   COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### 參數  
 *bInitialized*  
 **TRUE** ，如果 DLL 模組已初始化的 `AfxInitExtensionModule`。  
  
 `hModule`  
 指定 DLL 模組的控制代碼。  
  
 *hResource*  
 指定 DLL 自訂資源模組的控制代碼。  
  
 *pFirstSharedClass*  
 對資訊 \( `CRuntimeClass` 結構\) 的指標有關 DLL 模組的第一個執行階段類別。  用來提供執行階段類別清單的開頭。  
  
 *pFirstSharedFactory*  
 對 DLL 模組的指標首先物件 Factory \( `COleObjectFactory` 物件\)。  用來提供 Class Factory 清單的開頭。  
  
## 備註  
 MFC 擴充 DLL 必須在其 `DllMain` 的兩個項目\):  
  
-   呼叫 [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md) 並檢查傳回值。  
  
-   建立 **CDynLinkLibrary** 物件 DLL 匯出 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件或擁有自己的自訂資源。  
  
 `AFX_EXTENSION_MODULE` 結構是用來保存擴充 DLL 模組狀態的複本，包括由擴充 DLL 初始化為執行一般靜態物件建構的一部分執行階段類別物件的複本，在 `DllMain` 中項目之前。  例如：  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_1.cpp)]  
  
 在 `AFX_EXTENSION_MODULE` 結構中儲存的模組資訊可以複製到 **CDynLinkLibrary** 物件。  例如：  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_2.cpp)]  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md)   
 [AfxTermExtensionModule](../Topic/AfxTermExtensionModule.md)