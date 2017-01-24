---
title: "執行 LIB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.TargetMachine"
  - "Lib"
  - "VC.Project.VCLibrarianTool.PrintProgress"
  - "VC.Project.VCLibrarianTool.SuppressStartupBanner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ 命令檔"
  - "/MACHINE 目標平台選項"
  - "/NOLOGO 程式庫管理員選項"
  - "/VERBOSE 程式庫管理員選項"
  - "分號命令檔"
  - "命令檔"
  - "命令檔, LIB"
  - "破折號選項規範"
  - "斜線選項規範"
  - "LIB [C++], 執行 LIB"
  - "MACHINE 目標平台選項"
  - "-MACHINE 目標平台選項"
  - "NOLOGO 程式庫管理員選項"
  - "-NOLOGO 程式庫管理員選項"
  - "冒號, 命令檔"
  - "正斜線 (/)"
  - "VERBOSE 程式庫管理員選項"
  - "-VERBOSE 程式庫管理員選項"
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 執行 LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用各種命令列選項來控制 LIB。  
  
## LIB 命令列  
 若要執行 LIB，請輸入 `lib` 命令，並在命令後接上您正使用 LIB 執行之工作的選項和檔名。  LIB 也接受命令檔 \(Command File\) 中的命令列輸入，在下面的章節中將會敘述。  LIB 不使用環境變數。  
  
> [!NOTE]
>  如果您習慣使用 Windows NT 的 Microsoft Win32 軟體開發套件 \(Software Development Kit，SDK\) 所提供的 LINK32.exe 和 LIB32.exe 工具，您可能已經使用了 `link32 -lib` 命令或是 `lib32` 命令來管理程式庫並建立匯入程式庫。  請務必要變更您的 Makefile 和批次 \(Batch\) 檔，以便改用 `lib` 命令。  
  
## LIB 命令檔  
 您可以使用下列語法將命令檔中的命令列引數傳遞到 LIB：  
  
```  
LIB @commandfile  
```  
  
 `commandfile` 檔案是文字檔。  在 @ 符號和檔案名稱之間不允許有空格或 Tab 字元。  並沒有預設的副檔名；您必須指定完整的檔案名稱，包含副檔名在內。  這裡不能使用萬用字元。  您可以和檔名一起指定絕對或相對路徑。  
  
 在命令檔中，引數可以用空格或 Tab 字元分隔，如同在命令列一樣；它們也可以用新行字元 \(Newline Character\) 分隔。  使用分號 \(;\) 來標記註解。  LIB 會忽略所有從分號開始到該行結束的的文字。  
  
 您可以在命令檔指定全部或部分的命令列，您也可以在 LIB 命令使用一個以上的命令檔。  LIB 接受命令檔輸入，就如同在命令列的那個位置上指定一樣。  命令檔不能被巢狀 \(Nest\) 指定。  除非使用 \/NOLOGO 選項，否則 LIB 會回應命令檔的內容。  
  
## 使用 LIB 選項  
 選項是由虛線 \( – \) 或斜線 \(\/\) 選項規範，後接選項名稱所組成。  選項名稱不可縮寫。  某些選項可接受於冒號 \(:\) 之後指定的引數。  在選項規格內不可有空格或 Tab 字元。  請使用一個或多個空格或 Tab 字元來分隔命令列上的選項規格。  選項名稱及其關鍵字或檔名引數並沒有大小寫之分別，但是做為引數的識別項是區分大小寫的。  LIB 會根據在命令列和命令檔中指定的順序處理選項。  如果選項以不同的引數重複指定，最後一個指定的會優先處理。  
  
 下列選項可套用至所有的 LIB 模式：  
  
 \/ERRORREPORT \[NONE &#124; PROMPT &#124; QUEUE &#124; SEND\]  
 如果 lib.exe 在執行階段失敗，您可以使用 \/ERRORREPORT 將這些內部錯誤的相關資訊傳送到 Microsoft。  
  
 如需 \/ERRORREPORT 的詳細資訊，請參閱 [\/errorReport \(回報編譯器內部錯誤\)](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 \/LTCG  
 會使得程式庫在使用連結時產生程式碼下建置。如需詳細資訊，請參閱 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 \/MACHINE  
 指定程式的目標平台。  通常，您不需指定 \/MACHINE。  LIB 從 .obj 檔案推斷電腦類型。  然而，在某些情形下，LIB 無法判斷電腦類型而發出錯誤訊息。  如果發生這樣的錯誤訊息，請指定 \/MACHINE。  但在 \/EXTRACT 模式，這個選項只是用來驗證而已。  請在命令列使用 `lib /?` ，查看可使用的電腦類型。  
  
 \/NOLOGO  
 隱藏 LIB 著作權訊息和版本號碼的顯示，並防止命令檔的回應。  
  
 \/VERBOSE  
 顯示有關工作階段進度的詳細資訊，其中包括正在加入的 .obj 檔名稱。  這些資訊會送至標準輸出，也可以重新導向至檔案中。  
  
 \/WX\[:NO\]  
 將警告視為錯誤。  如需詳細資訊，請參閱[\/WX \(將連結器警告視為錯誤\)](../../build/reference/wx-treat-linker-warnings-as-errors.md)。  
  
 其他的選項只能套用到指定的 LIB 模式。  這些選項將會在描述每個模式的章節中討論。  
  
## 請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)