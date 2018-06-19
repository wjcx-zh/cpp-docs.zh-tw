---
title: 模組定義陳述式的規則 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- .def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f8de42480dae9be203a132561d722c18d6952c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376386"
---
# <a name="rules-for-module-definition-statements"></a>模組定義陳述式的規則
下列語法規則套用至.def 檔案中的所有陳述式。 每個陳述式的說明特定陳述式適用於其他規則。  
  
-   陳述式、 屬性關鍵字和使用者指定的識別碼會區分大小寫。  
  
-   長時間的檔案名稱包含空格或分號 （;） 必須括在雙引號 （"）。  
  
-   使用一或多個空格、 tab 字元或換行字元分隔的引數的陳述式關鍵字以及分隔各陳述式。 冒號 （:） 或指定引數的等號 （=） 會圍繞著零或多個空格、 定位字元或新行字元。  
  
-   A**名稱**或**文件庫**陳述式中，如果使用，必須在前面的所有其他陳述式。  
  
-   **區段**和**匯出**陳述式可以在.def 檔中出現一次以上。 每個陳述式可能需要多個規格，必須以一個或多個空格、 tab 字元或新行字元分隔。 陳述式關鍵字必須出現在第一次的規格之前，一次，而且可以重複在每個其他規格之前。  
  
-   許多陳述式有相同的連結命令列選項。 請參閱對應的 LINK 選項，如需詳細資訊的描述。  
  
-   .Def 檔案中的註解的分號 （;） 來指定每個註解行的開頭。 註解不能共用同一線路與陳述式，但它可以出現在多行陳述式中的規格之間。 (**區段**和**匯出**多行陳述式。)  
  
-   數值引數是指定基底 10 或十六進位。  
  
-   如果字串引數符合[保留字](../../build/reference/reserved-words.md)，就必須括在雙引號 （"）。  
  
## <a name="see-also"></a>另請參閱  
 [模組定義檔 (.Def)](../../build/reference/module-definition-dot-def-files.md)  