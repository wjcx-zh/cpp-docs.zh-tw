---
title: "Win32ThreadTraits Class | Microsoft Docs"
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
  - "Win32ThreadTraits"
  - "ATL::Win32ThreadTraits"
  - "ATL.Win32ThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "執行緒 [ATL], creation functions"
  - "執行緒 [ATL], Windows threads"
  - "Win32ThreadTraits class"
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Win32ThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供 Windows 執行緒提供建立函式。  如果執行緒不會使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class Win32ThreadTraits  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Win32ThreadTraits::CreateThread](../Topic/Win32ThreadTraits::CreateThread.md)|\(靜態\) 會呼叫這個函式會建立不應該使用 CRT 函式的執行緒。|  
  
## 備註  
 執行緒特性是執行緒的特定型別提供建立函式的類別。  建立函式的方式與 Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式的簽章和語意。  
  
 下列類別會使用執行緒特性:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒使用 CRT 函式，請使用 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)