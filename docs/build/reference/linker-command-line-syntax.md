---
title: 連結器命令列語法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab367a7bcb03030f807c8f24ecab088308036bd
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571391"
---
# <a name="linker-command-line-syntax"></a>連結器命令列語法
若要執行連結。EXE，使用下列命令語法：  
  
```  
LINK arguments  
```  
  
 `arguments`包含選項和檔名，而且可以依任何順序指定。 選項為已處理的第一個，則檔案。 使用一或多個空格或定位點分隔的引數。  
  
> [!NOTE]
>  您可以啟動此工具只能從 Visual Studio 命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。  
  
 命令列選項選項規範組成，破折號 （-） 或斜線 （/），後面接著選項的名稱。 選項名稱不能被縮寫。 有些選項需要引數，指定在冒號 （:） 之後。 沒有空格或定位字元內允許的選項規格中，除了 /COMMENT 選項中加上引號的字串內。 以十進位數或 C 語言標記法指定數字的引數。 選項名稱和其關鍵字或檔名引數不區分大小寫，但做為引數的識別碼會區分大小寫。  
  
 若要傳送檔案至連結器，請在命令列上指定檔案名稱之後連結 命令。 您可以指定絕對或相對路徑與檔名，以及您可以使用萬用字元在檔名。 如果您省略的點 （.） 和檔案名稱副檔名，連結會假設為了尋找檔案的.obj。 連結不會使用副檔名或缺乏將內容假設檔案，它會藉由檢查，判斷檔案類型，並加以處理。  
  
 link.exe 會傳回成功 （沒有錯誤） 的零。  否則，連結器會傳回停止連結的錯誤號碼。  例如，如果連結器產生 LNK1104，連結器就會傳回 1104年。  因此，連結器發生錯誤時傳回的最低錯誤編號為 1000年。  傳回值 128 代表作業系統或.config 檔案; 的組態問題載入器未載入 link.exe 或 c2.dll。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)