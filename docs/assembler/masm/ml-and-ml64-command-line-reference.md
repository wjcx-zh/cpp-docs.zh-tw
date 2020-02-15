---
title: ML 和 ML64 命令列參考
description: Microsoft MASM ML 和 ML64 組合器命令列選項的參考指南。
ms.date: 02/09/2020
f1_keywords:
- ML
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
ms.openlocfilehash: b5c5a79417cb141da3d5cfe1c08aa39e02a9c7c2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257360"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令列參考

組合並連結一或多個元件語言原始程式檔。 命令列選項會區分大小寫。

如需 ml64 的詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="syntax"></a>語法

> ML \[*選項*] *filename* \[ \[*選項*] *filename*]
>
> ML64 \[*選項*] *filename* \[ \[*選項*] *filename*] ... \[/link *link_options*]

### <a name="parameters"></a>參數

*選項*\
下表列出的選項。

|選項|動作|
|------------|------------|
|**/AT**|啟用小型記憶體模型支援。 針對違反 .com 格式檔案需求的程式碼結構啟用錯誤訊息。 此選項不等於[。模型](dot-model.md)**小型**指示詞。<br /><br /> 無法在 ml64 中使用。|
|**/Bl** *filename*|選取替代連結器。|
|**/c**|僅限組合。 沒有連結。|
|**/coff**|產生物件模組的通用物件檔案格式（COFF）類型。 Win32 元件語言開發所需。<br /><br /> 無法在 ml64 中使用。|
|**/Cp**|保留所有使用者識別碼的大小寫。|
|**/Cu**|將所有識別碼對應至大寫（預設值）。<br /><br /> 無法在 ml64 中使用。|
|**/Cx**|會保留公用和外部符號中的大小寫。|
|**/D** *符號*⟦ =*值*⟧|定義具有指定名稱的文字宏。 如果遺漏*值*，則為空白。 以空格分隔的多個標記必須括在引號中。|
|**/EP**|產生前置處理過的來源清單（傳送至 STDOUT）。 請參閱 **/Sf**。|
|**/ERRORREPORT** [**無** &#124; **提示** &#124;佇列&#124; **傳送**]| 已取代。 錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。 |
|**/F** *hexnum*|將堆疊大小設定為*hexnum*位元組（與 **/link/STACK**：*number*相同）。 值必須以十六進位標記法表示。 **/F**和*hexnum*之間必須有一個空格。|
|**/Fe** *filename*|命名可執行檔。|
|**/Fl**⟦*filename*⟧|產生組合的程式代碼清單。 請參閱 **/Sf**。|
|**/Fm**⟦*filename*⟧|建立連結器對應檔。|
|**/Fo** *filename*|命名物件檔案。 如需詳細資訊，請參閱[備註](#remarks)。|
|**/FPi**|產生浮點算術的模擬器修正（僅限混合語言）。<br /><br /> 無法在 ml64 中使用。|
|**/Fr**⟦*filename*⟧|產生來源瀏覽器 .sbr 檔案。|
|**/Fr**⟦*filename*⟧|產生來源瀏覽器 .sbr 檔案的延伸格式。|
|**/Gc**|指定使用 FORTRAN 或 Pascal 樣式函數呼叫和命名慣例。 與**選項語言相同： PASCAL**。<br /><br /> 無法在 ml64 中使用。|
|**/Gd**|指定 C 樣式函數呼叫和命名慣例的用法。 與**選項語言相同： C**。<br /><br /> 無法在 ml64 中使用。|
|**/GZ**|指定使用 __stdcall 函式呼叫和命名慣例。  與**選項語言相同： STCALL**。<br /><br /> 無法在 ml64 中使用。|
|**/H** *數位*|將外部名稱限制為數字的有效字元。 預設值為31個字元。<br /><br /> 無法在 ml64 中使用。|
|**/help**|呼叫 QuickHelp 以取得 ML 的協助。|
|**/I** *路徑名稱*|設定 include 檔案的路徑。 最多允許10個 **/i**選項。|
|**/nologo**|隱藏成功元件的訊息。|
|**/omf**|產生物件模組檔案格式（OMF）類型的物件模組。  **/omf**意指 **/c**;ML 不支援連結 OMF 物件。<br /><br /> 無法在 ml64 中使用。|
|**/Sa**|開啟所有可用資訊的清單。|
|**/safeseh**|將物件標記為不包含任何例外狀況處理常式，或包含所有以宣告的例外狀況處理常式[。SAFESEH](dot-safeseh.md)。<br /><br /> 無法在 ml64 中使用。|
|**/Sf**|將第一個傳遞清單新增至列出檔案。|
|**/Sl** *寬度*|設定以每行字元數為單位的來源清單行寬。 範圍是60到255或0。 預設值為 0。 與[頁面](page.md)寬度相同。|
|**/Sn**|產生清單時關閉符號表。|
|**/Sp** *長度*|以每頁的行數設定來源清單的分頁長度。 範圍為10到255或0。 預設值為 0。 與[頁面](page.md)長度相同。|
|**/Ss** *文字*|指定來源清單的文字。 與子[標題](subtitle.md)文字相同。|
|**/St** *文字*|指定來源清單的標題。 與[標題](title.md)文字相同。|
|**/Sx**|開啟清單中的 false 條件。|
|**/Ta** *filename*|組合的來源檔案，其名稱結尾不是 .asm 副檔名。|
|**/w**|與 **/W0/WX**相同。|
|**/W** *層級*|設定警告層級，其中*level* = 0、1、2或3。|
|**/WX**|會在產生警告時傳回錯誤碼。|
|**/X**|忽略包含環境路徑。|
|**/Zd**|產生物件檔案中的行號資訊。|
|**/Zf**|使所有符號變成公用。|
|**/Zi**|產生物件檔案中的 CodeView 資訊。|
|**/Zm**|啟用**M510**選項，以取得與 MASM 5.1 的最大相容性。<br /><br /> 無法在 ml64 中使用。|
|**/Zp**⟦*對齊*⟧|在指定的位元組界限上封裝結構。 *對齊*可以是1、2或4。|
|**/Zs**|僅執行語法檢查。|
|**/?**|顯示 ML 命令列語法的摘要。|

*檔案名*\
檔案的名稱。

*link_options*\
連結選項。 如需詳細資訊，請參閱[連結器選項](../../build/reference/linker-options.md)。

## <a name="remarks"></a>備註

ML 和 ML64 的某些命令列選項是位置相關性。 例如，因為 ML 和 ML64 可以接受數個 **/c**選項，所以必須在 **/c**之前指定任何對應的 **/fo**選項。 下列命令列範例說明每個元件檔案規格的物件檔案規格：

```cmd
ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm
```

## <a name="environment-variables"></a>環境變數

|變數|描述|
|--------------|-----------------|
|INCLUDE|指定 include 檔案的搜尋路徑。|
|ML|指定預設的命令列選項。|
|.TMP|指定暫存檔案的路徑。|

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](ml-error-messages.md)\
[Microsoft 巨集組譯工具參考](microsoft-macro-assembler-reference.md)
