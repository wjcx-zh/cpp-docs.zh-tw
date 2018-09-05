---
title: ML 和 ML64 命令列參考 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ML
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41d3603bc09b7c63fdd152e1c7d5921c2bb3eb7c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693399"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令列參考

會組譯及連結一或多個組件語言原始程式檔。 命令列選項會區分大小寫。

如需有關 ml64.exe 的詳細資訊，請參閱[MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="syntax"></a>語法

> ML [[*選項*]] *filename* [[[[*選項*]] *filename*]]

> ML64 [[*選項*]] *filename* [[[[*選項*]] *filename*]]...[[/ link> *linkoptions*]]

### <a name="parameters"></a>參數

*options*<br/>
下表所列的選項。

|選項|動作|
|------------|------------|
|**/AT**|可讓小型記憶體模型支援。 可讓程式碼建構違反.com 格式檔案的需求的錯誤訊息。 請注意，這相當於[。模型](../../assembler/masm/dot-model.md)**微小**指示詞。<br /><br /> Ml64.exe 中無法使用。|
|**/Bi** *檔名*|選取替代的連結器。|
|**/c**|只會組合。 不會連結。|
|**/coff**|產生通用物件檔案格式 (COFF) 物件模組的類型。 通常開發所需的 Win32 組件語言。<br /><br /> Ml64.exe 中無法使用。|
|**/Cp**|會保留所有的使用者識別碼的大小寫。|
|**/Cu**|將所有識別碼都對應為大寫 （預設值）。<br /><br /> Ml64.exe 中無法使用。|
|**/Cx**|會保留在公用和 extern 符號的大小寫。|
|**/D** *符號*[[=*值*]]|定義具有指定名稱的文字巨集。 如果*值*會遺失，其為空白。 以空格分隔的多個權杖必須括在引號內。|
|**/EP**|產生前置處理過的來源清單 （傳送至 STDOUT）。 請參閱 **/Sf**。|
|**/ERRORREPORT** [ **NONE** &AMP;#124; **提示** &AMP;#124; **佇列** &AMP;#124; **傳送**]|如果 ml.exe 或 ml64.exe 會在執行階段失敗，您可以使用 **/ERRORREPORT**有關這些內部錯誤，傳送給 Microsoft 的資訊。<br /><br /> 如需詳細資訊 **/ERRORREPORT**，請參閱[/errorReport （回報編譯器內部錯誤）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|
|**/F** *hexnum*|設定堆疊大小*hexnum*位元組 (這是與相同 **/連結/堆疊**:*數目*)。 值必須是以十六進位標記法來表示。 必須有之間保留一個空格 **/F**並*hexnum*。|
|**/Fe** *檔名*|名稱的可執行檔。|
|**/Fl**[[*filename*]]|會產生組合的程式碼清單。 請參閱 **/Sf**。|
|**/Fm**[[*filename*]]|建立連結器對應檔案。|
|**/Fo** *檔名*|命名物件檔案。 如需詳細資訊，請參閱 < 備註 > 一節。|
|**/FPi**|會產生浮點算術 （只混合語言） 的模擬器修正-工作。<br /><br /> Ml64.exe 中無法使用。|
|**/Fr**[[*filename*]]|產生來源瀏覽器.sbr 檔案。|
|**/FR**[[*filename*]]|會產生原始程式瀏覽器.sbr 檔擴充的格式。|
|**/Gc**|指定使用 FORTRAN 或依照 pascal 命名法樣式函式呼叫和命名慣例。 與相同**選項的語言： PASCAL**。<br /><br /> Ml64.exe 中無法使用。|
|**/Gd**|指定使用 c-style 函式呼叫和命名慣例。 與相同**選項的語言： C**。<br /><br /> Ml64.exe 中無法使用。|
|**/GZ**|指定使用 __stdcall 函式呼叫和命名慣例。  與相同**選項的語言： STCALL**。<br /><br /> Ml64.exe 中無法使用。|
|**/H** *數目*|將數字的有效字元數限制外部名稱。 預設為 31 個字元。<br /><br /> Ml64.exe 中無法使用。|
|**/help**|呼叫 QuickHelp ML 的說明。|
|**/I** *路徑名稱*|設定包含檔案路徑。 最多 10 個 **/I**允許選項。|
|**/nologo**|抑制成功的組件的訊息。|
|**/omf**|產生物件模組檔案格式 (OMF) 類型的物件模組。  **/omf**意味著 **/c**;ML.exe 不支援連結 OMF 物件。<br /><br /> Ml64.exe 中無法使用。|
|**/Sa**|開啟的所有可用的資訊清單。|
|**/safeseh**|標示為包含任何例外狀況處理常式，或包含宣告使用的例外狀況處理常式物件[。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> Ml64.exe 中無法使用。|
|**/Sf**|加入第一個階段清單至清單的檔案。|
|**/Sl** *寬度*|設定來源，其中列出每一行的字元數的線條寬度。 範圍是 60 到 255 個或 0。 預設值為 0。 與相同[網頁](../../assembler/masm/page.md)寬度。|
|**/Sn**|產生清單時，請關閉符號表。|
|**/Sp** *長度*|設定頁面長度的來源，其中列出在每頁行數。 範圍是到 255 個 10 或 0。 預設值為 0。 與相同[網頁](../../assembler/masm/page.md)長度。|
|**/Ss** *文字*|指定原始檔清單的文字。 與相同[副標題](../../assembler/masm/subtitle.md)文字。|
|**/St** *文字*|指定原始檔清單的標題。 與相同[TITLE](../../assembler/masm/title.md)文字。|
|**/Sx**|開啟清單中，則為 false 的條件。|
|**/Ta** *檔名*|組合名稱結尾不是.asm 延伸模組的原始程式檔。|
|**/w**|與相同 **/W0/WX**。|
|**/W** *層級*|設定警告層級中，其中*層級*= 0、 1、 2 或 3。|
|**/WX**|如果會產生警告，則傳回錯誤碼。|
|**/X**|忽略 INCLUDE 環境路徑。|
|**/Zd**|產生目的檔中的行號資訊。|
|**/Zf**|可公開的所有符號。|
|**/Zi**|產生目的檔中的 CodeView 資訊。|
|**/Zm**|可讓**M510** MASM 5.1 的最大相容性選項。<br /><br /> Ml64.exe 中無法使用。|
|**/Zp**[[*對齊*]]|指定的位元組界限上封裝結構。 *對齊*可以是 1、 2 或 4。|
|**/Zs**|執行僅檢查語法。|
|**/?**|顯示 ML 命令列語法的摘要。|

*filename*<br/>
檔案的檔名。

*linkoptions*<br/>
連結選項。  請參閱[連結器選項](../../build/reference/linker-options.md)如需詳細資訊。

## <a name="remarks"></a>備註

一些命令列選項，以 ML 和 ML64 會放置區分特性。 例如，因為 ML 和 ML64 可以接受數個 **/c**選項，任何對應 **/Fo**之前，必須指定選項 **/c**。 下列的命令列範例會說明每個組件檔案規格的物件檔案規格：

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>環境變數

|變數|描述|
|--------------|-----------------|
|INCLUDE|指定搜尋 include 檔的路徑。|
|ML|指定預設的命令列選項。|
|TMP|指定暫存檔的路徑。|

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>
[Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>