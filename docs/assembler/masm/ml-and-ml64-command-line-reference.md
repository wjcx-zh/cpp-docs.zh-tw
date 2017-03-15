---
title: "ML and ML64 Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ML"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/W* MASM compiler option"
  - "/c MASM compiler option"
  - "/EP MASM compiler option"
  - "/Fe MASM compiler option"
  - "/Zp MASM compiler option"
  - "/AT MASM compiler option"
  - "/Zm MASM compiler option"
  - "/Sf MASM compiler option"
  - "/Sp MASM compiler option"
  - "/w MASM compiler option"
  - "/Fl MASM compiler option"
  - "/coff MASM compiler option"
  - "/St MASM compiler option"
  - "/Cx MASM compiler option"
  - "/Sl MASM compiler option"
  - "/Cu MASM compiler option"
  - "MASM (Microsoft Macro Assembler), ML command-line reference"
  - "/FPi MASM compiler option"
  - "/Zf MASM compiler option"
  - "ML environment variable"
  - "/Fr MASM compiler option"
  - "/help MASM compiler option"
  - "/Sa MASM compiler option"
  - "/Zd MASM compiler option"
  - "/I MASM compiler option"
  - "/? MASM compiler option"
  - "/Bl MASM compiler option"
  - "/Fm MASM compiler option"
  - "/Fo MASM compiler option"
  - "command-line reference [ML]"
  - "/Sn MASM compiler option"
  - "/Gd MASM compiler option"
  - "/D* MASM compiler option"
  - "environment variables, ML"
  - "/Gc MASM compiler option"
  - "/F* MASM compiler option"
  - "/Sc MASM compiler option"
  - "/H MASM compiler option"
  - "/Zs MASM compiler option"
  - "/omf MASM compiler option"
  - "/Sg MASM compiler option"
  - "/Cp MASM compiler option"
  - "/Zi MASM compiler option"
  - "/nologo MASM compiler option"
  - "/Sx MASM compiler option"
  - "/WX MASM compiler option"
  - "/Ss MASM compiler option"
  - "command line, reference [ML]"
  - "/Ta MASM compiler option"
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# ML and ML64 Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

