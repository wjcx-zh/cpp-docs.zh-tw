---
title: 嚴重錯誤 C1045 |Microsoft 文件
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
ms.openlocfilehash: 78ff500d050fbb646dd97fc898279712fb750d9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197607"
---
# <a name="fatal-error-c1045"></a>嚴重錯誤 C1045
編譯器限制 : 連結規格巢狀結構太深  
  
 巢狀的外部超過編譯器限制。 巢狀的外部可以加上外部連結類型，如 `extern` "C++"。 降低巢狀外部的數目以解決此錯誤。