---
title: 嚴重錯誤 C1126 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062471"
---
# <a name="fatal-error-c1126"></a>嚴重錯誤 C1126

'identifier': 自動配置超過大小

配置給本機變數的函式 （加上的編譯器，例如額外的 20 個位元組，可切換的函式所使用的空間數量有限） 的空間超過限制。

若要更正這個錯誤，請使用`malloc`或`new`配置大量的資料。