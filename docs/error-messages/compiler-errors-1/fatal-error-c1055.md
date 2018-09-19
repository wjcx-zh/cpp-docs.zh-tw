---
title: 嚴重錯誤 C1055 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6960d8168bd818e4d1baa30e5e54940e6e4dc2e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115446"
---
# <a name="fatal-error-c1055"></a>嚴重錯誤 C1055

編譯器限制： 索引鍵不足

來源檔案包含太多符號。 編譯器已用完雜湊索引鍵的符號表。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 原始程式檔分成較小的檔案。

1. 消除不必要的標頭檔。

1. 重複使用而不是建立新的暫存和全域變數。