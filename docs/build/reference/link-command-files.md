---
title: "LINK 命令檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e585fb8fa11d4e3ffe8eff842baacb05f109754c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="link-command-files"></a>LINK 命令檔
您可以連結的命令檔的形式傳遞命令列引數。 若要指定至連結器的命令檔，請使用下列語法：  
  
```  
LINK @commandfile  
```  
  
 `commandfile`是文字檔案的名稱。 沒有空格或定位點之間允許 at 符號 (@) 和檔案名稱。 沒有任何預設擴充功能。您必須指定完整的檔名，包括任何副檔名。 無法使用萬用字元。 您可以指定為絕對或相對路徑與檔名。 連結不會使用環境變數來搜尋檔案。  
  
 在命令檔中，引數可分隔空格或定位字元 （因為在命令列） 並以新行字元。  
  
 您可以指定全部或部分的命令列命令檔中。 您可以使用 LINK 命令中的多個命令檔。 連結會接受命令檔輸入，如同它已指定命令列上的位置。 不可為巢狀命令檔。 連結回應命令檔案的內容，除非[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)指定選項。  
  
## <a name="example"></a>範例  
 下列命令以建置 DLL 會傳遞物件的檔案和程式庫的名稱不同的命令檔中，並會使用第三個命令的 /EXPORTS 選項規格的檔案：  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)