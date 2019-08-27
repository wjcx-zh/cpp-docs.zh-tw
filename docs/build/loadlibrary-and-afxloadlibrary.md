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
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493214"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

進程會呼叫[LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)或[LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)), 以明確連結至 DLL。 如果函式成功, 它會將指定的 DLL 對應到呼叫進程的位址空間, 並將控制碼傳回給可與明確連結中的其他函數搭配使用的 dll (例如`GetProcAddress`和`FreeLibrary`)。

`LoadLibrary`嘗試使用用於隱含連結的相同搜尋順序來找出 DLL。 如果系統找不到 DLL, 或如果進入點函式傳回 FALSE, `LoadLibrary`則會傳回 Null。 如果呼叫`LoadLibrary`指定的 dll 模組已對應到呼叫進程的位址空間, 則函式會傳回 dll 的控制碼, 並遞增模組的參考計數。

如果 DLL 具有進入點函式, 作業系統就會`LoadLibrary`在呼叫的執行緒內容中呼叫函數。 如果 DLL 已附加至進程, 且先前的呼叫`LoadLibrary`沒有對函式的對應呼叫`FreeLibrary` , 則不會呼叫此進入點函式。

對於載入 mfc 延伸 dll 的 mfc 應用程式, 我們建議您使用`AfxLoadLibrary` `LoadLibrary`而不是。 `AfxLoadLibrary`在呼叫`LoadLibrary`之前處理執行緒同步。 的介面 (函數原型) `AfxLoadLibrary`與`LoadLibrary`相同。

如果 Windows 無法載入 DLL, 進程可能會嘗試從錯誤中復原。 例如, 處理常式可能會通知使用者錯誤, 並要求使用者指定 DLL 的另一個路徑。

> [!IMPORTANT]
> 請務必指定任何 Dll 的完整路徑。 載入檔案時, 會先搜尋目前目錄。 如果您沒有限定檔案的路徑, 可能會載入不是預期檔案的檔案。 另一個避免這種情況的方法是使用[/DEPENDENTLOADFLAG](reference/dependentloadflag.md)連結器選項。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
