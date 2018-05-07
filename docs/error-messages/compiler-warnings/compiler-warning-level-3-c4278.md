---
title: 編譯器警告 （層級 3） C4278 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b556166f61c5d77ac34fb7243ac25d5baeaa2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4278"></a>編譯器警告 (層級 3) C4278
'identifier': 類型程式庫 'tlb' 中的識別項已經是巨集;使用 'rename' 限定詞  
  
 當使用[#import](../../preprocessor/hash-import-directive-cpp.md)，您要匯入的 typelib 中的識別項嘗試宣告識別項***識別碼***。 不過，這是已經是有效的符號。  
  
 使用`#import`**重新命名**屬性來指派別名給類型程式庫中的符號。