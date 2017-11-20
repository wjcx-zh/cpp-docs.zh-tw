---
title: "位元欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebdfd892b164d10fbed46a481184c23113af4bc5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="bitfields"></a>位元欄位
結構的位元欄位限制為 64 位元，而且可以類型為帶正負號 int、 不帶正負號的 int、 int64、 或不帶正負號的 int64。 跨越類型界限的位元欄位會略過對齊的下一個類型的對齊方式的位元欄位的位元。 例如，整數的位元欄位不能跨越 32 位元界限。  
  
## <a name="see-also"></a>另請參閱  
 [類型和儲存區](../build/types-and-storage.md)