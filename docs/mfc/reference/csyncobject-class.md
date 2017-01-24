---
title: "CSyncObject Class | Microsoft Docs"
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
  - "CSyncObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSyncObject class"
  - "同步類別, CSyncObject"
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSyncObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供常用的功能同步的純虛擬類別在 Win32 物件。  
  
## 語法  
  
```  
class CSyncObject : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSyncObject::CSyncObject](../Topic/CSyncObject::CSyncObject.md)|建構 `CSyncObject` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSyncObject::Lock](../Topic/CSyncObject::Lock.md)|同步處理物件的存取權。|  
|[CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md)|同步處理物件的存取權。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSyncObject::operator HANDLE](../Topic/CSyncObject::operator%20HANDLE.md)|提供對的同步物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CSyncObject::m\_hObject](../Topic/CSyncObject::m_hObject.md)|為基礎的同步處理物件的控制代碼。|  
  
## 備註  
 MFC 程式庫提供從 `CSyncObject`衍生的數個類別。  這些是 [CEvent](../../mfc/reference/cevent-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)和 [CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 如需如何使用同步處理物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)