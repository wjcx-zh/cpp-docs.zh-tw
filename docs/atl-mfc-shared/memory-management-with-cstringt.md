---
title: 使用 CStringT 進行記憶體管理
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: bf1f99b92761c84d59b6f7bfb9aef67d7e097893
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222026"
---
# <a name="memory-management-with-cstringt"></a>使用 CStringT 進行記憶體管理

類別[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是用來操作可變長度字元字串的範本類別。 保存這些字串的記憶體是透過與每個實例相關聯的字串管理員物件來配置和釋放 `CStringT` 。 MFC 和 ATL 提供的預設具現化 `CStringT` （稱為 `CString` 、 `CStringA` 和 `CStringW` ），其會操控不同字元類型的字串。 這些字元類型分別為 TCHAR、 **`char`** 和類型 **`wchar_t`** 。 這些預設字串類型使用的字串管理員會從進程堆積（在 ATL 中）或 CRT 堆積（在 MFC 中）配置記憶體。 對於一般應用程式而言，這個記憶體配置配置就已足夠。 不過，針對使用大量字串（或多執行緒程式碼）的程式碼，預設記憶體管理員可能無法以最佳方式執行。 本主題描述如何覆寫的預設記憶體管理行為 `CStringT` ，建立特別針對手邊的工作優化的配置器。

- [自訂字串管理員的實作為（基本方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [避免堆積爭用](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [自訂字串管理員的實作為（Advanced 方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT：自訂字串管理員的範例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>另請參閱

[CustomString 範例](../overview/visual-cpp-samples.md)
