---
title: 連結器工具錯誤 LNK1181 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 617678e5453acdafaf72875857b0e0f9b84a110a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1181"></a>連結器工具錯誤 LNK1181
無法開啟輸入的檔案 'filename'  
  
 連結器找不到`filename`因為它不存在或找不到路徑。  
  
 錯誤 LNK1181 包含部分常見的原因：  
  
-   `filename` 正因為連結器列，但該檔案上的其他相依性不存在。  
  
-   A **/LIBPATH**陳述式所指定目錄含有`filename`遺失。  
  
 若要解決上述問題，請參考連結器列上的任何檔案都存在於系統上。  此外也請確認沒有 **/LIBPATH**陳述式，針對每個含有連結器相依檔案的目錄。  
  
 Lnk1181 另一個可能的原因是有內嵌空格長檔名不以引號括住。  在此情況下，連結器將只能辨識檔案名稱最多的第一個空間，並再假設副檔名為。 obj這種情況的解決方案是來括住的長檔名 （路徑加上檔案名稱） 以引號。  
  
 如需詳細資訊，請參閱[.lib 檔做為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
## <a name="see-also"></a>另請參閱  
 [/LIBPATH (其他 Libpath)](../../build/reference/libpath-additional-libpath.md)