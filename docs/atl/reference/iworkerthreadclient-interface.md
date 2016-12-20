---
title: "IWorkerThreadClient Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IWorkerThreadClient"
  - "ATL::IWorkerThreadClient"
  - "IWorkerThreadClient"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IWorkerThreadClient interface"
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IWorkerThreadClient Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`IWorkerThreadClient` 是 [CWorkerThread](../../atl/reference/cworkerthread-class.md) 類別的用戶端實作的介面。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
__interface IWorkerThreadClient  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[CloseHandle](../Topic/IWorkerThreadClient::CloseHandle.md)|實作這個方法關閉控制代碼與這個物件相關聯的。|  
|[執行](../Topic/IWorkerThreadClient::Execute.md)|表示控制項中包含與這個物件收到信號時，請實作這個方法會執行程式碼。|  
  
## 備註  
 請實作這個介面，當您在背景工作執行緒需要執行以回應變成的控制代碼都收到信號的程式碼時。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CWorkerThread Class](../../atl/reference/cworkerthread-class.md)