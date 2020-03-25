---
title: 嚴重錯誤 C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: c349c09b4931c0a303e7619b364ab237394bd4fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204447"
---
# <a name="fatal-error-c1055"></a>嚴重錯誤 C1055

編譯器限制：索引鍵不足

來源檔案包含太多符號。 編譯器已用完符號表的雜湊索引鍵。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 將來源檔案分割成較小的檔案。

1. 排除不必要的標頭檔案。

1. 重複使用暫時和全域變數，而不是建立新的變數。
