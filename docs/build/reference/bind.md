---
title: -BIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372427"
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>備註  
 這個選項會設定為可執行檔或 DLL 的匯入位址資料表中的進入點的位址。 使用此選項，以降低載入程式的時間。  
  
 指定程式的可執行檔和 Dll 中的*檔案*EDITBIN 命令列上的引數。 選擇性*路徑*/BIND 引數指定的位置指定的檔案所使用的 dll。 請以分號隔開多個目錄 (**;**)。 如果*路徑*未指定，EDITBIN 搜尋 PATH 環境變數中指定的目錄。 如果*路徑*會指定 EDITBIN 忽略 PATH 變數。  
  
 根據預設，程式載入器載入程式時設定的進入點的位址。 此程序所花費的時間會有所差異，取決於 Dll 的數字和程式中參考的進入點的數目。 如果程式已修改其中 /BIND，且基底位址的可執行檔和 Dll 不會衝突已經載入的 Dll，如果作業系統不需要設定這些位址。 不正確地以檔案的情況下，作業系統重新放置到程式的 Dll，並重新計算的進入點位址，以將新增到程式的載入時間。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)