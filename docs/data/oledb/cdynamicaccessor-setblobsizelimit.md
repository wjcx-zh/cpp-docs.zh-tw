---
title: "CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs"
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
  - "CDynamicAccessor::SetBlobSizeLimit"
  - "SetBlobSizeLimit"
  - "CDynamicAccessor.SetBlobSizeLimit"
  - "ATL.CDynamicAccessor.SetBlobSizeLimit"
  - "ATL::CDynamicAccessor::SetBlobSizeLimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobSizeLimit 方法"
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetBlobSizeLimit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以位元組設定最大金鑰大小。  
  
## 語法  
  
```  
  
      void SetBlobSizeLimit(  
   DBLENGTH nBlobSize   
);  
```  
  
#### 參數  
 `nBlobSize`  
 指定 BLOB 的大小限制。  
  
## 備註  
 以位元組設定最大 BLOB 大小;資料行大於這個值會被視為 BLOB。  有些提供者提供資料行的非常大的大小 \(例如 2 GB\)。  不要嘗試配置的記憶體大小，這通常會嘗試繫結這些資料行做為 BLOB。  以這種方式並不需要配置任何記憶體，不過，您仍然可以讀取所有資料，而不需要攔截的 \(懼。  不過，您可能會想要強制 `CDynamicAccessor` 繫結在它們的原生資料型別的大行的一些情況。  若要這麼做，請在呼叫 **Open**前呼叫 `SetBlobSizeLimit` 。  
  
 建構函式方法 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 設定的最大 BLOB 大小為預設值 8,000 位元組。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)