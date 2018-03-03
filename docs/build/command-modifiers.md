---
title: "命令修飾詞 |Microsoft 文件"
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
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 610725bf52522cd5041d2f6dcadb422bf942458a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-modifiers"></a>命令修飾詞
您可以指定一或多個命令修飾詞，上述命令，您可以選擇以空格或定位字元分隔。 如同命令修飾詞必須縮排。  
  
|修飾詞|用途|  
|--------------|-------------|  
|@*命令*|可防止命令的顯示。 不會隱藏顯示的命令。 根據預設，NMAKE 回應所有執行的命令。 使用 /S 隱藏顯示整個 makefile 中;使用**。無訊息**隱藏顯示 makefile 的一部分。|  
|**-**[`number` ]*命令*|關閉的錯誤檢查*命令*。 根據預設，NMAKE 中止時命令傳回非零結束代碼。 如果-`number`是使用，NMAKE 就會停止如果結束代碼超過`number`。 空格或定位點不能出現之間繪製虛線和*數目。* 至少一個空格或定位點之間必須有`number`和*命令*。 若要關閉的錯誤檢查整個 makefile; 使用 /I使用**。忽略**若要關閉的錯誤檢查 makefile 的一部分。|  
|**!** *command*|執行*命令*每個相依檔案如果*命令*使用 **$ \* \***  （在相依性的所有相依檔案） 或**$?** （中的所有相依檔案時間戳記晚於目標的相依性）。|  
  
## <a name="see-also"></a>請參閱  
 [Makefile 中的命令](../build/commands-in-a-makefile.md)