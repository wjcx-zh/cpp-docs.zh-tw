---
title: "CRTThreadTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CRTThreadTraits"
  - "ATL.CRTThreadTraits"
  - "CRTThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRTThreadTraits class"
  - "執行緒 [ATL], creation functions"
  - "執行緒 [ATL], CRT threads"
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CRTThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供執行緒 CRT 提供建立函式。  如果執行緒是使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CRTThreadTraits  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRTThreadTraits::CreateThread](../Topic/CRTThreadTraits::CreateThread.md)|\(靜態\) 呼叫這個函式建立可以使用 CRT 函式的執行緒。|  
  
## 備註  
 執行緒特性是執行緒的特定型別提供建立函式的類別。  建立函式的方式與 Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式的簽章和語意。  
  
 下列類別會使用執行緒特性:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒不會使用 CRT 函式，請使用 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) 。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)