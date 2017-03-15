---
title: "Allocating and Releasing Memory for a BSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "bstr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, 記憶體配置"
  - "記憶體 [C++], 釋放"
  - "記憶體配置, BSTR"
  - "memory deallocation, BSTR memory"
  - "memory deallocation, string memory"
  - "字串 [C++], 釋放"
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Allocating and Releasing Memory for a BSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立 `BSTR`個並將它們用於避免記憶體流失的它們在 COM 物件時，您必須注意視為在記憶體中。  當 `BSTR` 介面內時，您必須釋放它的記憶體，當您完成使用後。  不過，在中，當 `BSTR` 透過介面之外，接收的物件負責其記憶體管理的責任。  
  
 一般而言，配置及釋放供 `BSTR`配置之記憶體的規則如下:  
  
-   當您呼叫需要指標 `BSTR` 引數的函式時，您必須在呼叫之前 `BSTR` 配置的記憶體後釋放它。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   當您呼叫會傳回 `BSTR`的函式時，您必須釋放字串。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   當您實作會傳回 `BSTR`的函式時，將字串，但不要釋放它。  接收函式釋放記憶體。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)   
 [SysAllocString](http://msdn.microsoft.com/zh-tw/9e0437a2-9b4a-4576-88b0-5cb9d08ca29b)   
 [SysFreeString](http://msdn.microsoft.com/zh-tw/8f230ee3-5f6e-4cb9-a910-9c90b754dcd3)