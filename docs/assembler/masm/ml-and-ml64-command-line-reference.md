---
title: "ML 和 ML64 命令列參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ML
dev_langs: C++
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a7a2a5baadab38283b621cb2f6ae99b36fe0a50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令列參考
會組譯及連結一或多個組件語言原始程式檔。 命令列選項會區分大小寫。  
  
 如需有關 ml64.exe 的詳細資訊，請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="syntax"></a>語法  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>參數  
 `options`  
 下表所列的選項。  
  
|選項|動作|  
|------------|------------|  
|**/AT**|啟用小記憶體模型支援。 可讓違反.com 格式檔案的需求的程式碼建構的錯誤訊息。 請注意，這相當於[。模型](../../assembler/masm/dot-model.md)**微小**指示詞。<br /><br /> 不適用於 ml64.exe。|  
|**/Bi**`filename`|選取替代的連結器。|  
|**/c**|只會組譯。 未連結。|  
|**/coff 一起使用**|會產生通用物件檔案格式 (COFF) 物件模組的類型。 通常所需的 Win32 組件語言的開發。<br /><br /> 不適用於 ml64.exe。|  
|**/Cp**|會保留所有的使用者識別碼的大小寫。|  
|**/Cu**|將所有的識別項對應至英文大小寫 （預設值）。<br /><br /> 不適用於 ml64.exe。|  
|**/Cx**|保留大小寫的公開憑證與外部符號。|  
|**/D** `symbol`[[=`value`]]|定義具有指定名稱的文字巨集。 如果`value`已遺失，其為空白。 以空格分隔的多個權杖必須括在引號中。|  
|**/EP**|會產生前置處理過的來源清單 （傳送至 STDOUT）。 請參閱**/Sf**。|  
|**/ERRORREPORT** [ **NONE** &#124;**提示**&#124;**佇列**&#124;**傳送**]|如果 ml.exe 或 ml64.exe 無法在執行階段，您可以使用**/ERRORREPORT**需這些內部錯誤，將資訊傳送給 Microsoft。<br /><br /> 如需有關**/ERRORREPORT**，請參閱[/errorReport （回報編譯器內部錯誤）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|**/F**`hexnum`|設定堆疊大小`hexnum`位元組 (這是與相同**/連結/堆疊**:`number`)。 此值必須表示的十六進位表示法。 必須有之間的空格**/F**和`hexnum`。|  
|**/Fe**`filename`|可執行檔的名稱。|  
|**/Fl**[[`filename`]]|會產生組合的程式碼清單。 請參閱**/Sf**。|  
|**/Fm**[[`filename`]]|建立連結器對應檔。|  
|**/Fo**`filename`|命名物件檔案。 如需詳細資訊，請參閱 < 備註 > 一節。|  
|**/Fpi**|會產生浮點算術 （只有混合語言） 的模擬器修復的動作。<br /><br /> 不適用於 ml64.exe。|  
|**/Fr**[[`filename`]]|產生來源瀏覽器.sbr 檔案。|  
|**/FR**[[`filename`]]|會產生來源瀏覽器.sbr 檔的延伸的格式。|  
|**/Gc**|指定使用 FORTRAN 或 Pascal 樣式函式呼叫和命名慣例。 與相同**選項語言： PASCAL**。<br /><br /> 不適用於 ml64.exe。|  
|**/Gd**|指定使用的 C 樣式函式呼叫和命名慣例。 與相同**選項語言： C**。<br /><br /> 不適用於 ml64.exe。|  
|**/GZ**|指定使用 __stdcall 函式呼叫和命名慣例。  與相同**選項語言： STCALL**。<br /><br /> 不適用於 ml64.exe。|  
|**/H**`number`|數字的顯著性字元限制外部名稱。 預設值為 31 個字元。<br /><br /> 不適用於 ml64.exe。|  
|**/help**|呼叫 QuickHelp ML 的說明。|  
|**/I**`pathname`|Include 檔的設定路徑。 最多 10 個**/I**允許選項。|  
|**/nologo**|抑制成功的組件的訊息。|  
|**/omf**|產生物件模組檔案格式 (OMF) 類型的物件模組。  **/omf**意味著**/c**;ML.exe 不支援連結 OMF 物件。<br /><br /> 不適用於 ml64.exe。|  
|**/Sa**|開啟的所有可用的資訊清單。|  
|**/safeseh**|將標示為包含任何例外狀況處理常式，或包含宣告與例外狀況處理常式物件[。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> 不適用於 ml64.exe。|  
|**/Sf**|加入第一階段清單到清單的檔案。|  
|**/Sl**`width`|設定來源清單中每行字元的線條寬度。 範圍是 0 到 255 個 60。 預設值為 0。 與相同[頁面](../../assembler/masm/page.md)寬度。|  
|**/Sn**|產生清單時，請關閉符號表。|  
|**/Sp**`length`|設定頁面長度的來源清單中每頁的行。 範圍是 0 到 255 個 10。 預設值為 0。 與相同[頁面](../../assembler/masm/page.md)長度。|  
|**/Ss**`text`|指定文字來源清單。 與相同[副標題](../../assembler/masm/subtitle.md)文字。|  
|**/St**`text`|指定來源清單的標題。 與相同[標題](../../assembler/masm/title.md)文字。|  
|**/Sx**|開啟 false 條件清單中。|  
|**/Ta**`filename`|將原始程式檔名稱結尾不.asm 擴充功能的組合。|  
|**/w**|與相同**/W0/WX**。|  
|**/W**`level`|設定警告層級，其中`level`= 0、 1、 2 或 3。|  
|**/WX**|如果產生的警告，則傳回錯誤碼。|  
|**/X**|忽略 INCLUDE 環境路徑。|  
|**/Zd**|目的檔中產生行號資訊。|  
|**/Zf**|會公開所有符號。|  
|**/Zi**|目的檔中產生 CodeView 資訊。|  
|**/Zm**|可讓**M510** MASM 5.1 與最大的相容性的選項。<br /><br /> 不適用於 ml64.exe。|  
|**/Zp**[[`alignment`]]|指定的位元組界限上封裝結構。 `alignment`可以是 1、 2 或 4。|  
|**/Zs**|執行僅檢查語法。|  
|**/?**|顯示 ML 命令列語法的摘要。|  
  
 `filename`  
 檔案的檔名。  
  
 `linkoptions`  
 連結選項。  請參閱[連結器選項](../../build/reference/linker-options.md)如需詳細資訊。  
  
## <a name="remarks"></a>備註  
 ML 和 ML64 的一些命令列選項是放置區分。 例如，因為 ML 和 ML64 可以接受數個**/c**選項，任何對應**/Fo**必須指定選項，然後再**/c**。 下列命令列範例將說明每個組件檔案規格的物件檔案規格：  
  
 **ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>環境變數  
  
|變數|描述|  
|--------------|-----------------|  
|INCLUDE|指定 include 檔搜尋路徑。|  
|ML|指定預設的命令列選項。|  
|TMP|指定暫存檔的路徑。|  
  
## <a name="see-also"></a>請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)   
 [Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)