---
title: 編譯器警告 (層級 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627626"
---
# <a name="compiler-warning-level-3-c4278"></a>編譯器警告 (層級 3) C4278

> '*識別碼*': 類型程式庫中的識別項'*tlb*' 已經是巨集; 使用 'rename' 限定詞

使用時[#import](../../preprocessor/hash-import-directive-cpp.md)，您要匯入型別程式庫中的識別項嘗試宣告識別項*識別項*。 不過，這已經是有效的符號。

使用`#import`**重新命名**屬性，以將別名指派給類型程式庫中的符號。