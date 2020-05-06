---
title: 擴充 DLL：概觀
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221367"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 延伸模組 DLL：概觀

MFC 擴充 DLL 是一個 DLL，通常會執行衍生自現有 MFC 程式庫類別的可重複使用類別。 MFC 擴充 Dll 是使用 MFC 的動態連結程式庫版本（也稱為 MFC 的共用版本）所建立。 只有以共用版本的 MFC 建立的 MFC 可執行檔（應用程式或一般 MFC Dll），才可以使用 MFC 擴充 DLL。 有了 MFC 延伸 DLL，您就可以從 MFC 衍生新的自訂類別，然後將這個擴充版本的 MFC 提供給呼叫您 DLL 的應用程式。

擴充 Dll 也可以用來在應用程式和 DLL 之間傳遞 MFC 衍生的物件。 與傳遞物件相關聯的成員函式存在於建立物件的模組中。 當使用 MFC 的共用 DLL 版本時，這些函式會正確匯出，因此您可以在應用程式和它所載入的 MFC 延伸 Dll 之間，自由地傳遞 MFC 或 MFC 衍生的物件指標。

如需滿足 MFC 延伸模組 DLL 基本需求的 DLL 範例，請參閱 MFC 範例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。 特別是，請查看 Testdll1 .cpp 和 Testdll2 .cpp 檔案。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化 MFC 延伸模組 DLL](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [MFC 擴充 Dll](extension-dlls.md)

- [在一般 MFC Dll 中使用資料庫、OLE 和通訊端 MFC 延伸 Dll](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>請參閱

[DLL 的種類](kinds-of-dlls.md)
