---
title: 點指示詞 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29eeedbdc2eaccb753751082a38736fa239837b2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dot-directives"></a>點指示詞
指定外部描述區塊，在一行的開始點指示詞。 點指示詞以句點為開頭 (。 )，後面接著冒號 （:）。 允許空格和定位點。 點指示詞名稱會區分大小寫，且必須為大寫。  
  
|指示詞|用途|  
|---------------|-------------|  
|**.忽略：**|會忽略命令，其指定為 makefile 的結尾處傳回零的結束代碼。 根據預設，如果命令傳回非零結束代碼，暫止 NMAKE。 若要還原錯誤檢查，請使用**！CMDSWITCHES**。 若要忽略單一命令的結束代碼，請使用破折號 （-） 修飾詞。 若要略過整個檔案的結束代碼，請使用 / 我。|  
|**.珍貴：** *目標*|會保留*目標*磁碟上如果更新這些指令會暫止的; 如果有任何作用命令會刪除該檔案來處理中斷。 與一個或多個空格或定位字元分隔目標名稱。 根據預設，NMAKE 會刪除目標，如果組建因 CTRL + C 或 CTRL + BREAK。 每次使用**。珍貴**整個 makefile; 適用於多個規格會累計。|  
|**.無訊息：**|隱藏的執行命令，從指定的 makefile 結尾的位置。 根據預設，NMAKE 就會顯示它會叫用的命令。 若要還原回應，請使用**！CMDSWITCHES**。 若要隱藏單一命令的回應，使用**@** 修飾詞。 若要隱藏整個檔案的回應，請使用/s。|  
|**.尾碼：** `list`|列出擴充功能的推斷規則比對。預先定義包含下列副檔名：.exe.obj.asm.c.cpp.cxx.bas.cbl。 如.pas.res.rc.f.f90|  
  
 若要變更**。尾碼**清單順序，或若要指定新的清單，請清除清單並指定新的設定。 若要清除清單，指定冒號後面的任何擴充功能：  
  
```  
.SUFFIXES :  
```  
  
 若要將其他尾碼新增到清單的結尾，指定  
  
```  
.SUFFIXES : suffixlist  
```  
  
 其中*suffixlist*是其他尾碼，以一個或多個空格或定位字元分隔的清單。 若要查看目前的設定**。尾碼**，使用 /P.執行 NMAKE  
  
## <a name="see-also"></a>另請參閱  
 [NMAKE 參考](../build/nmake-reference.md)