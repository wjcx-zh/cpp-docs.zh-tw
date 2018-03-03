---
title: "編譯器警告 （層級 3） C4278 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 249b13b70f3f10942852d7a9aa13dcf4f08e1f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4278"></a>編譯器警告 (層級 3) C4278
'identifier': 類型程式庫 'tlb' 中的識別項已經是巨集;使用 'rename' 限定詞  
  
 當使用[#import](../../preprocessor/hash-import-directive-cpp.md)，您要匯入的 typelib 中的識別項嘗試宣告識別項***識別碼***。 不過，這是已經是有效的符號。  
  
 使用`#import`**重新命名**屬性來指派別名給類型程式庫中的符號。