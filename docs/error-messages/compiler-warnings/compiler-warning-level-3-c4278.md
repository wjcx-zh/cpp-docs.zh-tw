---
title: 編譯器警告 （層級 3） C4278 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
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
ms.openlocfilehash: f63337de2e14b1cb0f9d854df962ab2aa9c8014e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205777"
---
# <a name="compiler-warning-level-3-c4278"></a>編譯器警告 (層級 3) C4278

> '*識別碼*': 類型程式庫中的識別項'*tlb*' 已經是巨集; 使用 'rename' 限定詞

使用時[#import](../../preprocessor/hash-import-directive-cpp.md)，您要匯入型別程式庫中的識別項嘗試宣告識別項*識別項*。 不過，這已經是有效的符號。

使用`#import`**重新命名**屬性，以將別名指派給類型程式庫中的符號。