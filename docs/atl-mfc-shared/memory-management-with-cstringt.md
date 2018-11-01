---
title: 使用 CStringT 管理記憶體
ms.date: 11/04/2016
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: f45aac11f0c42aecf8c72cf6f7d1630d50b780f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598013"
---
# <a name="memory-management-with-cstringt"></a>使用 CStringT 管理記憶體

類別[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是範本類別，用來操作變數長度字元字串。 要保留這些字串的記憶體配置和釋放與每個執行個體相關聯的字串管理員物件透過`CStringT`。 MFC 和 ATL 提供的預設值具現化`CStringT`，稱為`CString`， `CStringA`，和`CStringW`，其操作的不同字元類型的字串。 這些字元類型屬於類型 TCHAR 之外**char**，和`wchar_t`分別。 這些預設字串型別會使用字串管理員，會從程序中的堆積 （ATL) 或 （MFC) 中的 CRT 堆積配置記憶體。 對於一般應用程式，此記憶體配置方案已足夠。 不過，進行大量的程式碼使用的字串 （或多執行緒程式碼） 的預設記憶體管理員可能不會以最佳方式執行。 本主題描述如何覆寫的預設記憶體管理行為`CStringT`，特別建立配置器適用於手邊的工作。

- [自訂字串管理員實作 (基本方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [避免堆積競爭](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [自訂字串管理員實作 (進階方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT︰ 的自訂字串管理員範例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>另請參閱

[CustomString 範例](../visual-cpp-samples.md)

