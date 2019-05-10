---
title: LoadLibrary 和 AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: 661d7742fb0fedae45bc063ba3821193d6c5438e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220606"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

處理呼叫[LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)或是[LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) 明確地連結至 DLL。 如果函式成功，它會指定的 DLL 對應到呼叫處理序的位址空間，並可與其他函式中明確連結的 DLL 中傳回的控制代碼，例如`GetProcAddress`和`FreeLibrary`。

`LoadLibrary` 嘗試使用隱含連結使用的相同搜尋順序找出 DLL。 如果系統找不到 DLL 或進入點函式會傳回 FALSE，`LoadLibrary`會傳回 NULL。 如果呼叫`LoadLibrary`指定已經對應到呼叫的處理序的位址空間的 DLL 模組函式會傳回 DLL 並遞增的控制代碼之參考計數的模組。

如果 DLL 進入點函式，則作業系統會呼叫函式呼叫的執行緒內容中`LoadLibrary`。 如果 DLL 已經連結至處理程序因為前一個呼叫，不會呼叫進入點函式`LoadLibrary`具有任何對應呼叫`FreeLibrary`函式。

載入 MFC 擴充 Dll 的 MFC 應用程式，我們建議您使用`AfxLoadLibrary`而不是`LoadLibrary`。 `AfxLoadLibrary` 處理執行緒同步處理，才能呼叫`LoadLibrary`。 介面 （函式原型），以`AfxLoadLibrary`等同於`LoadLibrary`。

如果 Windows 無法載入 DLL，處理序可以嘗試從錯誤復原。 比方說，此程序無法通知錯誤的使用者，並要求使用者指定 dll 的另一個路徑。

> [!IMPORTANT]
> 請確定指定的任何 Dll 的完整路徑。 載入檔案時，會先搜尋目前的目錄。 如果您不限定檔案的路徑，可能會載入並不是預期的檔案。 若要避免這個問題的另一個方法是使用[/DEPENDENTLOADFLAG](reference/dependentloadflag.md)連結器選項。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>另請參閱

- [建立 C /C++在 Visual Studio 中的 Dll](dlls-in-visual-cpp.md)
