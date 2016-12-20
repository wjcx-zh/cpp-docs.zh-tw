---
title: "Memory Management with CStringT | Microsoft Docs"
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
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, description of"
  - "CString objects, 記憶體管理"
  - "CStringT class, 記憶體管理"
  - "IAtlStringMgr class, 使用"
  - "記憶體 [C++], 用法"
  - "字串 [C++], custom memory management"
  - "字串 [C++], 記憶體管理"
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Memory Management with CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別是用來 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 的樣板類別作業可變長度字元字串。  保留這類字串的記憶體傳遞字串處理常式物件配置和釋放，與 `CStringT`每個執行個體。  MFC 和 ATL 提供 `CStringT`的預設執行個體化之後，呼叫 `CString`、 `CStringA`和 `CStringW`，作業不同的配置類型字串。  這些字元型別分別是型別 **TCHAR**、 `char`和 `wchar_t`。  這些預設字串型別使用處理堆積的字串處理常式 \(在 ATL\) 或 CRT 堆積配置記憶體 \(在 MFC\)。  對於一般的應用程式，因此這個記憶體配置足夠。  不過，在中，針對程式碼執行耗用大量使用的字串 \(或多個執行緒的程式碼\) 的預設記憶體管理員可能無法最佳方式執行。  本主題將說明如何覆寫預設 `CStringT`記憶體管理行為，建立為工作特別最佳化的配置器手上。  
  
-   [自訂字串處理常式 \(基底方法的實作\)。](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [避免堆積爭用](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [自訂字串處理常式 \(進階方法\) 的實作。](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT:自訂字串處理常式的範例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## 請參閱  
 [CustomString 範例](../top/visual-cpp-samples.md)