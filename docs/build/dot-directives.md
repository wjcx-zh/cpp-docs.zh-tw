---
title: "點指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 中的點指示詞"
  - "NMAKE 程式, 點指示詞"
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 點指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在描述區塊之外、且必須在行首指定點指示詞。  點指示詞開頭為句號  \(.\)，後面跟隨著冒號 \(:\)。  可以使用空格和定位字元。  點指示詞名稱會區分大小寫，而且需使用大寫。  
  
|指示詞|用途|  
|---------|--------|  
|**.IGNORE :**|忽略命令從指定給 Makefile 結尾的位置所傳回的非零的結束代碼 \(Exit Code\)。  根據預設，如果命令傳回非零的結束代碼，NMAKE 將會暫止。  若要還原錯誤檢查，請使用 **\!CMDSWITCHES**。  若要忽略單一命令的結束代碼，請使用破折號 \(–\) 修飾詞 \(Modifier\)。  若要忽略整個檔案的結束代碼，請使用 \/I。|  
|**.PRECIOUS :** *targets*|如果暫止了更新 *targets* 的命令，會把它們保留在磁碟上；如果命令是透過刪除檔案來處理中斷，則會沒有作用。  使用一或多個空格或是定位字元分隔目標名稱。  根據預設，如果 CTRL\+C 或 CTRL\+BREAK 中斷了組建，NMAKE 會刪除目標。  每次使用 **.PRECIOUS** 都會套用至整個 Makefile，如果使用多個規格，其作用也會相對增加。|  
|**.SILENT :**|從指定給 Makefile 結尾的位置上隱藏顯示執行的命令。  根據預設，NMAKE 會顯示所叫用 \(Invoke\) 的命令。  若要還原 echo，請使用 **\!CMDSWITCHES**。  若要隱藏單一命令的 echo，請使用 **@** 修飾詞。  若要隱藏整個檔案的 echo，請使用 \/S。|  
|**.SUFFIXES :** `list`|列出推斷規則相符的副檔名，預先定義為包含下列副檔名：.exe .obj .asm .c .cpp .cxx .bas .cbl .for .pas .res .rc .f .f90|  
  
 若要變更 **.SUFFIXES** 清單順序或指定新清單，請清除清單並指定新設定。  若要清除清單，在冒號後請不要指定副檔名：  
  
```  
.SUFFIXES :  
```  
  
 若要加入其他後置字元至清單結尾，請指定  
  
```  
.SUFFIXES : suffixlist  
```  
  
 在此處的 *suffixlist* 是其他後置字元的清單，由一或多個空格或定位字元分隔。  若要查看 **.SUFFIXES** 的目前設定，請以 \/P 執行 NMAKE。  
  
## 請參閱  
 [NMAKE 參考](../build/nmake-reference.md)