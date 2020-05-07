---
title: FreeLibrary 和 AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821547"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary

當不再需要 DLL 模組時，明確連結至 DLL 的進程會呼叫[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)函式。 此函式會遞減模組的參考計數。 而且，如果參考計數為零，則會從進程的位址空間取消對應。

在 MFC 應用程式中，使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而`FreeLibrary`非來卸載 MFC 擴充 DLL。 的介面（函數原型） `AfxFreeLibrary`與相同。 `FreeLibrary`

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C/c + + Dll](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
