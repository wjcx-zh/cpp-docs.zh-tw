---
title: "Makefile 前置處理器指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
dev_langs: C++
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 742faea629cb085c203e231c29ab9e512b9c2812
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="makefile-preprocessing-directives"></a>Makefile 前置處理指示詞
前置處理器指示詞不區分大小寫。 初始驚嘆號 （！） 必須出現在一行的開頭。 零或多個空格或定位字元可以驚嘆號的縮排的後面出現。  
  
 **!CMDSWITCHES**  
 {**+**&#124; **-** }*選項*...開啟每個*選項*列出開啟或關閉。 空格或定位字元必須出現在之前 + 或-運算子;沒有任何可以出現在運算子之間和[選項字母](../build/nmake-options.md)。 字母不區分大小寫，且已指定但不是斜線 （/）。 若要開啟某些選項並關閉其他，使用不同的**！CMDSWITCHES**。  
  
 只有 /D / 用於我、 /N 和 /S makefile。 除非 /F、 /HELP、 /NOLOGO，允許 Tools.ini，所有的選項/X，，/？。 描述區塊中指定的變更進行下一個描述區塊才生效。 這個指示詞更新**MAKEFLAGS**; 如果在遞迴時繼承變更**MAKEFLAGS**指定。  
  
 **!錯誤***文字*   
 顯示*文字*錯誤 U1050，則會中止 NMAKE，即使在 /K，/ I、 **。忽略**， **！CMDSWITCHES**，或使用破折號 （-） 命令修飾詞。 空格或定位點之前*文字*都會被忽略。  
  
 **!訊息***文字*   
 顯示*文字*至標準輸出。 空格或定位點之前*文字*都會被忽略。  
  
 **!包含**[  **\<** ] *filename*[  **>** ]  
 讀取*filename*為 makefile，再繼續執行目前的 makefile。 搜尋 NMAKE *filename*第一次在指定或目前目錄中，然後以遞迴方式透過目錄的任何父系 makefile，然後，如果*filename*括在角括弧 (\<>)，在所指定的目錄中**INCLUDE**巨集，一開始設定為 INCLUDE 環境變數。 可用來傳遞**。尾碼**設定**。珍貴**，和推斷規則，以便遞迴 makefile。  
  
 **!如果**  `constantexpression`  
 處理陳述式之間**！如果**下, 一個**！其他**或`!ENDIF`如果`constantexpression`評估為非零值。  
  
 **!IFDEF***巨集名稱*   
 處理陳述式之間`!IFDEF`下, 一個**！其他**或`!ENDIF`如果*巨集名稱*定義。 Null 巨集視為定義。  
  
 **!IFNDEF***巨集名稱*   
 處理陳述式之間**！IFNDEF**下, 一個**！其他**或`!ENDIF`如果*巨集名稱*未定義。  
  
 **!其他**[**如果** *constantexpression* &#124;**IFDEF** *巨集名稱*&#124;**IFNDEF** *巨集名稱*]  
 處理陳述式之間**！其他**下, 一個`!ENDIF`如果之前**！如果**， `!IFDEF`，或**！IFNDEF**陳述式評估為零。 選擇性的關鍵字進一步控制前置處理。  
  
 **!ELSEIF**  
 同義字**！ELSE IF**。  
  
 **!ELSEIFDEF**  
 同義字**！其他 IFDEF**。  
  
 **!ELSEIFNDEF**  
 同義字**！其他 IFNDEF**。  
  
 `!ENDIF`  
 結束標記**！如果**， `!IFDEF`，或**！IFNDEF**區塊。 之後的任何文字`!ENDIF`同一行上會被忽略。  
  
 **!UNDEF***巨集名稱*   
 取消定義*巨集名稱*。  
  
## <a name="see-also"></a>另請參閱  
 [Makefile 前置處理](../build/makefile-preprocessing.md)