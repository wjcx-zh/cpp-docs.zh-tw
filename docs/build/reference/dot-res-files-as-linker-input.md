---
title: .Res 檔做為連結器輸入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71344bb752ff7a328ddd5f718a5de1c1f42b65be
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370663"
---
# <a name="res-files-as-linker-input"></a>.Res 檔做為連結器輸入
連結程式時，您可以指定一個.res 檔案。 資源編譯器 (RC) 會建立.res 檔。 連結會自動將.res 檔案轉換成 COFF。 CVTRES.exe 工具必須是 LINK.exe 相同目錄中，或在 PATH 環境變數所指定的目錄中。  
  
## <a name="see-also"></a>另請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)