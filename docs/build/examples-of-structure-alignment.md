---
title: "結構對齊範例 | Microsoft Docs"
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
  - "範例 [C++], 結構對齊"
  - "結構對齊"
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 結構對齊範例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列四個範例都會個別宣告對齊的結構或等位，對應的圖表則會說明該結構或等位在記憶體中的配置。  圖表中的每欄都表示一個位元組的記憶體，欄中的數字則表示該位元組的位移。  每個圖表第二列中的名稱，都對應於宣告中的變數名稱。  有陰影的欄位則表示需要填補才能達成指定的對齊。  
  
 ![AMD 轉換範例](../build/media/vcamd_conv_ex_1.png "vcAmd\_conv\_ex\_1")  
範例 1  
  
 ![AMD 轉換範例](../build/media/vcamd_conv_ex_2.png "vcAmd\_conv\_ex\_2")  
範例 2  
  
 ![AMD 轉換範例](../build/media/vcamd_conv_ex_3.png "vcAmd\_conv\_ex\_3")  
範例 3  
  
 ![AMD 轉換範例](../build/media/vcamd_conv_ex_4.png "vcAmd\_conv\_ex\_4")  
範例 4  
  
## 請參閱  
 [類型和儲存區](../build/types-and-storage.md)