---
title: 配置零記憶體
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313489"
---
# <a name="allocating-zero-memory"></a>配置零記憶體

**ANSI 4.10.3**如果要求的大小`calloc`為`malloc`零， `realloc`則為、或函數的行為

`calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)
