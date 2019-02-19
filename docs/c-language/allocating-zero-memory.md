---
title: 配置零記憶體
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147460"
---
# <a name="allocating-zero-memory"></a>配置零記憶體

**ANSI 4.10.3** `calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為

`calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。

## <a name="see-also"></a>另請參閱

[程式庫函式](../c-language/library-functions.md)
