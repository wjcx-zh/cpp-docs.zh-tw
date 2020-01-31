---
title: LoadLibrary 和 AfxLoadLibrary
description: 使用 LoadLibrary 和 AfxLoadLibrary 在 MSVC 中明確載入 Dll。
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821534"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

進程會呼叫[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)或[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) ，以明確連結到 DLL。 （MFC 應用程式會使用[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)或[AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)）。如果函式成功，它會將指定的 DLL 對應到呼叫進程的位址空間，並傳回 DLL 的控制碼。 在用於明確連結的其他函式中，需要控制碼，例如 `GetProcAddress` 和 `FreeLibrary`。 如需詳細資訊，請參閱[明確連結](linking-an-executable-to-a-dll.md#linking-explicitly)。

`LoadLibrary` 嘗試使用用於隱含連結的相同搜尋順序來找出 DLL。 `LoadLibraryEx` 可讓您更充分掌控搜尋路徑的順序。 如需詳細資訊，請參閱[動態連結程式庫搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order)。 如果系統找不到 DLL，或如果進入點函式傳回 FALSE，`LoadLibrary` 會傳回 Null。 如果 `LoadLibrary` 的呼叫指定已對應到呼叫進程之位址空間的 DLL 模組，此函式會傳回 DLL 的控制碼，並遞增模組的參考計數。

如果 DLL 具有進入點函式，作業系統會在呼叫 `LoadLibrary` 或 `LoadLibraryEx`的執行緒內容中呼叫函式。 如果 DLL 已附加至進程，則不會呼叫進入點函式。 當先前呼叫 `LoadLibrary` 或 DLL 的 `LoadLibraryEx` 沒有對應的 `FreeLibrary` 函數呼叫時，就會發生這種情況。

對於載入 MFC 延伸 Dll 的 MFC 應用程式，我們建議您使用 `AfxLoadLibrary` 或 `AfxLoadLibraryEx`，而不是 `LoadLibrary` 或 `LoadLibraryEx`。 MFC 函式會在明確載入 DLL 之前處理執行緒同步處理。 `AfxLoadLibrary` 和 `AfxLoadLibraryEx` 的介面（函數原型）與 `LoadLibrary` 和 `LoadLibraryEx`相同。

如果 Windows 無法載入 DLL，您的進程可能會嘗試從錯誤復原。 例如，它可以通知使用者錯誤，然後要求另一個 DLL 路徑。

> [!IMPORTANT]
> 請務必指定任何 Dll 的完整路徑。 當 `LoadLibrary`載入檔案時，可能會先搜尋目前的目錄。 如果您沒有完整限定檔案的路徑，可能會載入所需檔案以外的檔案。 當您建立 DLL 時，請使用[/DEPENDENTLOADFLAG](reference/dependentloadflag.md)連結器選項來指定靜態連結 DLL 相依性的搜尋順序。 在您的 Dll 中，使用明確載入的相依性的完整路徑，並 `LoadLibraryEx` 或 `AfxLoadLibraryEx` 呼叫參數來指定模組搜尋順序。 如需詳細資訊，請參閱[動態連結程式庫安全性](/windows/win32/dlls/dynamic-link-library-security)和[動態連結程式庫搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order)。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>請參閱

- [在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
