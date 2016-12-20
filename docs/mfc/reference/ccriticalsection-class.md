---
title: "CCriticalSection Class | Microsoft Docs"
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
  - "CCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCriticalSection class"
  - "critical sections"
  - "同步類別, CCriticalSection class"
  - "synchronization objects, critical section"
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示「關鍵區段」—一次只允許一個執行緒存取資源或程式碼區段的同步處理的物件。  
  
## 語法  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCriticalSection::CCriticalSection](../Topic/CCriticalSection::CCriticalSection.md)|建構 `CCriticalSection` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCriticalSection::Lock](../Topic/CCriticalSection::Lock.md)|使用將 `CCriticalSection` 物件的存取權。|  
|[CCriticalSection::Unlock](../Topic/CCriticalSection::Unlock.md)|釋放 `CCriticalSection` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CCriticalSection::operator CRITICAL\_SECTION\*](../Topic/CCriticalSection::operator%20CRITICAL_SECTION*.md)|擷取指標內部 **CRITICAL\_SECTION** 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCriticalSection::m\_sect](../Topic/CCriticalSection::m_sect.md)|**CRITICAL\_SECTION** 物件。|  
  
## 備註  
 在中，只有一個執行緒可以同時允許修改資料或某些其他控制資源時，關鍵區段就很有用。  例如，將節點加入至連結的清單是應該由一個執行緒一次只允許的處理序。  您可以使用控制項連結串列的 `CCriticalSection` 物件，只有一個執行緒可以對清單中每個的存取權。  
  
> [!NOTE]
>  實際的 Win32 **CRITICAL\_SECTION** 物件提供 `CCriticalSection` 類別的功能。  
  
 關鍵區段 \(而非使用 Mutex \(請參閱 [CMutex](../../mfc/reference/cmutex-class.md)\)，當速度非常重要的資源，而不會跨越處理序界限內。  
  
 有兩個方法會使用 `CCriticalSection` 物件:獨立應用程式和內嵌於類別。  
  
-   會在需要時，使用獨立 `CCriticalSection` 物件的個別方法， `CCriticalSection` 建構物件。  在從建構函式的成功傳回時，明確鎖定具有呼叫的物件。 [鎖定](../Topic/CCriticalSection::Lock.md)之後。  但是，在進行存取這個關鍵區段時，請呼叫 [解除鎖定](../Topic/CCriticalSection::Unlock.md) 。  這個方法，不過，讀取原始程式碼的人的更清楚，比較容易發生錯誤的存取，之前或之後，您必須記住鎖定和解除鎖定關鍵區段。  
  
     較好的方法是使用 [CSingleLock](../../mfc/reference/csinglelock-class.md) 類別。  它也有 `Lock` 和 `Unlock` 方法，不過，您不需要擔心解除鎖定資源，如果發生例外狀況。  
  
-   內嵌的方法可以具有多個執行緒共用類別將 `CCriticalSection`型別的資料成員加入到類別和鎖定資料成員時，需要。  
  
 如需使用 `CCriticalSection` 物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMutex Class](../../mfc/reference/cmutex-class.md)