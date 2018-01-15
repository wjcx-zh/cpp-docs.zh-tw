---
title: ".Res 檔做為連結器輸入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ac4dedc419c28b4e68d7dcc1772f176738580b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="res-files-as-linker-input"></a>.Res 檔做為連結器輸入
連結程式時，您可以指定一個.res 檔案。 資源編譯器 (RC) 會建立.res 檔。 連結會自動將.res 檔案轉換成 COFF。 CVTRES.exe 工具必須是 LINK.exe 相同目錄中，或在 PATH 環境變數所指定的目錄中。  
  
## <a name="see-also"></a>請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)