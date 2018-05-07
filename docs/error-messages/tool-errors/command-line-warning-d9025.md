---
title: 命令列警告 D9025 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9025
dev_langs:
- C++
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3875a2cbd065fd5ad887267bcc80748fa9845d0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9025"></a>命令列警告 D9025
覆寫 '1' 與選項 '2'  
  
 *選項 1*選項已指定，但是再由覆寫*選項 2*。 *選項 2*選項使用。  
  
 如果兩個選項指定了相衝突，或不相容的指示詞，則會使用指定或隱含的最遠到右邊的選項，在命令列上的指示詞。  
  
 如果您從開發環境中，在編譯時，收到這個警告，並不確定的選項衝突所在，請考慮下列各項：  
  
-   在程式碼或專案的專案設定中，可以指定選項。 如果您看一下編譯器[命令列屬性頁](../../ide/command-line-property-pages.md)，如果您看到中的選項衝突**所有選項**欄位則選項會設定專案屬性頁面中，否則選項在原始程式碼中設定。  
  
     如果選項已設定專案屬性頁中，尋找編譯器的前置處理器 屬性頁上 （在 方案總管 中選取專案節點）。  如果您不會看到那里設定，請檢查並確定每個原始程式碼檔 （在 方案總管) 的前置處理器 屬性頁面設定的選項並未新增那里。  
  
     如果程式碼中設定的選項可以設定程式碼或 windows 標頭。  您可能會嘗試建立前置處理過的檔案 ([/P](../../build/reference/p-preprocess-to-a-file.md))，並搜尋符號。