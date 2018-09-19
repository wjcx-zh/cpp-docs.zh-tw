---
title: 配置零記憶體 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085052"
---
# <a name="allocating-zero-memory"></a>配置零記憶體

**ANSI 4.10.3** `calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為

`calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)