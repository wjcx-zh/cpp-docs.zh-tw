---
title: "連結器命令列語法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ce42aa031b91d5a4ec21ed14ac7cb47643e1325
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-command-line-syntax"></a>連結器命令列語法
若要執行連結。EXE，使用下列命令語法：  
  
```  
LINK arguments  
```  
  
 `arguments`包括選項和檔名，以及可以任何順序指定。 選項為已處理的第一個，然後才是檔案。 使用一個或多個空格或定位字元分隔引數。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。  
  
 命令列選項選項規範組成，破折號 （-） 或斜線 （/），後面接著選項的名稱。 選項名稱不能為縮寫。 某些選項可接受於冒號 （:） 之後指定為引數。 沒有空格或定位點內的選項規格，除了允許 /COMMENT 選項中有引號的字串內。 指定以十進位數或 C 語言標記法的數值引數。 選項名稱及其關鍵字或檔名引數並不區分大小寫，但做為引數的識別碼會區分大小寫。  
  
 連結命令之後將檔案傳遞至連結器，請在命令列上指定檔名。 您可以指定為絕對或相對路徑與檔名，以及您可以使用萬用字元在檔名。 如果您省略的點 （.） 和檔案名稱副檔名，連結會假設.obj 為了尋找檔案。 連結未使用的副檔名或缺乏猜測內容的檔案。它會檢查它，來判斷檔案類型，並加以處理。  
  
 link.exe 會傳回成功 （沒有錯誤） 的零。  否則，連結器會傳回停止連結的錯誤號碼。  例如，如果連結器產生 LNK1104，連結器會傳回 1104年。  因此，連結器發生錯誤時傳回的錯誤編號最小為 1000年。  傳回值為 128 代表作業系統或.config 檔案中，有設定問題載入器未載入 link.exe 或 c2.dll。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)