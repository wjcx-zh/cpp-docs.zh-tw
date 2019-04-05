---
title: 在提供者內支援無限制執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: a2afb7354dd0447375ee6205b7c5d9a4755aa4b8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025334"
---
# <a name="supporting-free-threading-in-your-provider"></a>在提供者內支援無限制執行緒

所有 OLE DB 提供者類別是安全執行緒，並會據以設定登錄項目。 它是效能的個不錯的主意，以支援無限制執行緒，以協助提供高層級，在多使用者的情況下。 為了協助保持您的提供者具備執行緒安全，您必須確認會正確封鎖您的程式碼。 每當您撰寫或儲存資料時，您必須封鎖存取關鍵區段。

每個 OLE DB 提供者範本物件有它自己的重要區段。 若要使封鎖更容易，每個您所建立的新類別應該採取的父類別的樣板類別名稱做為引數。

下列範例示範如何封鎖您的程式碼：

```cpp
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

如需有關如何保護與關鍵區段`Lock`並`Unlock`，請參閱[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

確認任何方法您覆寫 (例如`Execute`) 是安全執行緒。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)