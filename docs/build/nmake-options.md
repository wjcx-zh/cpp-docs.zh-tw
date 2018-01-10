---
title: "NMAKE 選項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef3b987de737d8300f88690754456b73c946180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-options"></a>NMAKE 選項
下表詳述 NMAKE 選項。 選項會加上斜線 （/） 或破折號 （-） 和不區分大小寫。 使用[！CMDSWITCHES](../build/makefile-preprocessing-directives.md)變更 Tools.ini 或 makefile 中的選項設定。  
  
|選項|用途|  
|------------|-------------|  
|/ A|強制建置所有評估的目標，即使未過期相對於相依性。 不強制建置不相關的目標。|  
|B|即使時間戳記相等的則會強制建置。 建議只針對非常快速的系統 （解決方式或較少的兩秒）。|  
|/C|抑制預設輸出，包括非嚴重 NMAKE 錯誤或警告，時間戳記，以及 NMAKE 著作權訊息。 隱藏 /k 所發出的警告|  
|/D|顯示評估時間戳記的每個目標和相依性和一則訊息時的目標不存在。 用於/P 與偵錯 makefile。 使用**！CMDSWITCHES**以設定或清除 /D makefile 的一部分。|  
|/E|會使環境變數，以覆寫 makefile 的巨集定義。|  
|/ERRORREPORT [無 &#124;提示字元 &#124;佇列 &#124;傳送]|如果在執行階段失敗 nmake.exe，您可以使用 /ERRORREPORT 需這些內部錯誤，將資訊傳送給 Microsoft。<br /><br /> 如需 /ERRORREPORT 的詳細資訊，請參閱[/errorReport （回報編譯器內部錯誤）](../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|/F`filename`|指定`filename`為 makefile。 可以在之前的空格或定位字元`filename`。 指定一次針對每個 makefile /F。 若要提供從標準輸入 makefile，指定虛線 （-） `filename`，且結尾 F6 或 CTRL + Z 的鍵盤輸入。|  
|/G|顯示包含使用 ！INCLUDE 指示詞。  請參閱[Makefile 前置處理指示詞](../build/makefile-preprocessing-directives.md)如需詳細資訊。|  
|/ 說明 /？|顯示 NMAKE 命令列語法的簡短摘要。|  
|/I|會忽略所有命令的結束代碼。 若要設定或清除 /I makefile 的一部分，請使用**！CMDSWITCHES**。 若要忽略的 makefile 一部分的結束代碼，使用破折號 （-） 命令修飾詞或[。忽略](../build/dot-directives.md)。 如果同時指定，會覆寫 /K。|  
|/K|如果命令傳回錯誤，會繼續建置不相關的相依性。 同時會發出警告，並傳回的結束代碼為 1。 根據預設，如果任何命令傳回非零結束代碼，暫止 NMAKE。 /K 警告會被 /C 隱藏;/I 會覆寫 /K，如果同時指定這兩者。|  
|/N|顯示，但不會執行命令的方式。前置處理的命令會執行。 不會顯示遞迴 NMAKE 呼叫命令。 適用於偵錯 makefile 和檢查時間戳記。 若要設定或清除 /N makefile 的一部分，請使用**！CMDSWITCHES**。|  
|/NOLOGO|隱藏 NMAKE 著作權訊息。|  
|/P|顯示資訊 (巨集、 推斷規則、 目標、 [。後置字元](../build/dot-directives.md)清單) 至標準輸出，然後執行組建。 如果沒有 makefile 或命令列的目標已存在，它會顯示資訊僅供參考。 使用 /D makefile 的偵錯。|  
|/Q|檢查目標; 的時間戳記不會執行建置。 如果任何目標不會傳回結束代碼為零如果所有目標都是最新，則為非零結束代碼。 前置處理的命令會執行。 從批次檔執行 NMAKE 時很有用。|  
|/R|清除**。尾碼**清單，並忽略推斷規則和 Tools.ini 檔案中所定義或預先定義的巨集。|  
|/S|隱藏的執行命令。 若要抑制顯示部分的 makefile，請使用 **@** 命令修飾詞或[。無訊息](../build/dot-directives.md)。 若要設定或清除 /S makefile 的一部分，請使用**！CMDSWITCHES**。|  
|/T|更新的命令列的目標 （或第一個 makefile 目標） 的時間戳記和執行前置處理命令，但不是執行組建。|  
|/U|必須 /N.搭配使用 傾印內嵌 NMAKE 檔，以便 /N 輸出可以用作批次檔。|  
|/X`filename`|NMAKE 錯誤輸出會傳送`filename`而不是標準錯誤。 可以在之前的空格或定位字元`filename`。 若要傳送至標準輸出的錯誤輸出，請為指定虛線 （-） `filename`。 不會影響命令的輸出到標準錯誤。|  
|/Y|停用批次模式推斷規則。 選取此選項時，所有的批次模式推斷規則會被當做一般的推斷規則。|  
  
## <a name="see-also"></a>請參閱  
 [執行 NMAKE](../build/running-nmake.md)