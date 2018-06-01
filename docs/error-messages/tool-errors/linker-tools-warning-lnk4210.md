---
title: 連結器工具警告 LNK4210 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8700d9ad8eeef177de2f70f616cb0c06ba50670
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703674"
---
# <a name="linker-tools-warning-lnk4210"></a>連結器工具警告 LNK4210

> 區段*區段*存在; 可能那里無法處理的靜態初始設定式或終止函式

## <a name="remarks"></a>備註

靜態初始設定式或結束字元，導入了一些程式碼，但應用程式啟動時，則不會執行 VCRuntime 程式庫啟始程式碼或它的對等 （這需要執行的靜態初始設定式或結束字元）。 以下是一些需要靜態初始設定式或結束字元的程式碼的範例：

- 建構函式、 解構函式或虛擬函式表的全域類別變數。

- 初始化與非編譯時間常數的全域變數。

若要修正這個問題，請嘗試下列其中一項：

- 使用靜態初始設定式中移除所有的程式碼。

- 請勿使用[/NOENTRY](../../build/reference/noentry-no-entry-point.md)。 移除 /NOENTRY 之後，您可能也必須移除[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)在連結器命令列。

- 如果您的組建使用 /MT，加入 libcmt.lib，即 libvcruntime.lib、 和 libucrt.lib 在連結器命令列。 如果您的組建使用 /MTd，加入 libcmtd.lib、 vcruntimed.lib 和 libucrtd.lib。

- 時從 /clr: pure 編譯至 /clr，移除[/ENTRY](../../build/reference/entry-entry-point-symbol.md)從連結器列的選項。 這可讓 CRT 初始化，並可讓應用程式啟動時要執行的靜態初始設定式。 **/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

[/GS](../../build/reference/gs-buffer-security-check.md)編譯器選項需要初始化`__security_init_cookie`函式。 在執行中的 VCRuntime 程式庫啟動程式碼中預設會提供這類初始化`_DllMainCRTStartup`。

- 如果使用 /ENTRY，建置專案之後，如果 /ENTRY 以外傳遞函式`_DllMainCRTStartup`，函式必須呼叫`_CRT_INIT`初始化 CRT。 如果您的 DLL 會使用 /GS、 需要靜態初始設定式，或呼叫 MFC 或 ATL 程式碼的內容中單獨這個呼叫是不夠的。 請參閱[Dll 和 Visual c + + 執行階段程式庫行為](../../build/run-time-library-behavior.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