組件和連結一或多個組件語言原始程式檔。  命令列選項會區分大小寫。  
  
 如需有關 ml64.exe 的詳細資訊，請參閱[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 語法  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### 參數  
 `options`  
 下表列出的選項。  
  
|選項|動作|  
|--------|--------|  
|**\/AT**|啟用小記憶體模型的支援。  啟動違反.com 格式檔案的需求的程式碼建構的錯誤訊息。  請注意這不等於 [。模型](../../assembler/masm/dot-model.md)**TINY**指示詞。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Bl** `filename`|選取替代的連結器。|  
|**\/c**|只會組合。  沒有連結。|  
|**\/coff**|產生通用物件檔案格式 \(COFF\) 類型的物件模組。  通常所需的 Win32 組件語言的開發。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Cp**|會保留所有的使用者識別項的大小寫。|  
|**\/Cu**|將所有的識別項對應至大寫 \(預設值\)。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Cx**|保留大小寫的公用和外部的符號。|  
|**\/D** `symbol`\[\[\=`value`\]\]|定義具有指定名稱的文字巨集。  如果`value`已遺失，它是空白的。  以空格分隔的多個權杖都必須以引號括住。|  
|**\/EP**|會產生前置處理過的來源清單 \(傳送到 STDOUT\)。  請參閱 **\/Sf**。|  
|**\/ERRORREPORT** \[ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND** \]|如果 ml.exe 或 ml64.exe，請在執行階段失敗，您可以使用**\/ERRORREPORT**傳送資訊給 Microsoft，關於這些內部的錯誤。<br /><br /> 如需 **\/ERRORREPORT** 的詳細資訊，請參閱 [\/errorReport \(回報編譯器內部錯誤\)](../../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|**\/F** `hexnum`|設定堆疊大小為`hexnum`個位元組 \(這等同於**\/link\/STACK**：`number`\)。  值必須十六進位標記法來表示。  必須要有之間的空間**\/F**和`hexnum`。|  
|**\/Fe** `filename`|命名的可執行檔。|  
|**\/Fl**\[\[`filename`\]\]|會產生組裝好的程式碼清單。  請參閱 **\/Sf**。|  
|**\/Fm**\[\[`filename`\]\]|建立連結器的對應檔。|  
|**\/Fo** `filename`|目的檔的名稱。  如需詳細資訊請參閱 ＜ 備註 ＞ 一節。|  
|**\/FPi**|會產生模擬器修正增量浮點算術 \(只有混合語言\)。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Fr**\[\[`filename`\]\]|會產生原始程式瀏覽器.sbr 檔。|  
|**\/FR**\[\[`filename`\]\]|會產生原始程式瀏覽器.sbr 檔的延伸的形式。|  
|**\/Gc**|指定樣式 FORTRAN 或依照 pascal 命名法的函式呼叫，並命名慣例的用法。  Same as **OPTION LANGUAGE:PASCAL**.<br /><br /> Ml64.exe 中無法使用。|  
|**\/Gd**|指定 c 樣式函式呼叫，並命名慣例的用法。  Same as **OPTION LANGUAGE:C**.<br /><br /> Ml64.exe 中無法使用。|  
|**\/GZ**|指定使用 \_\_stdcall 函式呼叫，並命名慣例。  Same as **OPTION LANGUAGE:STCALL**.<br /><br /> Ml64.exe 中無法使用。|  
|**\/H** `number`|限制外部名稱，只顯著性數字的字元。  預設值為 31 個字元。<br /><br /> Ml64.exe 中無法使用。|  
|**\/help**|如需毫升會呼叫 QuickHelp。|  
|**\/I** `pathname`|集合包含檔案路徑。  最多 10 個**\/I**允許的選項。|  
|**\/nologo**|不顯示成功的組件的訊息。|  
|**\/omf**|會產生物件模組的檔案格式 \(OMF\) 類型的物件模組。  **\/omf**implies **\/c**; ML.exe 不支援連結 OMF 物件。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Sa**|開啟的所有可用的資訊清單。|  
|**\/safeseh**|標示為包含沒有例外處理常式或含有例外處理常式的宣告與物件 [。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Sf**|加入第一階段清單至清單的檔案。|  
|**\/Sl** `width`|設定線條寬度的來源清單中每一行的字元。  範圍是 60 到 255 之間則為 0。  預設值為 0。  相同的[頁面](../../assembler/masm/page.md)寬度。|  
|**\/Sn**|產生清單時，請關閉符號表。|  
|**\/Sp** `length`|設定每一頁的各行裡列出的來源頁面長度。  範圍是 10 至 255，則為 0。  預設值為 0。  相同的[頁面](../../assembler/masm/page.md)長度。|  
|**\/Ss** `text`|指定文字的來源清單。  相同的[副標題](../../assembler/masm/subtitle.md)的文字。|  
|**\/St** `text`|指定的來源清單的標題。  相同的[標題](../../assembler/masm/title.md)的文字。|  
|**\/Sx**|顯示在清單中的條件式，則為 false。|  
|**\/Ta** `filename`|組件名稱不結束於副檔名為.asm 原始程式檔。|  
|**\/w**|Same as **\/W0\/WX**.|  
|**\/W** `level`|設定警告層級，其中`level` \= 0、 1、 2 或 3。|  
|**\/WX**|如果會產生警告，則傳回錯誤碼。|  
|**\/X**|略過包含環境路徑。|  
|**\/Zd**|產生在目的檔中的行號資訊。|  
|**\/Zf**|所有符號都可公用的。|  
|**\/Zi**|在目的檔中，會產生可檢視程式碼的資訊。|  
|**\/Zm**|可讓**M510**達到最佳相容性 MASM 5.1 的選項。<br /><br /> Ml64.exe 中無法使用。|  
|**\/Zp**\[\[`alignment`\]\]|封裝結構於指定的位元組的界限上。  `alignment`可以是 1、 2 或 4。|  
|**\/Zs**|執行語法檢查。|  
|**\/?**|顯示毫升命令列語法的摘要。|  
  
 `filename`  
 檔案的名稱。  
  
 `linkoptions`  
 \[連結\] 選項。  如需詳細資訊，請參閱 [連結器選項](../../build/reference/linker-options.md)。  
  
## 備註  
 某些命令列的選項，以毫升和 ML64 是敏感的位置。  比方說，因為毫升和 ML64 可以接受多個**\/c**項目、 任何對應**\/Fo**之前，必須指定選項**\/c**。  下列的命令列範例會說明每個組件檔案規格的物件指定檔案：  
  
 **ml.exe \/Fo a1.obj \/c a.asm \/Fo b1.obj \/c b.asm**  
  
## 環境變數  
  
|變數|描述|  
|--------|--------|  
|包含|指定包含檔案的搜尋路徑。|  
|毫升|指定預設的命令列選項。|  
|TMP|指定存放暫存檔的路徑。|  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)   
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)