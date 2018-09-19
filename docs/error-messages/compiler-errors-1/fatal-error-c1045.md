---
title: 嚴重錯誤 C1045 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1045
dev_langs:
- C++
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c18d6f9b502e818992097c3042689cf66457792
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024771"
---
# <a name="fatal-error-c1045"></a>嚴重錯誤 C1045

編譯器限制 : 連結規格巢狀結構太深

巢狀的外部超過編譯器限制。 巢狀的外部可以加上外部連結類型，如 `extern` "C++"。 降低巢狀外部的數目以解決此錯誤。