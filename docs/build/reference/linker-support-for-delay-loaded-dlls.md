---
title: 延遲載入 DLL 的連結器支援
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: b6e514a6b13aced4fcd765df091810504f948588
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809570"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>延遲載入 DLL 的連結器支援

MSVC 連結器現在支援 Dll 的延遲的載入。 這減輕您需要使用 Windows SDK 函式**LoadLibrary**並**GetProcAddress**實作延遲載入的 DLL。

在 Visual c + + 6.0 中之前, 在執行階段載入 DLL 的唯一方式是使用**LoadLibrary**並**GetProcAddress**; 作業系統會載入 DLL 時可執行檔或 DLL 使用載入它。

隱含連結至 dll 時，Visual c + + 6.0 中，從開始，連結器會提供選項，以延遲載入 DLL，直到程式該 DLL 中呼叫的函式。

應用程式可能會延遲載入 DLL，使用[/DELAYLOAD （延遲載入匯入）](delayload-delay-load-import.md)使用協助程式函式 （Visual c + + 所提供的預設實作） 的連結器選項。 Helper 函式會藉由呼叫在執行階段中載入的 DLL **LoadLibrary**並**GetProcAddress**您。

您應該考慮延遲載入 DLL，如果：

- 您的程式可能不會在 DLL 中呼叫函式。

- 在您的程式執行，可能不取得呼叫 DLL 中的函式。

其中一個建置期間，可以指定延遲的載入 DLL。EXE 或。DLL 專案。 答:。延遲的一個或多個 Dll 載入的 DLL 專案不應該自己呼叫的延遲載入的進入點位在 Dllmain 中。

下列主題將描述延遲載入 Dll:

- [指定要延遲載入的 DLL](specifying-dlls-to-delay-load.md)

- [明確卸載延遲載入的 DLL](explicitly-unloading-a-delay-loaded-dll.md)

- [載入延遲載入 DLL 的所有匯入](loading-all-imports-for-a-delay-loaded-dll.md)

- [繫結匯入](binding-imports.md)

- [錯誤處理和通知](error-handling-and-notification.md)

- [傾印延遲載入的匯入](dumping-delay-loaded-imports.md)

- [延遲載入 DLL 的條件約束](constraints-of-delay-loading-dlls.md)

- [了解協助協助程式函式](understanding-the-helper-function.md)

- [開發您自己的協助程式函式](developing-your-own-helper-function.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../dlls-in-visual-cpp.md)<br/>
[MSVC 連結器參考](linking.md)
