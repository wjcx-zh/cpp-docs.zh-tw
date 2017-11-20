---
title: ".Ilk 檔做為連結器輸入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e7d801992beb75ccc14e185fc062dc4c51f8433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ilk-files-as-linker-input"></a>.Ilk 檔做為連結器輸入
當以累加方式連結，連結就會更新它的第一個累加連結期間建立的.ilk 狀態檔。 此檔案具有基底名稱與相同的.exe 或.dll 檔案，而且具有副檔名.ilk。 在後續的累加連結，連結會更新.ilk 檔。 如果.ilk 檔遺漏，連結會執行完整連結，並建立新的.ilk 檔。 如果無法使用的.ilk 檔，連結會執行非累加連結。 如需有關累加連結的詳細資訊，請參閱[累加連結 (/incremental)](../../build/reference/incremental-link-incrementally.md)選項。  
  
## <a name="see-also"></a>另請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)