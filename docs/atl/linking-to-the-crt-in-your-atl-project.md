---
title: 連結到 ATL 專案中的 CRT
ms.date: 11/04/2016
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
ms.openlocfilehash: b117165c82e51a59fe691b90f8ef92d0ba802cbc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287943"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>連結到 ATL 專案中的 CRT

[C 執行階段程式庫](../c-runtime-library/crt-library-features.md)(CRT) 提供許多有用的功能，可以讓程式設計更容易在 ATL 開發。 所有的 ATL 專案連結到 CRT 程式庫。 您所見連結中的方法的優缺點[優點和權衡取捨的方法用來連結到 CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)。

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>連結到 CRT 程式映像上的效果

如果您以靜態方式連結到 CRT，CRT 的程式碼放在您的可執行檔映像，您不需要對系統執行您的映像中的 CRT DLL。 如果您以動態方式連結到 CRT，CRT DLL 中的程式碼的參考會放在您的映像，但不是程式碼本身中。 為了讓您指定的系統上執行的映像，此 CRT DLL 必須存在於該系統上。 即使當您以動態方式連結到 CRT，您可能會發現一些程式碼可以以靜態方式連結 (例如`DllMainCRTStartup`)。

當您連結您的映像時，您明確或隱含指定的作業系統將會呼叫之後載入映像的進入點。 預設進入點的 DLL， `DllMainCRTStartup`。 Exe，它是`WinMainCRTStartup`。 您可以覆寫 /ENTRY 連結器選項的預設值。 CRT 提供實作`DllMainCRTStartup`， `WinMainCRTStartup`，和`wWinMainCRTStartup`（Unicode 進入點的 exe）。 這些 CRT 提供進入點通用的物件上呼叫建構函式，並初始化其他有些 CRT 函式所使用的資料結構。 此啟動程式碼會將大約 25 K 加入至您的映像中，如果它以靜態方式連結。 如果它以動態方式連結，大多數的程式碼是 DLL，因此您的映像大小保持小。

如需詳細資訊，請參閱連結器主題[/ENTRY （進入點符號）](../build/reference/entry-entry-point-symbol.md)。

## <a name="optimization-options"></a>最佳化選項

使用連結器選項/opt:nowin98 可以進一步減少 10 K、 預設 ATL 控制項損失的增加載入 Windows 98 系統上的時間。 如需有關連結選項的詳細資訊，請參閱[/OPT （最佳化）](../build/reference/opt-optimizations.md)。

## <a name="see-also"></a>另請參閱

[使用 ATL 和 C 執行階段程式碼進行程式設計](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL 和 Visual C++ 執行階段程式庫行為](../build/run-time-library-behavior.md)
