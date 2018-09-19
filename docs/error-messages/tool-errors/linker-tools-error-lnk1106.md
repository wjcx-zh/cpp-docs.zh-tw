---
title: 連結器工具錯誤 LNK1106 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 719ff1a87f3f1afc19cf38736c0059c46a8a9bdc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110870"
---
# <a name="linker-tools-error-lnk1106"></a>連結器工具錯誤 LNK1106

無效的檔案或磁碟已滿： nelze vyhledat 位置

此工具無法讀取或寫入`location`記憶體對應檔案中。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 磁碟已滿。

     釋出一些空間，並重新連結。

1. 嘗試透過網路連結。

     有些網路完全不支援連結器所使用的記憶體對應檔案。 請嘗試連結到本機磁碟上。

1. 在您的磁碟上不正確的區塊。

     雖然的作業系統和磁碟硬體應該已偵測到這類錯誤，您可能想要執行磁碟檢查程式。

1. 堆積空間不足。

     請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)如需詳細資訊。