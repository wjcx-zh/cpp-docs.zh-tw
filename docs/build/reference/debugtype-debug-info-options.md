---
title: -DEBUGTYPE （偵錯資訊選項） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66868f7648d20b890f3c1e8c40802d77e3af4544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (偵錯資訊選項)
/DEBUGTYPE 選項指定 /DEBUG 選項所產生的偵錯資訊類型。  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## <a name="arguments"></a>引數  
 CV  
 通知連結器發出符號、行號和 PDB 檔案中其他物件編譯資訊的偵錯資訊。 根據預設，會啟用此選項時**偵錯**指定和 **/DEBUGTYPE**未指定。  
  
 PDATA  
 通知連結器將 .pdata 和 .xdata 項目加入至 PDB 檔案中的偵錯資料流資訊。 根據預設，會啟用此選項時同時**偵錯**和 **/DRIVER**指定選項。 如果 **/DEBUGTYPE:PDATA**自行指定，連結器會自動包含偵錯符號 PDB 檔案中的。 如果 **/DEBUGTYPE:PDATA，修復**指定，則連結器不包含偵錯符號 PDB 檔案中的。  
  
 FIXUP  
 通知連結器將重新配置資料表項目加入至 PDB 檔案中的偵錯資料流資訊。 根據預設，會啟用此選項時同時**偵錯**和 **/profile**指定選項。 如果 **/DEBUGTYPE:FIXUP**或 **/DEBUGTYPE:FIXUP，PDATA**指定，則連結器不包含偵錯符號 PDB 檔案中的。  
  
 引數 **/DEBUGTYPE**可能以任何順序結合，並以逗號分隔。 **/DEBUGTYPE**選項和其引數不區分大小寫。  
  
## <a name="remarks"></a>備註  
 使用 **/DEBUGTYPE**選項可指定偵錯資料流中包含的重新配置資料表資料或.pdata 和.xdata 標頭資訊。 這會使連結器包含使用者模式程式碼的相關資訊，當核心模式程式碼中斷時，該資訊可以在核心偵錯工具中顯示。 若要讓偵錯符號可用時**修復**已指定，包括**CV**引數。  
  
 若要偵錯程式碼在使用者模式中，這是常見的應用程式， **/DEBUGTYPE**選項不需要。 根據預設，輸出指定偵錯編譯器參數 ([/Z7、 /Zi、 /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) 發出所有資訊所需的 Visual Studio 偵錯工具。 使用 **/DEBUGTYPE:PDATA**或 **/debugtype: cv，PDATA，修復**結合使用者模式和核心模式元件，例如裝置驅動程式的組態應用程式的程式碼偵錯。 如需有關核心模式偵錯工具的詳細資訊，請參閱[Windows 偵錯工具 （WinDbg、 KD、 CDB、 NTSD）](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## <a name="see-also"></a>另請參閱  
 [/DEBUG （產生偵錯資訊）](../../build/reference/debug-generate-debug-info.md)   
 [/ 驅動程式 （Windows NT 核心模式驅動程式）](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [/PROFILE （效能工具分析工具）](../../build/reference/profile-performance-tools-profiler.md)   
 [偵錯工具 （WinDbg、 KD、 CDB、 NTSD） 的 windows](http://go.microsoft.com/fwlink/p?LinkID=285651)