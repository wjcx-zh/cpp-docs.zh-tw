---
title: "在提供者內支援無限制執行緒 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 多執行緒"
  - "執行緒 [C++], 提供者"
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 在提供者內支援無限制執行緒
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有的 OLE DB 提供者類別都為安全執行緒 \(Thread\-Safe\)，而且登錄項目已適當設定。  支援無限制執行緒以協助在多使用者環境中提供高層級的效能，是很好的作法。  若要讓提供者維持安全執行緒，您必須確認已經適當地封鎖程式碼。  每當寫入或儲存資料時，您必須封鎖關鍵區段 \(Critical Section\) 的存取。  
  
 每個 OLE DB 提供者樣板物件都有自己的關鍵區段。  若要使封鎖更容易，您建立的每個新類別都必須為樣板類別，且引數必須是父類別名稱。  
  
 以下範例說明如何封鎖程式碼：  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 如需如何使用 `Lock` 和 `Unlock` 保護關鍵區段的詳細資訊，請參閱[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
 您也必須驗證所覆寫的任何方法 \(例如 `Execute`\) 都為安全執行緒。  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)