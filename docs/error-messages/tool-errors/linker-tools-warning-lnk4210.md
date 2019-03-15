---
title: 連結器工具警告 LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816265"
---
# <a name="linker-tools-warning-lnk4210"></a>連結器工具警告 LNK4210

> 一節*一節*存在; 可能那里無法處理的靜態初始設定式或終止函式

## <a name="remarks"></a>備註

靜態初始設定式或結束字元，導入了一些程式碼，但應用程式啟動時，則不會執行 VCRuntime 程式庫啟動程式碼或其對等項目 （這需要執行的靜態初始設定式或結束字元）。 以下是一些需要靜態初始設定式或結束字元的程式碼的範例：

- 使用建構函式、 解構函式或虛擬函式表的全域類別變數。

- 初始化與非編譯時期常數的全域變數。

若要修正此問題，請嘗試下列其中一項：

- 使用靜態初始設定式中移除所有的程式碼。

- 請勿使用[/NOENTRY](../../build/reference/noentry-no-entry-point.md)。 移除 /NOENTRY 之後，您也可以移除[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)從連結器命令列。

- 如果您的組建使用 /MT，新增至您的連結器命令列 libcmt.lib、 libvcruntime.lib 和 libucrt.lib。 如果您的組建使用 /MTd，新增 libcmtd.lib、 vcruntimed.lib 和 libucrtd.lib。

- 時從 /clr: pure 編譯至 /clr，移除[/ENTRY](../../build/reference/entry-entry-point-symbol.md)從連結器列的選項。 這可讓 CRT 初始化，並可讓應用程式啟動時要執行的靜態初始設定式。 **/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

[/GS](../../build/reference/gs-buffer-security-check.md)編譯器選項需要使用`__security_init_cookie`函式。 在執行中的 VCRuntime 程式庫啟動程式碼中的預設會提供這項初始化`_DllMainCRTStartup`。

- 如果您的專案使用 /ENTRY 所建置，而且 /ENTRY 以外傳遞函式`_DllMainCRTStartup`，此函式必須呼叫`_CRT_INIT`初始化 CRT。 如果您的 DLL 會使用 /GS、 需要靜態初始設定式，或在 MFC 或 ATL 程式碼的內容中呼叫，單獨這個呼叫不足夠。 請參閱[Dll 和 Visual c + + 執行階段程式庫行為](../../build/run-time-library-behavior.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/linking.md)
