---
title: "NMAKE 的結束代碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb5548d74544ba4277fa1d901ffa9f0b91b83f2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="exit-codes-from-nmake"></a>NMAKE 的結束代碼
NMAKE 會傳回下列結束代碼：  
  
|程式碼|意義|  
|----------|-------------|  
|0|沒有任何錯誤 （可能有警告）|  
|1|（只有在使用 /K 時才會發出） 的組建不完整|  
|2|程式錯誤，可能是因為下列其中之一：|  
||-Makefile 中的 a 語法錯誤|  
||的來自命令錯誤或結束代碼|  
||-使用者中斷|  
|4|系統錯誤： 記憶體不足|  
|255|目標不是最新的 （只有在使用 /Q 時才會發出）|  
  
## <a name="see-also"></a>另請參閱  
 [執行 NMAKE](../build/running-nmake.md)