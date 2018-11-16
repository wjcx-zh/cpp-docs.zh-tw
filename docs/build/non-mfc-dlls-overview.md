---
title: 非 MFC DLL：概觀
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 15cceb80b0f771c0c304572e2263b1479d6b0db7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693018"
---
# <a name="non-mfc-dlls-overview"></a>非 MFC DLL：概觀

非 MFC 的 DLL 是在內部，不會使用 MFC 的 DLL，而且在 DLL 中匯出的函式可以呼叫由 MFC 或非 MFC 可執行檔。 從非 MFC DLL 使用標準的 C 介面通常被匯出函式。

如需非 MFC Dll 的詳細資訊，請參閱 <<c0> [ 動態連結程式庫](/windows/desktop/dlls/dynamic-link-libraries)Windows SDK 中。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [逐步解說： 建立和使用動態連結程式庫](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [從 DLL 匯出](../build/exporting-from-a-dll.md)

- [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)

- [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [靜態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](../build/extension-dlls-overview.md)

## <a name="see-also"></a>另請參閱

[DLL 的種類](../build/kinds-of-dlls.md)