---
title: 位元欄位 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85db49f138cc733326e47a3008e79bae5ab4b7cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="bitfields"></a>位元欄位
結構的位元欄位限制為 64 位元，而且可以類型為帶正負號 int、 不帶正負號的 int、 int64、 或不帶正負號的 int64。 跨越類型界限的位元欄位會略過對齊的下一個類型的對齊方式的位元欄位的位元。 例如，整數的位元欄位不能跨越 32 位元界限。  
  
## <a name="see-also"></a>另請參閱  
 [類型和儲存區](../build/types-and-storage.md)