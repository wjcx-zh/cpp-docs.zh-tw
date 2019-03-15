---
title: 點指示詞
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 2c21e8a18c76331f86a4e8966b4f67c9c9bc9b7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824991"
---
# <a name="dot-directives"></a>點指示詞

指定描述區塊，在一行的開頭之外的點指示詞。 點指示詞以句號作為開頭 (。 )，後面接著冒號 （:）。 允許空格和定位點。 點指示詞名稱會區分大小寫，且必須為大寫。

|指示詞|用途|
|---------------|-------------|
|**.忽略：**|會忽略命令，從指定的 makefile 結尾處傳回非零的結束代碼。 根據預設，如果命令傳回非零結束代碼，暫止 NMAKE。 若要還原錯誤檢查，請使用 **！CMDSWITCHES**。 若要忽略單一命令的結束代碼，請使用破折號 （-） 修飾詞。 若要忽略整個檔案的結束代碼，請使用 / 我。|
|**.珍貴：** *目標*|會保留*目標*磁碟上如果更新這些指令會暫止; 如果有任何作用命令會藉由刪除檔案來處理中斷。 使用一或多個空格或定位點分隔目標名稱。 根據預設，NMAKE 會刪除目標，如果組建中斷的 CTRL + C 或 CTRL + BREAK。 每次使用 **。寶貴**整個的 makefile; 適用於多個規格會累計。|
|**.無訊息：**|隱藏顯示執行的命令，從指定的 makefile 結尾的位置。 根據預設，NMAKE 就會顯示它會叫用的命令。 若要還原回應，請使用 **！CMDSWITCHES**。 若要隱藏單一命令的回應，使用**@** 修飾詞。 若要隱藏整個檔案的回應，請使用/s。|
|**.後置詞：** `list`|列出適用於推斷規則的比對，擴充功能預先定義包含下列副檔名：.exe.obj.asm.c.cpp.cxx.bas.cbl。 如需.pas.res.rc 1).f.f90|

若要變更 **。後置詞**清單順序，或若要指定新的清單，請清除清單，並指定新的設定。 若要清除清單，指定冒號之後的任何延伸模組：

```
.SUFFIXES :
```

若要將其他尾碼加入清單的結尾，請指定

```
.SUFFIXES : suffixlist
```

何處*suffixlist*是其他的後置字元，以一或多個空格或定位點分隔的清單。 若要查看目前的設定 **。後置詞**，使用 /P.執行 NMAKE

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
