---
title: "LINK 命令檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令檔 [C++]"
  - "命令檔 [C++], LINK"
  - "LINK 工具 [C++]"
  - "LINK 工具 [C++], 命令列語法"
  - "語法, LINK 命令檔"
  - "文字檔, 將引數傳遞至 LINK"
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# LINK 命令檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以將命令列引數以命令檔的形式傳遞給 LINK。  若要將命令檔指定給連結器，請使用下列語法：  
  
```  
LINK @commandfile  
```  
  
 `commandfile` 是文字檔的名稱。  在 @ 符號和檔案名稱之間不允許有空格或 Tab 字元。  沒有預設的副檔名；您必須指定完整的檔案名稱，包含副檔名。  這裡不能使用萬用字元。  您可以指定檔名的絕對或相對路徑。  LINK 不使用環境變數來搜尋檔案。  
  
 在命令檔中，引數可以用空格或 Tab 字元 \(像在命令列上一樣\) 以及新行 \(Newline\) 字元來分隔。  
  
 您可以在命令檔中指定全部或部分的命令列輸入。  您也可以在 LINK 命令中使用一個以上的命令檔。  LINK 會將命令檔輸入視同在命令列上同一位置所指定的命令一樣地接受它。  命令檔不能被巢狀 \(Nest\) 指定。  除非指定了 [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md) 選項，否則 LINK 會回應 \(Echo\) 命令檔的內容。  
  
## 範例  
 下列建置 DLL 的命令會在不同的命令檔中傳遞目的檔 \(Object File\) 和程式庫，並且使用第三個命令檔來記載 \/EXPORTS 選項：  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)