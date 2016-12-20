---
title: "連結器命令列語法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LINK 工具 [C++], 命令列語法"
  - "連結器 [C++], 語法"
  - "連結器命令列 [C++]"
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器命令列語法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要執行 LINK.EXE，請使用下列命令語法：  
  
```  
LINK arguments  
```  
  
 `arguments` 包括選項和檔名，而且可以任何順序指定。  選項會首先被處理，然後才是檔案。  請使用一個以上的空格或 Tab 字元來分隔引數。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動這個工具。  您不能從系統命令提示字元或從檔案總管來啟動它。  
  
 在命令列上，選項是由選項規範 \(短橫線 \(–\) 或正斜線 \(\/\)\) 後接選項名稱所構成。  選項名稱不可縮寫。  某些選項可接受於冒號 \(:\) 之後指定的引數。  除了在 \/COMMENT 選項中以引號括起來的字串之外，選項規格內均不允許有空格或 Tab 字元。  請以十進位數或 C 語言標記法指定數字引數。  選項名稱及其關鍵字或檔名引數並不區分大小寫，但是做為引數的識別項則必須區分大小寫。  
  
 若要將檔案傳遞給連結器，請在命令列上的 LINK 命令之後指定檔名。  您可以在檔名指定絕對或相對路徑，您也可以在檔名中使用萬用字元。  如果您省略句號 \(.\) 和副檔名，LINK 會假設要尋找 .obj 檔案。  LINK 不使用副檔名或在缺少副檔名的情況下對檔案內容進行假設；它是藉由檢查檔案來判斷檔案的類型，並且進行相對的處理。  
  
 link.exe 傳回零代表成功 \(沒有錯誤\)。否則，連結器會傳回停止連結的錯誤編號。例如，如果連結器產生 LNK1104，連結器會傳回 1104。因此，在由連結器所傳回錯誤的最低錯誤編號是 1000。傳回值 128 代表作業系統或組態檔的組態問題；載入器也未載入 link.exe 或 c2.dll。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)