---
title: "輸入和輸出 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5c4705ae56f11c1299e512814f8d83a49690a6ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="input-and-output"></a>輸入和輸出
I/O 函式會針對檔案和裝置進行讀取和寫入。 檔案 I/O 作業會以文字模式或二進位模式進行。 Microsoft 執行階段程式庫有三種 I/O 函式：  
  
-   [資料流 I/O](../c-runtime-library/stream-i-o.md) 函式會將資料視為個別字元的資料流。  
  
-   [低層級 I/O](../c-runtime-library/low-level-i-o.md) 函式會針對比資料流 I/O 所提供還要更低層級的作業，直接叫用作業系統。  
  
-   [主控台和連接埠 I/O](../c-runtime-library/console-and-port-i-o.md) 函式會直接讀取或寫入至主控台 (鍵盤和螢幕) 或 I/O 連接埠 (例如印表機連接埠)。  
  
    > [!NOTE]
    >  由於資料流函式會進行緩衝處理，而低層級函式不會，因此這兩種類型的函式通常不會相容。 處理特定檔案時，請不要同時使用資料流和低層級函式。  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)