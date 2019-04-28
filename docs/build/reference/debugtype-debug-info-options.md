---
title: /DEBUGTYPE (偵錯資訊選項)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 00e3cb61f8ec9aa707bb72aa9ff05a64f98d4e47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272291"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (偵錯資訊選項)

/DEBUGTYPE 選項指定 /DEBUG 選項所產生的偵錯資訊類型。

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>引數

**CV**<br/>
通知連結器發出符號、行號和 PDB 檔案中其他物件編譯資訊的偵錯資訊。 根據預設，會啟用此選項時 **/偵錯**指定並 **/DEBUGTYPE**未指定。

**PDATA**<br/>
通知連結器將 .pdata 和 .xdata 項目加入至 PDB 檔案中的偵錯資料流資訊。 根據預設，會啟用此選項時同時 **/偵錯**並 **/DRIVER**指定選項。 如果 **/DEBUGTYPE:PDATA**自行指定，連結器會自動包含偵錯 PDB 檔案中的符號。 如果 **/DEBUGTYPE:PDATA，修復**指定，連結器不會包含偵錯 PDB 檔案中的符號。

**FIXUP**<br/>
通知連結器將重新配置資料表項目加入至 PDB 檔案中的偵錯資料流資訊。 根據預設，會啟用此選項時同時 **/偵錯**並 **/設定檔**指定選項。 如果 **/DEBUGTYPE:FIXUP**或是 **/DEBUGTYPE:FIXUP，PDATA**指定，連結器不會包含偵錯 PDB 檔案中的符號。

引數 **/DEBUGTYPE**可能以任何順序結合，以逗號分隔。 **/DEBUGTYPE**選項和其引數不區分大小寫。

## <a name="remarks"></a>備註

使用 **/DEBUGTYPE**選項來指定包含重新配置資料表資料或.pdata 和.xdata 標頭資訊的偵錯資料流中。 這會使連結器包含使用者模式程式碼的相關資訊，當核心模式程式碼中斷時，該資訊可以在核心偵錯工具中顯示。 若要讓偵錯符號時**修復**會指定，包含**CV**引數。

在使用者模式中，也就是應用程式的常見項目，程式碼偵錯 **/DEBUGTYPE**選項，則不需要。 根據預設，輸出指定偵錯的編譯器參數 ([/z7，/Zi，/ZI](z7-zi-zi-debug-information-format.md)) 發出所有資訊所需的 Visual Studio 偵錯工具。 使用 **/DEBUGTYPE:PDATA**或是 **/debugtype: cv，PDATA，修復**結合使用者模式和核心模式元件，例如裝置驅動程式的組態應用程式的程式碼偵錯。 如需有關核心模式偵錯工具的詳細資訊，請參閱[偵錯工具的 Windows （WinDbg、 KD、 CDB、 NTSD）](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>另請參閱

[/DEBUG (產生偵錯資訊)](debug-generate-debug-info.md)<br/>
[/DRIVER (Windows NT 核心模式驅動程式)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (效能工具分析工具)](profile-performance-tools-profiler.md)<br/>
[偵錯工具 （WinDbg、 KD、 CDB、 NTSD） 的 Windows](/windows-hardware/drivers/debugger/index)
