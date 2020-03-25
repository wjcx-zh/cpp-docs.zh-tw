---
title: 在提供者內支援無限制執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 50e05b70a782dd343031443540790697e980c994
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209534"
---
# <a name="supporting-free-threading-in-your-provider"></a>在提供者內支援無限制執行緒

所有 OLE DB 提供者類別都是安全線程，並據此設定登錄專案。 最好是支援免費的執行緒，協助在多使用者情況下提供高階效能。 若要協助讓提供者具備執行緒安全，您必須確認您的程式碼已正確地遭到封鎖。 每當您撰寫或儲存資料時，都必須封鎖重要區段的存取。

每個 OLE DB 提供者範本物件都有自己的重要區段。 為了讓封鎖變得更容易，您所建立的每個新類別都應該是一個範本類別，接受父類別名稱做為引數。

下列範例顯示如何封鎖您的程式碼：

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

如需如何使用 `Lock` 和 `Unlock`保護重要區段的詳細資訊，請參閱[多執行緒：如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

確認您覆寫的任何方法（例如 `Execute`）都是安全線程。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
