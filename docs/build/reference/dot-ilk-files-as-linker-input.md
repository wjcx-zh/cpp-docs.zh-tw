---
title: ".Ilk 檔做為連結器輸入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b91d229e1c607be1ed35685ab7bfdffe2271e16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ilk-files-as-linker-input"></a>.Ilk 檔做為連結器輸入
當以累加方式連結，連結就會更新它的第一個累加連結期間建立的.ilk 狀態檔。 此檔案具有基底名稱與相同的.exe 或.dll 檔案，而且具有副檔名.ilk。 在後續的累加連結，連結會更新.ilk 檔。 如果.ilk 檔遺漏，連結會執行完整連結，並建立新的.ilk 檔。 如果無法使用的.ilk 檔，連結會執行非累加連結。 如需有關累加連結的詳細資訊，請參閱[累加連結 (/incremental)](../../build/reference/incremental-link-incrementally.md)選項。  
  
## <a name="see-also"></a>請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)