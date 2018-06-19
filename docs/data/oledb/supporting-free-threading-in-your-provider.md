---
title: 支援在您的提供者中的無限制執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9c61aea0fec1f6d808a0a34ee74bd0ce2d399a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108510"
---
# <a name="supporting-free-threading-in-your-provider"></a>在提供者內支援無限制執行緒
所有 OLE DB 提供者類別是安全執行緒，並據以設定登錄項目。 它是效能的個不錯的主意支援無限制執行緒可協助您提供高層級，在多使用者情況下。 為了協助保持您的提供者具備執行緒安全，您必須確認您的程式碼會正確地封鎖。 每當您撰寫或儲存資料時，您必須封鎖與關鍵區段的存取權。  
  
 每個 OLE DB 提供者範本物件有它自己的重要區段。 若要進行封鎖更容易，每個您建立新的類別應該是父類別的樣板類別名稱做為引數。  
  
 下列範例會示範如何封鎖您的程式碼：  
  
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
  
 如需有關如何保護關鍵區段與`Lock`和`Unlock`，請參閱[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
 您也必須檢查任何方法您覆寫 (例如`Execute`) 是安全執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)